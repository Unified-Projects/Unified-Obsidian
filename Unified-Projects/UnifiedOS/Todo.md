---

kanban-plugin: basic

---

## Todo

- [ ] Page trap
- [ ] Make sure that memory mapping is aware of the fact that we could run out of memory
- [ ] AHCI / SATA Driver
- [ ] APIC / SMP
- [ ] Multiprocessing
- [ ] Syscalls
- [ ] Bring non 32 bpi video drivers into support using a colour conversion and proper setting
- [ ] Make memory space allocations more faster by implementing a bitmap sort of operation when the memory space reaches the endpoint.
- [ ] Basic Device with all features needed for drivers and filesystem
- [ ] Unix-Like filesystem implementation


## In the works

- [ ] Memory Map Creation/Forking/Deletion
- [ ] Heap use heap memory space using virtual allocations!
- [ ] Setup Virtual Memory Allocations Using memory spaces


## Dunz

**Complete**
- [x] Setup UEFI Bootloader
- [x] Load Basic Video Output and Font File (GOP)
- [x] Basic Video Driver Implementation
- [x] Test screen print
- [x] Physical Allocator
- [x] Virtual Allocator
- [x] Mapper
- [x] Memory Manager
- [x] Heap Manager
- [x] Interrupts (Interrupt Descriptor Table)
- [x] Global Descriptor Table (GDT)!
- [x] PIT
- [x] Fixed Kernel Booting to configure stack
- [x] Setup Ctors
- [x] PCI reading


## Put aside

- [ ] All my //TODOs




%% kanban:settings
```
{"kanban-plugin":"basic"}
```
%%