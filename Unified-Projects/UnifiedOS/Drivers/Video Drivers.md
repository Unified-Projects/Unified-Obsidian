The short Idea is that with this I can draw strings to the screen, draw a bitmap and a rectangle.

To start we define a basic structure to hold all the screens information. This allows it to be passed along without any options. This will be double buffered when the memory manager is setup to increase speed of updating the screen and to stop screen tearing.

```C++ TI="Simple Surface Struct"
//Basic Video Surface Structure to hold screen info

struct Surface
{  
	// Basic Image Properties
	uint32_t Width;
	uint32_t Height;
	uint8_t Depth;
	
	// For line skipping
	size_t LineSkip;
	
	// Total Allocation
	size_t BufferSize;
	
	// Location (Will be mapped later to IO part and double buffered)
	uint32_t* ScreenFront; // Actuall Screen address
	uint32_t* ScreenBack; // Data written to
	
	// Instead of shifting we clear screen
	bool QuickShift;
};
```

## Text
Drawing text to the screen isn't too hard. As with my UEFI bootloader I have implemented a PSF Font file loader using it's built in interpreter. This gives me access to the glyphed data for drawing to the screen.  If the text runs over the bottom of the screen or has a newline character that will do the same the screen shifts the buffer up to allow room for it.

## Shifting
This is where the framebuffer shifts up to allow room for new characters to be placed in without completely removing the old lines. The method used is to count the number of newlines needed, shift the screen, then print the rest. This is quite processing heavy and is known to slow boot times. 

>**This can be slow on larger screens, so instead I added quick shift (Which will auto enable on screens bigger than 720p!) to clear the screen whenever the bottom is reached! If desired, I may make it toggleable on larger screens.**

>**We need to be careful to cast the ScreenBack to an uint8_t* as when incrementing an uint32_t* by 1 we actually move the pointer 4 bytes (1 uint32_t word) forward which will cause issues.**

## Print Function
The print function uses, I think, the standard formatting args. This is done using the standard stdarg header file with the toolchain, saving a lot of confusion in coding it. And to get around the no memory management, I pre-defined buffers that it uses instead.

```C++ TI="Print example"
Video::Print("%x is %d in hex!", 123, 123);
// Expected output: "0x7b is 123 in hex!"
```

> **NOTE THAT THE SCREEN MAY BE MESSED UP WITH PRINT FUNCTION AND THE SYSTEM MAY FAULT. THIS IS CAUSED BY THE PRINT FUNCTION ACCESING THE SAME BUFFER AT THE SAME TIME! FIX MAY BE NEEDING TO ALLOCATE MEMORY FOR EACH RUN AND THEN FREE IT!

> Double buffering creates efficiency in reading from screen buffer