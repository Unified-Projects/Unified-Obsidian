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
- [ ] Character buffers
- [ ] Remove a device on deinitialization (Think of a USB device being detached but marked as present!)
- [ ] With resolving a node, make sure to add the directory nodes to the tree and increment their handles to 1. I will need to close after each usage tho!
- [ ] IPC - Messages
- [ ] IPC - Endpoints
- [ ] Signal handleing
- [ ] Look into rare and occational screen issue post/During PCI intitialisation!
- [ ] Memory Map Deletion
- [ ] Fix filesystem node closing
- [ ] Fix filesystem multiple sections  to path (Daemon)
- [ ] Ensure we unmap the initial PML4 (fre it)


## Syscalls

- [ ] SYS_STAT
- [ ] SYS_YEILD
- [ ] SYS_EXEC
- [ ] SYS_FSTAT
- [ ] SYS_CLOSE
- [ ] SYS_


## In the works

- [ ] Syscall list


## Dunz

**Complete**
- [x] Setup UEFI Bootloader
- [x] Process Allocator
- [x] ELF Reading
- [x] Normal Processes
- [x] Load Basic Video Output and Font File (GOP)
- [x] Basic Video Driver Implementation
- [x] AHCI / SATA Driver
- [x] Test screen print
- [x] Physical Allocator
- [x] Virtual Allocator
- [x] Screen Scrolling seems to cause occasional crashes (presumably writing outside of memory range)
- [x] Memory Map Creation/Forking
- [x] Mapper
- [x] Memory Manager
- [x] Unix-Like filesystem implementation
- [x] Heap Manager
- [x] Multiprocessing
- [x] Interrupts (Interrupt Descriptor Table)
- [x] APIC / SMP
- [x] Global Descriptor Table (GDT)!
- [x] Kernel Panic Screen
- [x] Setup Virtual Memory Allocations Using memory spaces
- [x] PIT
- [x] Basic Device with all features needed for drivers and filesystem
- [x] Higher Kernel
- [x] Fixed Kernel Booting to configure stack
- [x] Setup Ctors
- [x] PCI reading
- [x] Check if a pointer is within a page table
- [x] Heap use heap memory space using virtual allocations!
- [x] Find physical address from virtual
- [x] Setup serial output


## Syscalls Completed

**Complete**
- [x] SYS_DEBUG
- [x] SYS_READ
- [x] SYS_OPEN
- [x] SYS_WRITE
- [x] SYS_MMAP
- [x] SYS_GETTID
- [x] SYS_LSEEK
- [x] SYS_SETFSBASE


## Put aside

- [ ] All my //TODOs
- [ ] Virtual memory freeing




%% kanban:settings
```
{"kanban-plugin":"basic"}
```
%%