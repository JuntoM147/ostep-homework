How are programs transformed to processes?

How does process creation actually work?

1) Load
	- The OS must load the code and any static data (e.g. initialised variables) into memory, into the address space of the process.
	- Programs initially reside on disk (or SSDs) in some kind of executable format. The process of loading a program requires the OS to read those bytes from disk and place them in memory somewhere.
	- Used to be done eagerly (load everything at once), but modern OSes perform this process lazily (as need basis).

2) Allocate stack memory
	- Programs use the stack for local variables, functions parameters, and return addresses. 
	- The OS allocates this memory and gives it to the process.
	- The OS will also likely initialize stack with arguments (fill in the parameters to `main()` with `argc` and `argv`) 

3) Allocate heap memory
	- The heap is used for explicitly requested dynamically-allocated data.
	- Programs request such space by calling `malloc()` and free it using `free()` 

4) I/O  
	- In `UNIX` systems each process has three open ***file descriptors*** for standard input, output and error. 
	- These descriptors let programs easily read input from the terminal and print output to the screen.
	