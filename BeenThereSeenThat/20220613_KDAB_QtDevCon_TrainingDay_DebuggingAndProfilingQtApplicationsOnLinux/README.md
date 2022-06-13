# 20220613 Debugging and Profiling Qt Applications on Linux

* trainer: Milian Wolff
* usually a three day training

## topics:
* debug symbols, compiler optimiations (page8)
* debugger (page 13)
* gammaray (page32)
* sanitizers (page 58)
* most notably: existance of the tools!
* kickstart the tooling experience

## rr - reverse debugger (like gdb)
* jumping back in time
* only gammaaray is qt specific; rest is also applicable for fortran, rust, ..

## more topics
* profiling setup for c++ applications (page 77)
* linux perf (page 80)
* heaptrack (page 124)
* conclusion (page 137)

## not part
* qml debugging: qml profiler embedded into qt creator
* windows specific tools from nvidia and vivante for gpu-profiling

* hint: do not put business logic into qml! no javascript
* linux perf and heaptracker are the most important one for profiling, evne for embedded applications

# please write down 3 things you hope to learn in this training
* targeting embedded devices
* huge boon of qt: target multiple things from the same code base
* take care that a subset of the stuff needs to be buildable on x86; even if you target ARM devices, but don't leave the tools out which do not target arm (natively)

* Milian Wolff comes from KDE development, FOSS, C++ experience, Qt experience, tries to include the scientific approach; especially when measuring improvements of performance

## debugging
* debugger, gammaray, sanitizers
* debug symboles, from instructionpointer to function name and line number
  * how are they related to compiler-optimizations:
  * needed for all of the tools!
  * have no inherent runtime overhead, just not used in case of no need
  * just if needed, they are loaded and actually used
  * but considerable disk space overhead; and also don't leak those details to your customers
  * can be splitinto a separate file and only deployed if needed (yocto for instance separates it by default)
  * independent of compiler optimizations
* qmake: either release build or debug build (dog slow?)

* to verify if your applcation or library has debug symboles:
  * use your debugger; GDB's info shared
  * objdump
* build code and  dependencies with debug support:
  * Qt: conigure -debug
  cmake: cmake -DCMAKE_BUILD_TYPE=Debug (relwithdebinfo)
* or invole the compiler with gcc/clang -o -g

* profile option: is just release with debug symbols on top
* release is completely useless, because you can run it, but don't get the information if something faulty happens

## rr
* showing "lab_cache" exmplae application: displaying delta of sines
* conditional breakpoint maybe as first try to figure out why the plot is so distorted aftre resizing
* he uses gdb: start&attach, set bp and edit with "cond 1 (original -cached) > 1. breaks with original 0.12 and cached -3e+19 -> out of range excess
* without tools: essentially restart the application in case you want to find the previous values ... a nightmare -> therefore we want to be able to jump back in time
*  rr very closely related to gdb, but also differnt
* rr should be properly integrated into visual studio
* time travel debugging tool for x86 linux
* records the whole application runtime
* ehances gdb by allowing fast reverse execution
* can be used to record non deterministic failures and replay them deterministically
* low overhed (~1.2 slowdown)
* really shines when a failure occurs randomlny, once in a hundred runs
* rr explots the performance measuring unit: works with intel and kernel >= 3.5 and amd zen
* works in VmWare in case of performance counters are virtualized
* ARM architecture not supported
* the tracefiles can get quite large; for the few seconds of the lab-app it was 6 Mibyte
* he does a replay and the "reverse-next" to see that the index is 1032; but it should be a maximum of 1000.
  * so where is the m_values buffer created? hardware watchpoint (!) -> he finds the location this bufer is initiaoized; but just with lenght 1000!
  * creating "checkpoints" to jump between different locations
* "so it is less code, so it is already better y defininition"
* replaced then the raw buffer with a std::vector
* also replaced the index access with at()
* rr record to capture flaky behaviour -> with an assertion; the "awatch workerthreadhasstarted" (not a typo)
* go back in time in case of an assertion! was ist set properly, what is the value, see the code (computation bug)
* "info locals" - no symbol table in case of stripped exectuable

