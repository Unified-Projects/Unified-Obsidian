This is a site of how I separate the memory space into sections for my os to utilise.

## 0x0 - 0x80 0000 0000 (0MiB to end of PML4 Entry 0)
>This is kernel space. Yes, I should use higher kernels but I don't really understand the best way of doing it - so I won't for now. The 512MiB is most likely not going to be used, but it gives room for more features and built-in drivers. It is also the memory space of physical memory, yes this will mean that no process can be 32 bit. This address should also hold the IO space (framebuffer, acpi, etc)

## 0x80 0000 0000 - 0x100 0000 0000 (PML4 Entry 1)
>This is kernel allocation space, not specifically for processes (they have there own) this is so that the frigg allocator only allocates a virtual address to not interrupt physical.

## 0x100 0000 0000 - 0x180 0000 0000 (PML4 Entry 2)

## 0x180 0000 0000 - 0x200 0000 0000 (PML4 Entry 3)

## 0x200 0000 0000 - 0x280 0000 0000 (PML4 Entry 4)

# IF MEMORY ISSUES OCOUR IT IS MOST LIKELY THE PAGEMAP TRYING TO ACCESS MEMORY THAT IS NOT MAPPED!