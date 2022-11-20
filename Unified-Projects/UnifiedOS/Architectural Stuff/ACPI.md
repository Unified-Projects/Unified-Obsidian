This comes form the RSDP(2) tables that are built into the motherbaord. This defines where the operating system can find information like the PCI tables or the types of battery, power commands.

To check if a table is present in the RSDP(2) we compare header signatures.
```CPP
struct SDTHeader{
	unsigned char Signature[4];
	uint32_t Length;
	uint8_t Revision;
	uint8_t Checksum;
	uint8_t OEMId[6];
	uint8_t OEMTableId[8];
	uint32_t OEMRevision;
	uint32_t CreatorId;
	uint32_t CreatorRevision;
} __attribute__((packed));
```