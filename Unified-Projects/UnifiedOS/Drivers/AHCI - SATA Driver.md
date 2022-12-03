## Enumeration !
Using the provided PCI device information, which can be gathered from the locate device function using a class, subclass and progIF. This is our AHCI controller, each controller has up to 32 ports of devices like SATA, SATAPI, SEMB, PM. We only want the SATA for now. We can then create a port device from this.

## Read/Writing
The process of writing or reading the the disk is identical to each other, with the only exception of the command registers being for either read or write. You read and write to the disk in terms of block sizes. Using the diskDevice partition we change this to being varied by allowing offsets into the disk instead of lba (block numbers).

## Device Chain
Each port gets attached to the /dev/sdx devices. (Limiting to 26 SATA devices). Adding them to the filesystem.