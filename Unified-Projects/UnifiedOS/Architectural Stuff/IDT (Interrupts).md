Interrupts are kind of a tool for getting the CPU's attention. This can either be because of a serious fault in the system or because something like a timer needs to tick or a PS2 mouse wants attention.

There are two sections to interrupts, a manager and a handler.

## Manager
This is where we intitialse the interrupts with a default handler and tell the system to start accepting these interrupts.

## Handler
