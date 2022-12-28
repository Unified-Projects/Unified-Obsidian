To boot into my OS, I chose to skip doing the setting long mode and use a tool called GNU-EFI which is helps you code your own EFI-tool or bootloader. This allows me to get all the information needed for my OS (i.e the Graphics Output Protocol or the RSDP tables or Memory map) and pass them into my kernel using C.

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

# Kernel Entry
We enter the kernel in assembly to setup some cpu flags and stack pointers that we can't really acomplish with c++.

We first initialise the PML4 for higher half kernel inits.
``` NASM
    ;# Prepare an identity mapped Page Map Level One (PML1)

    mov rax, V2P(prekernel_pml1)

%assign i 0

%rep ENTRIES_PER_PAGE_TABLE

    mov QWORD [rax], (i << 12) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

    add rax, 8

%assign i i+1

%endrep

  

    ;# Load prekernel Page Map Level Four (PML4).

    mov rax, V2P(prekernel_pml4)

    mov cr3, rax
```

We setup cpu flags and meory setup. We will use SSE4 functions se we set that flag aswel
> **Note: This means that for cpu's not supporting SSE4 extentions / x86_64-V2 they are not supported in the OS**
```NASM
mov rax, cr0
and ax, 0xFFFB      ; Clear coprocessor emulation
or ax, 0x2          ; Set coprocessor monitoring
mov cr0, rax

;Enable SSE
mov rax, cr4
or ax, 3 << 9       ; Set flags for SSE
mov cr4, rax

mov rcx, 0x277 ; PAT Model Specific Register
rdmsr
mov rbx, 0xFFFFFFFFFFFFFF
and rax, rbx
mov rbx, 0x100000000000000
or rax, rbx  ; Set PA7 to Write-combining (0x1, WC)
wrmsr
```

We need to copy the memory map and boot info into the stack for actual access in the kernel (As we only map 2MiB of physical memory and the bootloader tends to stick stuff at the end of memory)
```NASM
;# Copy boot info structure.
mov rcx, 64
mov rsi, rdi
mov rdi, V2P(boot_info)
cld
rep movsb

;# Copy EFI Memory Map to prekernel stack, update pointer in boot info.
;# Map size in 8 bytes is at boot_info + 24
mov rcx, QWORD [V2P(boot_info) + 24] ; RCX = total map size in bytes
sub rsp, rcx
mov rsi, QWORD [V2P(boot_info) + 16]
mov rdx, rsp
mov rdi, rsp
cld
rep movsb
mov rax, 0xffffffff80000000
add rdx, rax
mov QWORD [V2P(boot_info) + 16], rdx
```