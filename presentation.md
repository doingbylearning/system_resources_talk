%title: CPUs / Memory / Network Controllers, what are they and how do they work ?
%author: Markus Burger
%date: 2019-11-27

-> # What are we even talking about here ? <-

* We will cover a *lot* of theory (again^^)
* We will explore from the low to the high level how things work under the hood
* We will learn hopefully how these things fit together :D


Who here has heard about things like assembly/numa/cache coherency or the different kernel schedulers ?

--------------------------------------------------
-> # Let's start out with the basics shall we :D <-

soooooo what even is a cpu, what basic components are involved here ? (and yes its really simplistic for now)

* ALU arithmetic and logic unit
* CU control unit
* Registers

soooo what the hell are those :D?

ALU: contains circuits that do arithmetic and logic operations
CU: contains circuits that fetch an instruction from memory, decode it and pass the instruction to ALU, Registers, RAM or I/O depending upon what the instruction is
Registers: are memory storage often named as immediate memory and they assist ALU and CU in different operations

For example, During an addition operation if there is intermediate value, it may be stored to one of the registers called accumulator register.

Similarly, stack pointer register may be used to keep track of a program when a call to a sub-routine or function is made.

Program counter or instruction counter register may help CU find the address of next instruction during the execution of a program.

Status or flag register may contain the status of certain operation. For example, if an addition operation results in carry, the carry bit in flag register may turn ON

--------------------------------------------------
-> # ofc there is waaaay more <-

* Logic blocks that enable OOO (out of order execution)
* SIMD units (for vectorization)
* Cache controllers (coherence/consisticy protocols, requests, scheduling)
* Floating point units
* random number generator
* etc etc etc

hmm what are those and what are they used for ?

--------------------------------------------------
-> # L1/L2/L3 cache <-

L1 cache:
* fastest of them all with a latency of ~1ns
* split into 2 different areas with a typical size of 64kb, one for data and one for instructions
* typically exclusive per core

L2 cache:
* latency of ~4ns
* simply a bigger but slower cache also exclusive per core

L3 cache:
* latency of ~16ns
* biggest of them all
* shared between cores
* typicaly acts more as a cache coherency protocol enabler than as a cache
* is inclusive of all data in L1/L2

--------------------------------------------------
-> # Multi socket systems ? / NUMA ? <-

ok i think i got it now :D

but wait there is more
        \\   ^__^
         \\  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||


soo lets look at the numbers again what happens when we suddenly have multiple NUMA domains to worry about
( taken for the AMD EPYC Rome platform )

Level 1 cache access: 1.6 ns
Level 2 cache access: 4.8 ns
Level 3 cache access: 15.2 ns
Remote level 3 cache access: 63 ns
Local memory access: 75 ns
Remote memory access: 130 ns

wooooah thats quite and increase!
but what does things like "local" or "remote" memory mean cO?
and can we have multiple NUMA domains while still having only one socket cO?

--------------------------------------------------
-> # UMA / NUMA ? <-

what the hell is UAM or NUMA xD?

* UMA: uniform memory access
* NUMA: non-uniform memory access

Why does this matter ?

--------------------------------------------------
-> # NUMA <-

sooo now we know the difference between UMA and NUMA

how does this look like in practise and why should you care ^^
atm we only have UMA nodes in AWS, but that doesnt mean that there is not a NUMA system sitting underneath it
+ there are *real* NUMA instances available so you never know when you need it ;)


lets take a look at a typical output of *numastat -v* on a mesos slave from our system
Per-node numastat info (in MBs):
                          Node 0           Total
                 --------------- ---------------
Numa_Hit             29189672.95     29189672.95
Numa_Miss                   0.00            0.00
Numa_Foreign                0.00            0.00
Interleave_Hit            156.18          156.18
Local_Node           29189672.95     29189672.95
Other_Node                  0.00            0.00

can anybody tell me exactly what we are looking at here ?

--------------------------------------------------
-> # Mooooving on <-

Anybody know how processes are scheduled in a typical linux based system ?

--------------------------------------------------
-> # Linux CFS <-



--------------------------------------------------
-> #  <-

--------------------------------------------------
-> #  <-

NOTES:
https://medium.com/hungys-blog/linux-kernel-process-scheduling-8ce05939fabd
https://www.infradead.org/~mchehab/kernel_docs/unsorted/cachetlb.html
https://www.kernel.org/doc/html/latest/admin-guide/mm/numaperf.html
https://www.kernel.org/doc/html/latest/admin-guide/mm/concepts.html
https://blogs.igalia.com/dpino/2015/10/15/multicore-architectures-and-cpu-affinity/
https://www.glennklockwood.com/hpc-howtos/process-affinity.html
https://whatis.techtarget.com/definition/register
http://www.sciencehq.com/computing-technology/cpu-registers.html
https://www.makeuseof.com/tag/cpu-technology-explained/
https://www.makeuseof.com/tag/what-is-cpu-cache/
https://www.recurse.com/blog/7-understanding-c-by-learning-assembly
https://www.quora.com/What-is-an-intuitive-explanation-of-how-CPU-registers-work
https://whatis.techtarget.com/definition/register
https://www.quora.com/What-are-the-three-main-components-of-a-CPU

