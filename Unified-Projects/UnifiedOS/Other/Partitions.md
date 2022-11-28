## GPT

The OS only supports GPT formatted disks (GPT is a partitioning scheme that uses GUIDs and a fixed table of partitions to initialise the disks compared to MBR). This is the header contained within the disk's second sector (The first is still considered the MBR sector).
```CPP
struct GPTHeader{
	uint64_t signature;
	uint32_t revision;
	uint32_t size;
	uint32_t crc32;
	uint32_t reserved;
	uint64_t currentLBA;
	uint64_t backupLBA;
	uint64_t firstLBA;
	uint64_t lastLBA;
	uint8_t diskGUID[16];
	uint64_t partitionTableLBA;
	uint32_t partNum;
	uint32_t partEntrySize;
	uint32_t partEntriesCRC;
} __attribute__((packed)) ;
```

Then the sectors after contain this information (4 of these per sector, so about 32 sectors in total, making 128 partition entries possible)
```CPP
struct GPTParition{
	uint8_t typeGUID[16];
	uint8_t partitionGUID[16];
	uint64_t startLBA;
	uint64_t endLBA;
	uint64_t flags;
	uint8_t name[72];
} __attribute__((packed));
```

> **We really have to use packed here as we rely on the bit formatting of the architecture. This is little endian and it defines the order of which bytes will be read from the disk. The packed feature allows a direct conversion from the raw data to the structured data with all values being populated correct.**

When we mount the device to the filesystem as a volume, we detect is format and setup a volume corresponding to this (FAT32, Ext2, etc).