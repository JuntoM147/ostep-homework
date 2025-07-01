The OS takes physical resources (CPU, memory, disk) and ***virtualises*** them. It handles tough issues related to ***concurrency***. And it stores files ***persistently*** making them safe over the long term. 

### 1) Virtualisation

When the OS takes a ***physical resource*** (processor, memory, disk etc) and transforms it into a more general, powerful, and easy-to-use ***virtual*** form of itself. 

***What is the point of virtualisation?*** 
It makes the system easier to use. 

***What is the crux of the problem?***
"How does the OS virtualize resources?" 

"What mechanisms and policies are implemented by the OS to attain virtualisation?"

"How does the OS do so efficiently?"

"What hardware support is needed?"

#### Forms of Virtualisation

##### Virtualising the CPU
Turning a single or small number of CPUs into a seemingly infinite number of CPUs and thus allowing many programs to seemingly run at once is called ***virtualising the CPU***. 

##### Virtualising Physical Memory
Physical memory is just a array of bytes. To read memory a address is required to access the data stored there, and to write (or update) memory you must also specify the data written to the given address.

Each process has access to its own private virtual address space (or address space) which to OS somehow maps onto the physical memory of the machine. As far as the process is concerned it has physical memory all to itself, when in reality physical memory is a shared resource managed by the operating system.

### 2) Concurrency

The OS is often juggling many things at once, first running one process than another etc. Concurrency then is a conceptual term that refer to a host of problems that arise and must be addressed when working on many things at once.

##### The Crux of the Problem

When there are many concurrently executing threads within the same memory space, how can we build a correctly working program?

What primitives are needed from the OS?

What mechanisms should be provided by the hardware? How can we use them to solve the problems of concurrency?


### 3) Persistence

In system memory, data can be easily lost. Devices such as DRAM store values in a volatile manner (when power goes away or system crashes data is lost). Thus we need hardware and software to be able to store data ***persistently***.

The hardware comes in the form of some kind or I/O device. A hard drive and solid state drives are a common repository for long lived information.

Unlike the abstractions provided by the OS for the CPU and memory, the OS does not create a private virtualised disk to each application. Actually, it is often assumed that users will want to share information that is in files.

##### The Crux of the Problem

What techniques are needed to manage data persistently in a correct manner?

What mechanisms and policies are required to do so correctly?

What mechanisms and policies are required to do so with high performance? 

How is reliability achieved, in the face of failures in hardware and software?


In order to allow the user to tell the OS what to do and make use of its features, the OS provides some interfaces (APIs) that you can call. A typical OS provides a few hundred ***system calls*** that are available to applications. 

Because the OS provides these calls to run programs, access memory, and devices, and other related actions, we say that the OS provides ***standard library*** to applications. 

Each of the CPU, memory, and disk is a resource of the system. It is the OS' role to manage those ***resources***, doing so efficiently or fairly (or with other goals). Thus the OS is sometimes known as ***resource manager***. 






