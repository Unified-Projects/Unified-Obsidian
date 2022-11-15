The short Idea is that with this I can draw strings to the screen, draw a bitmap and a rectangle.

To start we define a basic structure to hold all the screens information. This allows it to be passed along without any options. This will be double buffered when the memory manager is setup to increase speed of updating the screen and to stop screen tearing.

```C++ TI="Simple Surface Struct"
struct Surface
{  
	// Basic Image Properties
	uint32_t Width;
	uint32_t Height;
	uint32_t Depth;
	
	// For line skipping
	uint32_t PixelsPerScanLine;
	
	// Location (Will be mapped later to IO part and double buffered)
	uint32_t* ScreenFront;
};
```

## Text
Drawing text to the screen isnt too hard. As with my UEFI bootloader I have implemented a PSF Font file loader using its built in interpreter. This gives me access to the glyphed data for drawing to the screen. 

### For now screen shifiting is not implemented so the screen will clear.

## Shifting
This is where the framebuffer shifts up to allow room for new characters to be placed in without completely removing the old lines. The method used is to count the number of newlines needed, shift the screen, then print the rest.

## Print Function
Print function can only be implemented after memory management due to conversions to strings.