CFS

* on a single cpu system cfs is very simple
* on a multi core system it gets quite complex fast ^^

soooo what is CFS :D?
CFS == completly fair scheduler (a little bit high and mighty but who am i to judge ^^)

lets stay for a moment on a single cpu system, just one core, can you picture how that might work ?
and just as a hint we are talking about a preemtive scheduler :D

------

Details

* timeslice
* priority
* vruntime
* runqueue
* per-core runqueue
* load balancing
* scheduler classes



------

CPU sampling

enter again EBPF :D and also the linux perf tools ;)

on-cpu sampling

easily done with EBPF and also with perf tools

off-cpu sampling

only really doable with EBPF


https://github.com/iovisor/bcc/blob/master/INSTALL.md#arch---aur

/usr/share/bcc/tools/runqslower

