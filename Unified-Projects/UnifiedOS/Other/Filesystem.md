## Devices
Devices will both have a device mount point within /dev/, but they will also have a option mountpoint within the filesystem structure (/mnt/, /media/, etc).

This extra mountpoint is defined by:
```CPP
struct Mountpoint
{
	Devices::Device* dev;
	Node* fsnode;
	Volume* volume;
	const char* mountpoint;
};
```
Which will get used by the resolver to ensure we use the correct device. These cannot be mounted within another device (with the exception of the root block device).

A device entry in the /dev/ looks something like this:
```CPP
struct Device_Identifier{
	Devices::Device* dev;
	Node* fsnode;
	const char* DevBlockName;
};
```

## Root Block Devices
I plan on creation of a disk for the UUIIDs to be read and put into a text file that is placed in the efi partition, then on boot this gets read and told to the kernel using the boot info, this can then be checked against the partition info of a disk to know if its the correct disk to be mounted at the location etc.

## Nodes
A node contains viable information for the volumes to be able to identify its location and read/write the data to the disk.
```CPP
lock_t blockedLock = 0;

uint32_t flags = 0;       // Flags
uint32_t pmask = 0;       // Permission mask
uid_t uid = 0;            // User id
ino_t inode = 0;          // Inode number
size_t size = 0;          // Node size
int nlink = 0;            // Amount of references/hard links
unsigned handleCount = 0; // Amount of file handles that point to this node
uint64_t volumeID;

int error = 0;

Node* parent; // Previous Node
```

The lock is important as with the system we can allocate a file to multiple processes however we want to lock access to read/write at the same time as this would cause disk issues.

## Directory Entries
>**Not Currently Implemented**

## Resolving
We first want to check that we don't already have the path open, if so we can just passthrough the node. If not then we want to see if the directory is held within an embedded mounted disk and then hold the mountpoint to be used when searching within the partition. Now we can split the string into sections and then find a node for each subfolder required before finding a final node of the file in question. We then add the folder back to the list of opened items for any other processes to be able to use.