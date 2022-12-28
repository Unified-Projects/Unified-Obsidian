Serial interface uses 6 ports. These range from port number 0x3F8-0x3FD.

There is a initial config stage:
```C++
Port1.Write(0x00); // Disable all interrupts
Port3.Write(0x80); // Enable DLAB (set baud rate divisor)
Port0.Write(0x03); // Set divisor to 3 (lo byte) 38400 baud
Port1.Write(0x00); //                  (hi byte)
Port3.Write(0x03); // 8 bits, no parity, one stop bit
Port2.Write(0xC7); // Enable FIFO, clear them, with 14-byte threshold
Port4.Write(0x0B); // IRQs enabled, RTS/DSR set
```

Then its just a matter of writing to the Serial on each log (Ensuring we disable interrupts for it.)