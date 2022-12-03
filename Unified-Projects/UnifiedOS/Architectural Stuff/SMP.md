For each core we initiate we want to hold some of its public values to be modified.
```CPP
struct CPU_CORE{ // Definitions for SMP
	CPU_CORE* self = nullptr;
	
	uint64_t ID;
	
	UnifiedOS::ProcessManagement::Thread* ActiveThread;
	
	uint64_t scratch; // Used in syscalls
	TSS_Store CPU_TSS __attribute__((aligned(16)));
	
	uint64_t GDT;
	GDT_PTR GDTPtr;
	
	uint64_t IDT;
	IDT_PTR IDTPtr;
	
	List<UnifiedOS::ProcessManagement::Thread*>* Threads;
	UnifiedOS::ProcessManagement::Process* ActiveProcess;
	
	RegisterContext* ActiveRegisters;
	fx_state_t* ActiveFXState;
} __attribute__((packed));
```

This is just some basic information within the core that describes what it's running/doing.

## Booting a core
We rely on our APIC code for this, we use its Send_IPI function which sends a interrupt to a specified core or all cores. There is a initiate IPI and then a start IPI. Which we pass the 16-bit smp code entry for it to use.

## SMP Core
Now for the smp code we need to be able to start in 16-bit addressing. This is because all cpu's start in 16-bit. This requires extra waste code as a part of the kernel, ensuring that we don't overwrite some kernel code in the process of loading the smp.
```NASM
section .padder ; Required Padding to give room for the SMP trampoline space to go
align 64
resb 0xFFFF ; 64KiB and max 16-bit address
```
> .padder is defined in our linker script to be at the verry begging of the kernel.

The rest of the initiation is similar to how we initiated on our current kernel. (Load GDT, Load page map, load IDT). Then proceed to halt until we setup processes.