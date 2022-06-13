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
* KDAB uses docker to run CI, not virtualized
* a trace/recording is completyl self-contained; no more syscalls, no network access, no rendering
* toolset:
  * reverse-continue
  * reverse-step
  * reverse-next
  * reverse-finish
* todo: try out Visual studio code to see how rr works there; with GUI
* else: qtCreator: just like remote debugging
* activate the gdb-output-view (then you can enter there reverse-next, .. to jump back in time)
* also: check the wiki-page from mozilla
* rr also records all subprocesses (children)
* interprocess communication: dbus; record time will work as usual

## GammaRay
* debug in minimum time a codebase which exists for years, graphically insepct the state of the application
* colleague: Volker has started it
* GR is picky, especially for windows; has to be build against the exact version of qt
* for yocto you can built it as part; else it maybe refuses to work or crashes
* remote debugging even possible (on target)
* `gammaray --inject-only -p $(pidof lab_example)`
* `ps aux | grep lab`
* then it shows which sockets you have connected to
* launch then gammaray: connect to running apps (with open sockets)
* GR also has a preview of the running application; pick elements, select items, 
* CTRL+shift+LMB: then picking inside the real app is even possible
* minimumheight of qt: set to 1 instead of 0! to get rid of the problem
* delete on runtime the items
* widgets > analyze paintings: [F9] - every single draw call; even with cost numbers
* also a gamechanger for coplex model-view-hierarchies; proxies, ..
* also shows statistics for object-creation; and also debugging levels

[short break]

### state machines
* dropped in qt6?
* benefit; restructuring easy, signals and slots for each transtion, simple way to decouple the logic; simple to expand because everyone says "for simple things i can implement it on my own"
* statemachines constrain you a bit; but constraints are good because they also limit your 'creativity' (for better readability)
* use scxml: state chart xml; w3c-standard for future use; also in Qt5.15; use this for further development instead of Qt-state-machines

* GR is split into two parts: core, which injects itself, and the UI-part, which gives insight into the values
* usable also for quickscenes: using the samegame-example from qt
* `gammaray ./samegame`
* cheat by changing the type of the blocks possible now; but where does this come in handy now?
  * good to debug mouseareas, which were maybe not fitting to a graphical item -> manually tracking and disabling items -> waste of time
  * item-picker:  inspect-tool; multiple overlaping mouse-areas -> now maybe two mouseareas are collecting events
  * "Problems"-section: items visible, but out of view; or other issues can be checked there
  * overdrawing visualisation! (check this)
  * imx-platforms: execeptionally bad at hardware-rendering
  * not the gpu or cpu too slow, but the memory bus is too slow, so the whole machine slows down
  * reduce overdrawing to increase performance
  * put a clear color as background-item instead of using the background-color of the root-node
* batching view: why important? gpu just same freqneuncy like the cpu, gpu is only fast when you can do lots of things in parellel; just works if there is not lots of clipping
  * with enabled clipping view now everything is reddish: this is a red flag; batching view shows everything colorful; so the gpu is not properly utilitzed; "clip: true" means that you don't want to clip manually properly
  * try to get rid of the "red" by checking which is most heavy; unclear if this is always a proper "low hanging fruit" and has any impact
* openGL frame debugger would help to see the paint calls: renderdoc (official tool) <- check this
* so GR is helpful for live-prototyping and adjusting measurements; but developer has to transfer the changes
* RMB on qml-item can open the respective file for easier editing (`go to creation`); only works if qml is integrated as ressources
* can you run it in a container: yes, should be relatively painless

## Sanitizers
* sanitizers are compiler addons
* missing init of memory, somethign was freed and then accessed later; big potential to shot yourself in the back
* with sanitizers and c++ it becomes really hard to write crappy code
* evolution of valgrind
* available ones:
  * address: memory error detector
  * thread: detect data races
  * undefined: check code for undefined behaviour
  * and more, with mixed maturity levels
* valgrind has a problem due to slowness and lots of synchronized threads
* google paid very smart people to solve this problem: valgrind as compiler plugin
  * add checks during compilation instead -> much larger setup-overhead; compile app in specific mode; everytime you run it, the checks will be there; but multiple checks will maybe be optimized away
  * he uses: address and undefined always enabled
