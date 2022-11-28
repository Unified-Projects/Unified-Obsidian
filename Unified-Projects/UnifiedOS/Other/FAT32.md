## Clusters
A file within a fat32 partition contains a reference to one Fat32 cluster. This entry in the FAT tables becomes a chain that will be followed to get each cluster that is needed for the file and what order they are to be in. These clusters point to a set of sectors (For example by default it's about 8 sectors per cluster) that come after all the reserved sectors.

## Files
File entries can be one of two types
#### Long File Name
```CPP
struct FAT_LFN_ENTRY
{
	uint8_t order;
	uint16_t characters0[5];
	uint8_t attributes;
	uint8_t type;
	uint8_t checksum;
	uint16_t characters1[6];
	uint16_t zero;
	uint16_t characters2[2];
} __attribute__((packed));
```
This will contain no information with regards to the file position, sizes or type. Rather this only contains some extra characters that the file may need.

### Normal
```CPP
struct FAT_FEntry
{
	uint8_t filename[8];
	uint8_t ext[3];
	uint8_t attributes;
	uint8_t reserved;
	uint8_t createTimeTenthsOfSecond;
	uint16_t creationTime;
	uint16_t creationDate;
	uint16_t accessedDate;
	uint16_t highClusterNum;
	uint16_t modificationTime;
	uint16_t modificationDate;
	uint16_t lowClusterNum;
	uint32_t fileSize;
} __attribute__((packed));
```
This is a 32 byte entry that describes file information and position within the partition. The partition uses this to read from the cluster entries and hold the inode value. I should setup a store for the FAT entry and index within parent node