---

kanban-plugin: basic

---

## Todo

- [ ] Global Descriptor Table (GDT)!
- [ ] Page trap
- [ ] Make Virtual Memory Page finder more optimised (By using Page*** and then accessing with [PDPT][{PD}][PT][Entry]])
- [ ] Make sure that memory mapping is aware of the fact that we could run out of memory
- [ ] Memory Map Creation/Forking/Deletion


## In the works

- [ ] Map page table to virtual memory (To <br> prevent issues I can see that I will need to deal with soon!)
- [ ] Memory Manager
- [ ] Heap Manager
- [ ] Interrupts (Interrupt Descriptor Table)


## Dunz

**Complete**
- [x] Setup UEFI Bootloader
- [x] Load Basic Video Output and Font File (GOP)
- [x] Basic Video Driver Implementation
- [x] Test screen print
- [x] Physical Allocator
- [x] Virtual Allocator
- [x] Mapper


## Put aside





%% kanban:settings
```
{"kanban-plugin":"basic"}
```
%%