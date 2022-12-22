## Processes
A process just contains information for filesystem (working directory and any open handles), a page map (For memory allocations) **TODO: Turn this into a allocator specific for processes and a page trap**. The environment variables and arguments and the threads behind the process.
```CPP
uint64_t NextThread;
List<Thread*>* threads;
Thread* MainThread;

List<Process*>* Children;
Process* Parent;

const char* Name;
const char* WorkingDirectory;
Vector<const char*>* Args;
Vector<const char*>* Env;

uint64_t NextHandle;
Vector<Filesystem::Handle*>* ProcessHandles;

SYS_Condition status;

uint64_t ID;
uint64_t ActiveTicks;

// TODO TURN INTO A ALLOCATOR
Paging::Virtual::PageMap* PMap;
```

## Threads
This holds information that is used with loading the process (The basic registers, fxstate, stack)

```CPP
RegisterContext Registers;
fx_state_t* FXState;
uint64_t fsBase = 0;

Process* Parent;

Thread* Next;
Thread* Prev;

int TIMESLICE = 0;

uint64_t ID;

SYS_Condition status;

uint64_t kernelStackBase;
uint64_t kernelStack;
```

## Scheduler
This manages all the processes and threads that run on each cpu core. We call the scheduler either through the use of interrupts (For other cores) or (on the main core) we use the PIT device to tell the scheduler to tick (Which will send the interrupts to the other cores). Here we move current process to stack (Unless its the idle process) and then proceed to get a new process and load it, or move onto the next thread on the process.

>Note: The scheduler uses one main stack (Instead of one per core) this means I don't need to create a load balancer but means we cannot schedule two cores simultaneously and so eventually the cores go out of sync by offsets of like 1 tick. This may come to bite me later.

The scheduler is also responsible for removing dying threads and processes.