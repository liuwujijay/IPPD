# Terms Summaries & Questions



##### User time (%U) 
The amount of CPU time used only by this process, spent in the user-mode code (not inside the kernel). 

##### System time (%S)
The amount of CPU time that used by this processs, spent within the kernel. This does not include library code (the library code indirectly calls system calls).
See reference 2 for user vs kernel modes.

##### Percent of CPU (%P)
This is the percentage of CPU that was given to the process, and it is calculated by %P = (%U+%S)/%E. Using multiple cores can cause %CPU > 100%. 
(Maximum = n\_cores * 100%)

##### Elapsed (wall-clock) time (%E)
The time it took from the start to finish of the call.
Thus, the elapsed time can include time which was spent on other processes by the CPU, as well as time when the process was blocked (for IO, etc.)

##### Average shared text size
The amount of the ‘text’ section of the program memory space, where the program code is stored (the actual program).

##### Average unshared data size
The ‘data’ section of the program stores global variables.

##### Average stack size
The size of the program ‘stack’ section stores local variables and the function stack frames, etc. 

##### Average total size
Total size is given by the sum of data, stack, and text sizes.

##### Maximum resident set size / Average resident set size
Resident set size is the amount of memory that belongs to a process and is currently present in the real RAM (not swapped).

##### Major / Minor page faults
A page fault is an interrupt that is caused when the program tries to access a memory page that is within the virtual memory space, but is not actually loaded into the main memory.
Major PF: processs attempts to access a page that is maped in the virtual memory space but is not available in physical memory, and there needs to be a space in physical memory to store it.
Minor PF: 

##### Voluntary / Involuntary context switches
Context switch is the action of storing/restoring the state of a program to that execution can be continued later. When a process is switched out, another process in the ready queue can take over the cpu resources.

##### Swaps
Inactive pages in memory are moved to the swap space when the RAM becomes full.

##### File system inputs / outputs
These are caused from reading in data from files and writing data to files.

##### Socket messages sent / received
Coming soon

##### Signals delivered
Coming soon

##### Page size
This is the fixed-length memory in the virtual memory space… If the program tries to access outside of the current available page(s), the a page fault occurs. Page lookups can be sped up with page lookup tables. 

##### Exit Status
Indicates the successs/failure(non-zero) of the program execution.



### Example Output of /usr/bin/time –v :

```
User time (seconds): 240.66
System time (seconds): 850.40
Percent of CPU this job got: 86%
Elapsed (wall clock) time (h:mm:ss or m:ss): 21:05.35
Average shared text size (kbytes): 0
Average unshared data size (kbytes): 0
Average stack size (kbytes): 0
Average total size (kbytes): 0
Maximum resident set size (kbytes): 16912
Average resident set size (kbytes): 0
Major (requiring I/O) page faults: 0
Minor (reclaiming a frame) page faults: 1108
Voluntary context switches: 3688
Involuntary context switches: 1148
Swaps: 0
File system inputs: 0
File system outputs: 22515720
Socket messages sent: 0
Socket messages received: 0
Signals delivered: 0
Page size (bytes): 4096
Exit status: 0
```


### References:

##### General Reference
[http://www.linuxintheshell.org/2013/02/26/episode-024-time-and-usrbintime/](http://www.linuxintheshell.org/2013/02/26/episode-024-time-and-usrbintime/)

##### User/System Time
[https://stackoverflow.com/questions/556405/what-do-real-user-and-sys-mean-in-the-output-of-time1](https://stackoverflow.com/questions/556405/what-do-real-user-and-sys-mean-in-the-output-of-time1) 

##### RSS & Page Faults
[https://unix.stackexchange.com/questions/30940/getrusage-system-call-what-is-maximum-resident-set-size](https://unix.stackexchange.com/questions/30940/getrusage-system-call-what-is-maximum-resident-set-size)

[https://unix.stackexchange.com/questions/35129/need-explanation-on-resident-set-size-virtual-size](https://unix.stackexchange.com/questions/35129/need-explanation-on-resident-set-size-virtual-size)

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Introduction_to_System_Administration/s1-memory-virt-details.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Introduction_to_System_Administration/s1-memory-virt-details.html)

[https://www.kernel.org/doc/gorman/html/understand/understand013.html](https://www.kernel.org/doc/gorman/html/understand/understand013.html)

[https://en.wikipedia.org/wiki/Page_fault](https://en.wikipedia.org/wiki/Page_fault)

[https://en.wikipedia.org/wiki/Page_(computer_memory)](https://en.wikipedia.org/wiki/Page_\(computer_memory\))

[https://en.wikipedia.org/wiki/Page_table](https://en.wikipedia.org/wiki/Page_table)



##### Text/Data/Stack Size
[http://menehune.opt.wfu.edu/Kokua/More_SGI/007-2478-008/sgi_html/ch01.html](http://menehune.opt.wfu.edu/Kokua/More_SGI/007-2478-008/sgi_html/ch01.html)
[http://osr507doc.sco.com/en/OSAdminG/det_proc_size.html](http://osr507doc.sco.com/en/OSAdminG/det_proc_size.html)


##### Context Switch
[https://www.cs.duke.edu/courses/spring01/cps110/slides/interleave/sld008.htm](https://www.cs.duke.edu/courses/spring01/cps110/slides/interleave/sld008.htm)
[https://en.wikipedia.org/wiki/Context_switch](https://en.wikipedia.org/wiki/Context_switch)


##### Swaps
[https://www.centos.org/docs/5/html/5.2/Deployment_Guide/s1-swap-what-is.html](https://www.centos.org/docs/5/html/5.2/Deployment_Guide/s1-swap-what-is.html)
[http://www.cyberciti.biz/faq/linux-which-process-is-using-swap/](http://www.cyberciti.biz/faq/linux-which-process-is-using-swap/)

##### Signals
[http://pubs.opengroup.org/onlinepubs/009695399/functions/xsh_chap02_04.html](http://pubs.opengroup.org/onlinepubs/009695399/functions/xsh_chap02_04.html)

##### Sockets
[http://techpubs.sgi.com/library/dynaweb_docs/0530/SGI_Developer/books/IRIX_NetPG/sgi_html/ch04.html](http://techpubs.sgi.com/library/dynaweb_docs/0530/SGI_Developer/books/IRIX_NetPG/sgi_html/ch04.html)



### Questions:

#### How does /usr/bin/time –v work?
When a process has a data structure (called process ?), which stores all of the information that is available for a process (such as run time, usr time, data usage). These things are kept track of as they get switched out of context. When you run a profiling program, it will look into this data structure to obtain the information. (Sources: YYZ & GV)

#### How do we measure time for multiple node, multiple thread
Usr/Syst times: Add them up

Wall Time: Depends on longest thread… Time from begin to end. 

Memory: this can be complicated

YYZ: Global vars are shared over thread, and local vars are kept in each process’s stack.

DMT: If you want to see the effects of cache sharing going on, try running experiments with increasing number of nodes. Ie, run 256 single threads, 128 * 2, 64 * 4, 32 * 8, 16 * 16… see how the times may change. 

Are there better profilers? Supercomputers should have some tool.

At least for “embarrassingly parallel” code where no need to communicate among threads, it should not be too complicated.
(Sources: DMT & YYZ)

