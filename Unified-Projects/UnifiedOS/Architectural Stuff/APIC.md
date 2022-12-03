## General
Using the ACPI tables (that we used in PCI detection) we can get a table for APIC, this holds mapping information and ids of all the cores present in our system. Some of these cores may be disabled by the system so we need to ensure that they are actually togglable.

## Local
Bases of booting up a core and sending interrupts between the cores (IPI).

## IO
Used for redirecting IRQ interrupts (Keep in mind we will need to disable PIC not only for this, but also that some systems no longer contain a PIC chip.).