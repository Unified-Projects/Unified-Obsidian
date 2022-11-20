These arn't so much as a architectual thing, however it does impact (at least from what i've seen) what works.

These are compiler provided funtions (crt0.o, crtn.o etc) and they need to be called to improve functionality. Hence using the linkerscript file we can locate where they are in memory and call them within the kernel function.