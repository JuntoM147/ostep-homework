The OS is a program, and like any other program it has some key data structures that track various relevant pieces of information.

To track the state the of each process, for example, the OS likely will keep some kind of ***process list*** for all processes that are ready and some additional information to track which process is currently running. The OS must also track in some way, blocked processes. When a I/O event completes, the OS should make sure to wake the correct process and ready it to run again.

A example of what type of information a OS needs to track about each process in the `xv6` kernel. 

```c
// the registers xv6 will save and restore 
// to stop and subsequently restart a process 
struct context { 
	int eip;
	int esp;
	int ebx; 
	int ecx; 
	int edx; 
	int esi; 
	int edi; 
	int ebp; 
};

// the different states a process can be in 
enum proc_state { UNUSED, EMBRYO, SLEEPING, RUNNABLE, RUNNING, ZOMBIE }; 

// the information xv6 tracks about each process 
// including its register context and state 
struct proc { 
	char *mem;                     // Start of process memory 
	uint sz;                       // Size of process memory 
	char *kstack;                  // Bottom of kernel stack 
				                   // for this process 
	enum proc_state state;         // Process state 
	int pid;                       // Process ID 
	struct proc *parent;           // Parent process 
	void *chan;                    // If !zero, sleeping on chan 
	int killed;                    // If !zero, has been killed 
	struct file *ofile[NOFILE];    // Open files 
	struct inode *cwd;             // Current directory 
	struct context context;        // Switch here to run process 
	struct trapframe *tf;          // Trap frame for the 
						           // current interrupt 
};
```

See [[Process States]] for a explanation of the zombie state

Some people refer to the individual structure that stores information about a process as a ***Process Control Block*** (PCB), a fancy way of talking about a C structure that contains information about each process (also sometimes called a process descriptor).
