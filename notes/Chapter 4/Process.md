The ***informal*** definition of a process is ***a running program***. 

It is the major OS abstraction of a running program.

The program itself is a lifeless thing, just bytes on a disk. It is the OS that takes these bytes and gets them running, transforming the program into something useful.

At any point in time, the process can be described by its [[Machine State]]

It is often the case that you want to run multiple processes at once. Doing so makes the system easy to use because you never have to be concerned with wether a CPU is available, you can just simply run programs. 


***"How do you then provide the illusion of many CPUs?"***

By running one process, stopping it then running another and so forth the OS can promote that multiple virtual CPUs exist when in fact there is only one (or a few) physical CPUs.

This basic technique is known as [[Time Sharing]]
