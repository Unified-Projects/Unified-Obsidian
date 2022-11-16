Idea links the the Excalidraw.

## Physical
To controll what physical pages are in use we use a bitmap. Which is pretty simple to implement. I just need to make sure that all IO is reserved and kernel space as this can cause issues is we allocate it to another process to overwrite.

## Virtual
For mapping virtual memory, pages are used. These consist of tables that for each table there are 512 more tables before eventually reaching the actual page entry which can then have the physical address entered and a couple flags.

This is a PageMap that will define all those tables for me and help me look for the entry.
```C++ TI="Page map struct"
struct PageMap {
	// Each layer (Using a builtin function these values can be filled with selected data)
	pml4_entry_t* pml4;
	pdpt_entry_t* pdpt;
	pd_entry_t* pageDirs; // ** because its a [] of uint64_t*
	page_t* page;
	
	// Physical Memory Posititons
	uint64_t* pageDirsPhys;
	uint64_t pdptPhys;
	uint64_t pml4Phys;
	
	page_t*** pageTables;
	
	// Load values to the layers (Returns -1 on not valid)
	int LocatePage(virtual_t Address);
} __attribute__((packed));
```

## Mapping

## Page trap
This is where we fault to whenever we receive a page fault. Here we check if we are a process or kernel. If we are kernel we panic the whole system. Otherwise we move to **reallocation** or if the memory was never a part of the process, page fault the process.

**reallocation** - Allocate the physicall part of the allocated virtual memory (We didn't first because we want to save memory)