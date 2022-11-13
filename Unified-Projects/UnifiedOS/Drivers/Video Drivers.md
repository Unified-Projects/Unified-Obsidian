The short Idea is that with this I can draw strings to the screen, draw a bitmap and a rectangle.

To start we define a basic structure to hold all the screens information. This allows it to be passed along without any options.

```C++ TI="Simple Surface Struct"
struct Surface
{  
	// Basic Image Properties
	uint32_t Width;
	uint32_t Height;
	uint32_t Depth;
	
	// For line skipping
	uint32_t PixelsPerScanLine;
	
	// Location (Eventually This will get mapped out of this location)
	uint32_t* Screen;
};
```

## Text
Drawing text to the screen isnt too hard. As with my UEFI bootloader I have implemented a PSF Font file loader using its built in interpreter. This gives me access to the glyphed data for drawing to the screen.