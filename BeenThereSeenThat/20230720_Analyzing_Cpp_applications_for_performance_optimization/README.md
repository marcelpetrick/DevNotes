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



TODO add the images from phone

*  
