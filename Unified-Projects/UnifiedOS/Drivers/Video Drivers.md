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
};
```

## Text
Drawing text to the screen isn't too hard. As with my UEFI bootloader I have implemented a PSF Font file loader using it's built in interpreter. This gives me access to the glyphed data for drawing to the screen.  If the text runs over the bottom of the screen or has a newline character that will do the same the screen shifts the buffer up to allow room for it.

## Shifting
This is where the framebuffer shifts up to allow room for new characters to be placed in without completely removing the old lines. The method used is to count the number of newlines needed, shift the screen, then print the rest.

## Print Function
Print function can only be implemented after memory management due to conversions to strings.