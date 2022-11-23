Interrupts are kind of a tool for getting the CPU's attention. This can either be because of a serious fault in the system or because something like a timer needs to tick or a PS2 mouse wants attention.

There are two sections to interrupts, a manager and a handler.

## Manager
This is where we initialise the interrupts with a default handler and tell the system to start accepting these interrupts.

The system requires a table of descriptors which look like this:
```CPP
struct gate_descriptor_t{
	uint16_t base_low;
	uint16_t sel;
	uint8_t ist;
	uint8_t flags;
	uint16_t base_med;
	uint32_t base_high;
	uint32_t null;
} __attribute__((packed)); // We use packed to tell the compiler not to move any of the definition arround (which would save memory but cause issues)
```

And we tell the system to size and position of the table with:
```CPP
struct idt_pointer_t
{
	uint16_t limit;
	uint64_t base;
} __attribute__((packed));
```

These will point to a assembly created code that configures register and stack variables before proceeding back to C++ for the handling of the interrupt.

## Handler
All this needs to be a basic function that takes two arguments, a data argument (For the interrupts that require one) and a register argument that holds the stack of the previous process pre interrupt.