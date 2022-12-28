A higher kernel is when the actual kernel data and program stuff gets mapped to the memory address 0xFFFF 0000 0000 0000 so that the entire sub memory space is actually available for the processes to make use of.

In order to do this, there needs to be two stages to the kernel. One stage that sets up a basic page table and does the mapping of the higher kernel, and then a second stage that actually is the kernel and frees up the lower half of the kernel to be used as normal memory. However, the physical address of the higher kernel needs to be above 0x10000 as the 16-bit SMP Setup will make use of it.

```NASM
SECTION .data

align 0x1000

prekernel_pml4:

    dq V2P(prekernel_pml3) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

%rep ENTRIES_PER_PAGE_TABLE - 3

    dq 0

%endrep

    dq V2P(prekernel_pml3_virt) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

    dq V2P(prekernel_pml3_high) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

prekernel_pml3_virt:

    dq V2P(prekernel_pml2) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

%rep ENTRIES_PER_PAGE_TABLE - 1

    dq 0

%endrep

prekernel_pml3:

    dq V2P(prekernel_pml2) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

%rep ENTRIES_PER_PAGE_TABLE - 1

    dq 0

%endrep

prekernel_pml3_high:

%rep ENTRIES_PER_PAGE_TABLE - 2

    dq 0

%endrep

    dq V2P(prekernel_pml2) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

    dq 0

prekernel_pml2:

    dq V2P(prekernel_pml1) + (PAGE_PRESENT | PAGE_READ_WRITE | PAGE_GLOBAL)

%rep ENTRIES_PER_PAGE_TABLE - 1

    dq 0

%endrep

prekernel_pml1:

%rep ENTRIES_PER_PAGE_TABLE

    dq 0

%endrep
```
> This is all achieved by this initial PML4 that gets loaded as it first maps 2MiB of physical memory to both lower memory and higher memory for the kernel to load from.

It is then verry important to re-setup paging in the kernel with a new page table and then map all the physical memory and higher memory so that we can have a functional allocator.

This also requires modification to the kernel linkscript
```Linkerscript
KERNEL_PHYSICAL = 0x10000;
KERNEL_VIRTUAL = 0xFFFFFFFF80000000;
. = KERNEL_VIRTUAL + KERNEL_PHYSICAL;
```

We specify the kernel physical so that we know where the kernel is loaded at. This allows us to easily map the kernel physical using the first page table. And its 0x10000 so that we have space the SMP