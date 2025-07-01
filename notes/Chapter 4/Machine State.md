At any given time, what parts of the machine are important to the execution of this program?

1) Memory.
	- Instructions lie in memory. The data that the running program reads and writes sits in memory as well. 
	- The memory can address (the ***address space***) is part of the process.
2) Registers
	- Many instructions explicitly read or update registers
	- Including special registers like ***program counter*** (PC or instruction pointer), ***stack pointer*** and associated ***frame pointer***.
3) I/O information
	- Programs often access persistent storage devices too. 
	- Might include a list of the files the process currently has open.
	