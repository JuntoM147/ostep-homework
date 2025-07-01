A idea of what must be included in any interface of an operating system.

These APIs in some form are available on any modern OS:

1) Create
	- An OS must include some method to create a new process.
	- When you type a command into the shell, or double click on a application icon, the OS is invoked to create a new process to run the program you have indicated. 

2) Destroy
	- As there is an interface for process creation, systems also provide an interface to destroy processes forcefully. 
	- Many process will run and exit themselves, but when they don't the user may wish to kill them. And thus an interface to halt a runaway process is quite useful.

3) Wait
	- Sometimes it is useful to wait for a process to stop running.

4) Miscellaneous control
	- Other than killing or waiting for a process, there are sometimes other controls that are possible.
	- Most OSes provide some kind of method to suspend a process (stop it from running for a while) and then resume it (continue running).

5) Status
	- There are usually interfaces to get some status information about a process.
	- How long has it run for, what state is it in.