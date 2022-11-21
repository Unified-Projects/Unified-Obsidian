## The main requirements are these headers

```CPP
struct PCIDeviceHeader{
	uint16_t VendorID;
	uint16_t DeviceID;
	uint16_t Command;
	uint16_t Status;
	uint8_t RevisionID;
	uint8_t ProgIF;
	uint8_t SubClass;
	uint8_t Class;
	uint8_t CacheLineSize;
	uint8_t LatencyTumer;
	uint8_t HeaderType;
	uint8_t BIST;
}__attribute__((packed));
```

```CPP
struct PCIHeader0
	PCIDeviceHeader Header;
	uint32_t BAR0;
	uint32_t BAR1;
	uint32_t BAR2;
	uint32_t BAR3;
	uint32_t BAR4;
	uint32_t BAR5;
	uint32_t CardbusCISPtr;
	uint16_t SubsystemVendorID;
	uint16_t SubsystemID;
	uint32_t ExpansionROMBaseAddr;
	uint8_t CapabilitiesPtr;
	uint8_t Rsv0;
	uint16_t Rsv1;
	uint32_t Rsv2;
	uint8_t InterruptLine;
	uint8_t InterruptPin;
	uint8_t MinGrant;
	uint8_t MaxLatency;
}__attribute__((packed));
```

The **PCIDeviceHeader** is just a simpler structure that embeds into **PCIHeader0** and is only really used when setting up the device / searching for its presence in the drivers. These then provided the basic information needed to use these drivers and interact with the hardware.

The next stages are to enumerate the devices. These can be found using 3 different stages. The first stage is buses and there are 32 of these for each entry in the MCFG table. Then each bus has32 devices, and they have 8 functions and these are the devices used in the drivers.