* demo: crashing app, he could get in with gdb and debug
* how to: qtcreator > projects page, then clone the debug build; just look into the cmake cache variables and then toggle it (check: advanced as well);  CMAKE_CXX_FLAGS; -fsanitize=adress,undefined (thread and address don't work well together - make different build configs)
  * now while running it will give output with undefined behaviour messages, etc. then also the sigsegv has more information, with context, really detailed! read the report: always read it from the top
  * in our case: forgot to init the data-member (m_ui)
* using a sanitized build has small overhead (he usually does) and has impact of 1 min instead of 20sec running
* meant for errors: no warnings
* continue running: -fsanizte-recover=all, then eset the environment var ASAN_OPTIONS=halt_on_error=0; BUT THIS IS NOT RECOMMENDED!
  * it is really suggested to fix the first appearing issue first
* example: "deepblue"; with generator; without optimiatzion it is 42, with -o1 it is 0. wow! but with address-sanitizer it shows again 42
  * so what is the problem here? therefore opt in addditional checks; all of them are rock-solid; no fase positives
  * "capture by reference is not a good thing" -> was a problem for the generator-lambda
  * 55 ways for effective c++ code; scott myers? <-- check this; -Weffc++
* also: leak checks for free
* "when you can read the backtrace, you are responsible for the leak" - simple
  * eversthing else is internal and can mostly be ignored
* maybe also create custom-suppression files to filter common things with used libs

* his workflow: source the script (to start in a well-defined session): check the common options
  * gdb: p _asan_describe_address(0x12342134124) -> gets you the source code calling this; who was allocating this originally? quite useful
* undefined behaviour sanitizer: will also tell what to do as solution
* debugging/data-folder has also a setup-file.sh, which; but maybe add the line for the lambda as well

### thread sanitizers
* deadlocks, data-races; destruction of locked mutex; "printf output creates barrier, which enables internal locking and magically the issue is gone"
* then you have to build Qt as well and the libs which do the threading; so much larger overhead
* in former times the clang-lib worked better, but GCC's libstdc++ should work now as well
* example "race()"
* lock order ivnersion problem: abba - classic problem of a deadlock
* p.75; sanitizers vs. valgrind
* sanitizers are much faster and use less memory
* no recompilation is required for Valgrind; all libraries linked into your application will be checked by Valgrind
  * some functionalities are not possible with valgrind at alle (like alignment fault and integer overflow)
* workflow: every patch which will be uploaded will be contiuously tested for win/mac/linux and for linux also the adress- and undefined behaviour-setup
  * directly get the report if something fails
  * nightly builds do static code analysis on top
* with qmake the suggested way is CONFIG+="sanitizer sanitize_address" ... (because qmake passes the flags only to compiler, not linker!)
* else it will be a linker error
* for qmkae using some ld-flag would also help, if you dont want to integrate it like this

## Profiling
* Linux Perf and heaptrack
* not talking today about QML: should not be used to implement business logic
* enable - and -02 (always with optimizations): ith std::vector and no optimizations would be very bad; with optimizations it works on level with C; "zero cost overhead" for cpp
  * only true to the optimized versions; else always you have to pay for the optimized version
  * do not profile un-optimized things; always -g and -O2
* godbolt: compiler explorer: check for the the de-virtualisation-example

### Perf
* perf list, stat, record, report
* has a Qt-Creator-integration (now)
* whole performance subsystem inside the kernel; as user-space-app you can't have access to the hardware
* has then access to pmu and trace points; good for measuring lock contention time
* 99% of the time cycles and context switches are the wanted topics
* check: zip-file: file `perf.init`; if this does not work, then read the reported errors
* but increases as well the attack surface (on dev machine ok, on server not)
* perf list: (example of targets for measurements)
  * branch prediction (spectre, meltdown, ..): branch-misses are very costly; but optimizing your code to branch-misses is nowadays not important
  * cpu-cycle versus cpu-instruction: first ones are equal to each other
  * context-switches
* perf stat: better than time
  * example: `ex_container QList`
  * time gives three numbers: real, user, sys: user+sys can be bigger than real, bceause of multithreading
* pikaur: what is this? 
* time -v ex_container QList (?)
* never ever use time again, always use perf stat: QList has 7 billion cycles, qvector 5 billions
  * on newer intel cpus: even slot-level is shown
  * less "backend bound" slots is better: backend means "waiting for file input"
  * even use perf list /d
  * Qvector better than qlist because contiguous buffer, no random pointer chasing (on the heap)
* `perf stat -repeat 10 -- my benchmark` with cycles to avoid fluctutations: but still pick targets which fluctuate less; so to change something were something can be said with high confidence; don't optimize noise
* workflow: write a very specific benchmark for one part of the app; then micro-optimize this one
* makes no sense for a ui-application, literally just for benchmarks
* example: ex_branches (with param 1 it sorts the data; branch predictior kicks in) -> result: sorting additionally the data literally makes it faster!
* workflow for number crunching: write a proxy, which also logs all the inputs from customer; and then optimize based on the input

* nperf record: i clicked on a button and it was slow; i resized the window and it was slow ... the case with ui-application
* find the code: what are we executing here?
* f-instruments for gcc in former time? writes entry- and exit-log for each function; but has huge overhead; instrumentation makes tracing slow and distorted
* so instead we do sampling: perf record (roughly a thousand samples per second); checks instruction pointer; map it then to a functio name, file name, line number, literally points to code which is executed
* result: Qt code, malloc, free: not only code which you called
  * at record time is sampled, at analyze-time it does the unwinding
  * perf record --call-graph dwarf ./ex_randomfedora, arch: debuginfoD_urls
  * debuginfod - check this
  * dwarf: copy also the first kilobytes of the stack to be able to unwind the stack! makes the trace bigger, but allows more feedback
* hotspot is a drop-in replacement - more graphical; always to go the flamegraph
  * anything you cannot read anymore in the flamegraph, is mostly optimized and does not need attention; really useful visualisation tool
  * meaning of the red color: no real meaning
  * caller/callee grouping: also gives then the file+linenumber
* better example: mandelbrot example; pretty badly written to show lots of use-cases
  * flamegraph shows the "drawMangelbrot" -> immediately going to caller/callee would be way to fast; better: prepare a benchmark for that specific function -> `mandelbrot -b 10` -> now it is possible to measure the ground truth as baseline
  * perf record, then hotspot, but then we get a broken flamegraph: but why is this the case? simply ignore that part where unwinding happened to work
  * sort by "inclusive amount of cycles" -> 50% for one chunk
  * perf stat:
    * -d : more datapoints
    * -r 5 : five runs
    * --output norm.txt : report to file for later checks (and maybe for the commit message)
* but beware of the diminishing returns .. but the treadmill has to be done
* next to the lab_mandelbrot is also a sol_mandelbrot: with even more optimizations
* the pimple-pattern of qt prevents compiler-optimizations
