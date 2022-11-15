Idea links the the Excalidraw.

## Physical
To controll what physical pages are in use we use a bitmap. Which is pretty simple to implement.

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