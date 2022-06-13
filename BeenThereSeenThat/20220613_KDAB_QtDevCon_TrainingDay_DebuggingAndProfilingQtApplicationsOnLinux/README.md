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
profiling setup for c++ applications (page 77)
linux perf (page 80)
heaptrack (page 124)
conclusion (page 137)

## not part
* qml debugging: qml profiler embedded into qt creator
* windows specific tools from nvidia and vivante for gpu-profiling

* hint: do not put business logic into qml! no javascript
* linux perf and heaptracker are the most important one for profiling, evne for embedded applications

# please write down 3 things you hope to learn in this training
* targeting embedded devices
* huge boon of qt: target multiple things from the same code base
* take care that a subset of the stuff needs to be buildable on x86; even if you target ARM devices, but don't leave the tools out which do not target arm (natively)
