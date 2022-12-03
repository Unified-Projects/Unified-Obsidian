---

kanban-plugin: basic

---

## Todo

- [ ] Page trap
- [ ] Make sure that memory mapping is aware of the fact that we could run out of memory
- [ ] Bring non 32 bpi video drivers into support using a colour conversion and proper setting
- [ ] Make memory space allocations more faster by implementing a bitmap sort of operation when the memory space reaches the endpoint.
- [ ] Double Buffer Screen To improve performance and reduce screen tearing!
- [ ] Document things like Vector, List, TTraits, Assert So I Have notes!
- [ ] Screen Scrolling seems to cause occasional crashes (presumably writing outside of memory range)
- [ ] Character buffers
- [ ] Remove a device on deinitialization (Think of a USB device being detached but marked as present!)
- [ ] With resolving a node, make sure to add the directory nodes to the tree and increment their handles to 1. I will need to close after each usage tho!
- [ ] Memory Map Creation/Forking/Deletion
- [ ] Syscall list
- [ ] IPC - Messages
- [ ] IPC - Endpoints
- [ ] Signal handleing
- [ ] Look into rare and occational screen issue post/During PCI intitialisation!


## Syscalls

- [ ] SYS_READ
- [ ] SYS_OPEN
- [ ] SYS_WRITE
- [ ] SYS_STAT
- [ ] SYS_YEILD
- [ ] SYS_EXEC
- [ ] SYS_DEBUG
- [ ] SYS_CLOSE
- [ ] SYS_FSTAT
- [ ] SYS_MMAP


## In the works



## Dunz

**Complete**
- [x] Setup UEFI Bootloader
- [x] Load Basic Video Output and Font File (GOP)
- [x] Basic Video Driver Implementation
- [x] AHCI / SATA Driver
- [x] Test screen print
- [x] Physical Allocator
- [x] Virtual Allocator
- [x] Mapper
- [x] Memory Manager
- [x] Unix-Like filesystem implementation
- [x] Heap Manager
- [x] Multiprocessing
- [x] Interrupts (Interrupt Descriptor Table)
- [x] APIC / SMP
- [x] Global Descriptor Table (GDT)!
- [x] Setup Virtual Memory Allocations Using memory spaces
- [x] PIT
- [x] Basic Device with all features needed for drivers and filesystem
- [x] Fixed Kernel Booting to configure stack
- [x] Setup Ctors
- [x] PCI reading
- [x] Check if a pointer is within a page table
- [x] Heap use heap memory space using virtual allocations!
- [x] Find physical address from virtual


## Put aside

- [ ] All my //TODOs
- [ ] Virtual memory freeing




%% kanban:settings
```
{"kanban-plugin":"basic"}
```
%%