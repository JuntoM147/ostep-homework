#### Key Takeaway

Efficient process scheduling improves CPU and I/O utilization.  

> **Run I/O-bound tasks early** to overlap their I/O wait time with CPU work from other processes.  

This minimizes idle time and increases overall system efficiency.

### Questions

1) Run `process-run.py` with the following flags: `-l 5:100,5:100`. What should the CPU utilisation be (e.g., the percent of time the CPU is in use?) Why do you know this? Use the `-c` and `-p` flags to see if you were right.

![[Pasted image 20250701173713.png]]

![[Pasted image 20250701173820.png]]


2)  Now run with these flags: `./process-run.py -l 4:100,1:0` . These flags specify one process with 4 instructions (all to use the CPU), and one that simply issues an I/O and waits for it to be done. How long does it take to complete both processes? Use `-c` and `-p` to find out if you were right.

![[Pasted image 20250701174510.png]]


3) Switch the order of the processes: -l 1:0,4:100. What happens now? Does switching the order matter? Why? (As always, use -c and -p to see if you were right)

![[Pasted image 20250701174610.png]]


4) We’ll now explore some of the other flags. One important flag is -S, which determines how the system reacts when a process is- sues an I/O. With the flag set to SWITCH ON END, the system will NOT switch to another process while one is doing I/O, in- stead waiting until the process is completely finished. What happens when you run the following two processes (`-l 1:0,4:100 -c -S SWITCH ON END`), one doing I/O and the other doing CPU work?

![[Pasted image 20250701175351.png]]


5) Now, run the same processes, but with the switching behavior set to switch to another process whenever one is WAITING for I/O (`-l 1:0,4:100 -c -S SWITCH_ON_IO`). What happens now?Use `-c` and `-p` to confirm that you are right. 

![[Pasted image 20250701175324.png]]



6) One other important behavior is what to do when an I/O completes. With `-I IO RUN LATER` , when an I/O completes, the process that issued it is not necessarily run right away; rather, whatever was running at the time keeps running. What happens when you run this combination of processes? (`./process-run.py -l 3:0,5:100,5:100,5:100 -S SWITCH ON IO -c -p -I IO RUN LATER`) Are system resources being effectively utilized?

![[Pasted image 20250701175637.png]]


7) Now run the same processes, but with `-I IO RUN IMMEDIATE` set, which immediately runs the process that issued the I/O. How does this behavior differ? Why might running a process that just completed an I/O again be a good idea?

![[Pasted image 20250701175733.png]]


8) Now run with some randomly generated processes using flags `-s 1 -l 3:50,3:50` or `-s 2 -l 3:50,3:50` or `-s 3 -l 3:50, 3:50`. See if you can predict how the trace will turn out. What happens when you use the flag `-I IO RUN IMMEDIATE` versus that flag `-I IO RUN LATER`? What happens when you use the flag `-S SWITCH ON IO` versus `-S SWITCH ON END`?

#### `-s 1 -l 3:50,3:50`

![[Pasted image 20250701180146.png]]

##### `-s 2 -l 3:50,3:50`

![[Pasted image 20250701180219.png]]

![[Pasted image 20250701181108.png]]

##### `-s 3 -l 3:50,3:50`

![[Pasted image 20250701180329.png]]

![[Pasted image 20250701181401.png]]

