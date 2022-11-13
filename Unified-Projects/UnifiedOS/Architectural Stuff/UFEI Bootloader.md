To boot into my os, I chose to skip doing the setting long mode and use a tool called GNU-EFI which is where you can code your own efi-tool or bootloader. This allows me to get all the information needed for my os (i.e the Graphics Output Protocol or the RSDP tables or Memory map) and pass them into my kernel using C.

## Basic Kernel Loading
```C TI="Get File"
//Load Kernel
EFI_FILE* Kernel = LoadFile(NULL, L"kernel.elf", image_handle, systab);
if(Kernel == NULL){
	Print(L"Could Not Load Kernel\n\r");
}
else{
	Print(L"Kernel Loaded Successfully\n\r");
}
```

```C TI="Read it to a elf object to be entered"
Elf64_Ehdr header;{
	UINTN FileInfoSize;
	EFI_FILE_INFO* FileInfo;
	Kernel->GetInfo(Kernel, &gEfiFileInfoGuid, &FileInfoSize, NULL);
	systab->BootServices->AllocatePool(EfiLoaderData, FileInfoSize, (void**)&FileInfo);
	Kernel->GetInfo(Kernel, &gEfiFileInfoGuid, &FileInfoSize, (void**)&FileInfo);
	UINTN size = sizeof(header);
	Kernel->Read(Kernel, &size, &header);
}

if(
	memcmp(&header.e_ident[EI_MAG0], ELFMAG, SELFMAG) != 0 ||
	header.e_ident[EI_CLASS] != ELFCLASS64 ||
	header.e_ident[EI_DATA] != ELFDATA2LSB ||
	header.e_type != ET_EXEC ||
	header.e_machine != EM_X86_64 ||
	header.e_version != EV_CURRENT
){
	Print(L"Bad Kernel Format\n\r");
}
else{
	Print(L"Kernel Header Successfully Varified\n\r");
}

Elf64_Phdr* phdrs;{
	Kernel->SetPosition(Kernel, header.e_phoff);
	UINTN size = header.e_phnum * header.e_phentsize;
	systab->BootServices->AllocatePool(EfiLoaderData, size, (void**)&phdrs);
	Kernel->Read(Kernel, &size, phdrs);
}

for(
	Elf64_Phdr* phdr = phdrs;
	(char*) phdr < (char*)phdrs + header.e_phnum * header.e_phentsize;
	phdr = (Elf64_Phdr*)((char*)phdr+ header.e_phentsize)
){
	switch (phdr->p_type){
	case PT_LOAD:{
		int pages = (phdr->p_memsz + 0x1000 -1) / 0x1000;
		Elf64_Addr segment = phdr->p_paddr;
		systab->BootServices->AllocatePages(AllocateAddress, EfiLoaderData, pages, &segment);

		Kernel->SetPosition(Kernel, phdr->p_offset);
		UINTN size = phdr->p_filesz;
		Kernel->Read(Kernel, &size, (void*)segment);
		break;
	}
	}
}

// And just enter it with a table of information created beforeyhand
void (*KernelStart)(BootInfo*) = ((__attribute__((sysv_abi)) void (*)(BootInfo*) ) header.e_entry);
```

## Other Example
```C TI="GOP Gathering"
//Will Get the framebuffer info
Framebuffer* InitiliseGop(){
	//GOP
	EFI_GUID gopGuid = EFI_GRAPHICS_OUTPUT_PROTOCOL_GUID;
	EFI_GRAPHICS_OUTPUT_PROTOCOL* gop;
	EFI_STATUS status;

	//Locate GOP
	status = uefi_call_wrapper(BS->LocateProtocol, 3, &gopGuid, NULL, (void**)&gop);
	if(EFI_ERROR(status)){
		Print(L"Unable to locate GOP\n\r");
		return NULL;
	}
	else{
		Print(L"GOP located\n\r");
	}

	//Read FB info
	framebuffer.BaseAddress = (void*)gop->Mode->FrameBufferBase;
	framebuffer.BufferSize = gop->Mode->FrameBufferSize;
	framebuffer.Width = gop->Mode->Info->HorizontalResolution;
	framebuffer.Height = gop->Mode->Info->VerticalResolution;
	framebuffer.PixelsPerScanLine = gop->Mode->Info->PixelsPerScanLine;

	//Retrun framebuffer
	return &framebuffer;
}
```
