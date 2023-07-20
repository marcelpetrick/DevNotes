# 20230720 Analyzing C++ applications for performance optimization

```
On July, 20th, we have the pleasure to welcome Elizaveta Shulankina to our user group. Elizaveta Shulankina is a senior software development engineer at Intel Corporation with 7 years of experience, using C++ as a primary tool. She is part of the team developing Intel Profiler tools, these tools help design and optimize code for modern computer architectures. She holds a Master's degree in Computer Science from State University of Nizhniy Novgorod (UNN), Russia. *** **Abstract**: Some of us, willingly or not, have needed to analyze the code for performance improvements. Of course, we resorted to various code profilers to figure out what was wrong with our perfectly written code... And more often than not, the profiler surprised us by pointing out a performance bottleneck in the code! This talk will be an introduction to C++ application performance optimization using tools such as Intel VTune Profiler and Intel Advisor. We'll briefly walk through the performance optimization steps, then take a small C++ application and ask VTune and Advisor to help us understand what's going on, what the performance bottlenecks are and how we can deal with them to make our application memory and compute efficient. We'll do a few iterations of tunning this C++ application and see how it speeds up. *** **Agenda:** 19:00 -- Welcome with Snacks and Drinks 19:30 -- Welcome at Zeiss 19:40 -- Main talk by Elizaveta Shulankina \~21:00 -- Open Discussions 22:00 -- Official End \*\*\* **Link to the live stream: TBA** \*\*\* **Sponsor**: Research Microscopy Solutions Deutschland (https://www.zeiss.de/mikroskopie/home.html)
```

## Introduction by the R&D guys from Zeiss
* Zeiss ZEN als platform
* data acquistion from the microscope as first step (multichannel, z-stack, panoramo and stitching)
* processing of the images & data
* descale, denoise, deconvolute
* dealing with high data loads
* store, view and load this data - this is mostly happening with C++ and Python
* pollen of dandelion (photo) - TODO insert here
* C++ in 80% of their products

## The real talk: analyzing C++ apps ..
### about performance optimization
* increased speed or efficiency of software
* better user experience, cost reduction, reliability increase
* sometimes: no ability to use a more powerful hardware to meet performance needs
### how to tune?
* find metric for the optimization cirtiera
* and second a stopping condition
* examples:
  * execution time
  * compute performance
  * frame rate
  * memory bandwith
![](img01.png)
* top down, closed loop methodology: priorization of the optimization
  * 1. System level tuning (processor, memory, network, disk)
  * 2. app level tuning: locking & synchronization, heap interaction, threading model, APIs used
  * 3. microarchitecture level tuning: instruction efficiency, branch preditiction/speculation, caches, data alignment/Byte Boundaries
 ![](img02.png) 
* 1. start with baseline, 2. go through performance improvement iterations, 3. break when a stopping condition is met
*  means: gather data, analyze data, tune, test .. repeat
![](img03.png)

### how to build a solid baseline?
* use right compiler falgs: compile in reelease mode, compile with optimization flags
* compile for the target cpu
* use optimized libraries
¹[](img04.png)
### how to make a right workload
* meaureable
* reproducible
* static
* reprensentative
* stable
### performance optimization levels
* first: design (!): revising the code architecture and design to avoid potential downtimes
* algorithms and data structures: choosing better algorithms that are of the best complexitiy and the most suitable
* source code and compilers: loop/function optimization, parallelization, ..

## looking at the app of the day: n-body gravity simulation
* some kind of HPC application
* baseline is 17min for a run on a quite performant platform (Xeon, 96 logical cores, 144 GB RAM)
* goal is to execute it in less than 3 seconds
### finding hotspots
* GravitySimulation::run is of course the hotspot
* cpu-utilization is almost zero, not multithreaded yet
* using OpenMP: just add `pragma omp parallel` for - less intrusive for the code
  * already down to 19s
* code is auto-vectorized, but the vectorization is not efficient (maybe not the right data-types or not good memory access?, also about the instruction set)
* what is vectorization? transform sequential code to explot vector processing capabilities
¹[](img05.png)
* examples: Intel SSE or SSE2
* Intel AVX, AVX2
* multithreading & vectorization speed-up
  * in the real world the result is bit less good than the optimal idal execution speed; see Amdahl's law: https://en.wikipedia.org/wiki/Amdahl%27s_law
* look at the recommendations to improve vectorization..
* chosing a proper datatype (float) reduces the time by 50% again: 10s
* using 512 bit-package-nstructions reduced it to 4 seconds
* uArch (micro architecture) optimization: ideal CPI (clocks per instruction) of 0.25
* CPI does not depend on CPU frequency which may change
* why instructions might not retire: frontend-bound; back-end bound, bad speculation
* iregular memory access patterns present: works better when the data is close together - best: uni-stride access, onstant stride access, worst: variable stride access
* SIMD is effective with unit stride access: array of structures is bad; structure of arrays is better and SIMD compatible!
* therefore rewrite the code or use the SDLT library: now it takes just 1.5s
* going deeper by using ASM would be possible, but then you are HW-bound
* best approac is to go: top-down, then focus on execution problems
* also offloading code to accelerators can help

## key points
* use optimized libs when possible: parallel STL, openmp, tbb, mkl, ipl
* get a solid baseline
* define optimization criteria for your workload
* profile your code
* fix your vode design and algorithms first

TODO add the images from phone
