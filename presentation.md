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

* ALU (arithmetic and logic unit)
* CU (control unit)
* Registers


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
