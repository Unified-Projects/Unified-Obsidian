This is a small chip on every system that runs at a fixed frequency of 1193182Hz. This also then sends interrupts (0x20) to the kernel telling it that it has ticked.

> Since 1193182Hz is a lot of interrupts, we set a divsor on the chip telling it to only send a interrupt at a frequency we can choose

This is used to create sleep functions and controll the scheduling of processes.