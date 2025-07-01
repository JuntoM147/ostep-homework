The key difference between a system call and a procedure (function) call is that a system call transfers control into the OS while simultaneously raising the hardware privilege level. 

User applications run in user mode which means the hardware restricts what applications can do.
In user mode:
- Can't typically initiate an I/O request to the disk

When a system call is initiated (using a special hardware instruction called a ***trap***) the hardware transfers control to a pre specified ***trap handler*** and simultaneously raises the privilege level to ***kernel*** mode.

In kernel mode the OS has full access to the hardware of the system and can do things like:
- Initiate I/O request
- Make more memory available to a program

When the OS is done servicing the request it passes control back to the user via a special ***return-from-trap*** instruction, which reverts to user mode while simultaneously passing control back to where the application left off. 