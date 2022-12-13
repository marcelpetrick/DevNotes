# 20221213 mucpp meeting: Timur Doumler - Low latency C++
* developer for CLion, ReSharper C++, Rider
* cpp 17 and 20 standardiztion meetings; check what cpp20 and 23 brings
* http://timur.audio

## Performance
* various different concepts: throughput vs. latency
* and what is "real time": not only means t produce the correct result, but it alsohas to produce it within a certain amount of time
* orthogonal ends of a spectrum; and depending on which side you care more, then differnt optimizations
* high throughut; optimise hte average case performeance
* versus: low latency: optimise the worst cast performance
* efficiency: reduce the amount of work/energy required to perform the task
* low latency: HFT (high frequency trading), audio, games, "embedded"
* throughout: internet servers, scientific simulations, quantitative finance

## hot path - concept
* gaming 5-16 ms, audio 1-5 ms, HFT 100ns to 10 micro-s; GUI 100ms
* consequences of "ho path" missing deadline
  * gaming: dropped video frames
  * audio: audible clicks/glitches
  * HFT: lost money
  * embedded: lives (airbag)
* topology:
  * audio: one hot path
  * gaming: parallel hot paths for rendering, one for the world updates, so multiple optimizations
* howe mch control do you have over the platform you are running on?
  * audio/gaming: a bit control
  * HFT: more performance and control
  * embedded: total control, less performance
* 
## Why use C++ for low-latency programming?
* manual memory management: big plus
  * influence over allocations, deallocations
* scalable zero-cost abstrations: templates, algorithmes
* huge body of existing libraries and framewokrs (in comparison to Rust)
  * JUCE for audio, Unreal Engine for gaming

* two categories:
  * targeting efficiency
  * targetting low latency
* most crucioa thing: measuring!
  * you donÄt know if something is efficient, fast, etc. unless you mesure it
  * recommendations: fedor pikus, the art of writing efficient programs (book, 2021)
  * Dave rowland: optimising a real-time audio processing library (2022; talk)
* performance analyse: measuring cahce misses, branch mispredicts, syscalls ...
* nspect the generated asembly: compiler explorer
* benchmarking: google benchmark gperftools, Nonius
* actual code vs. microbenchmarks
  * microbenchmarks are tricky: warm the cache, radnomise the heap, measure release build, be mindful of optimisations changing wat code you are measuring
* writing efficient code requires:
  * knowledge of the programming language,
  * .. the libraries used
  * .. of the compiler
    * x86: Agner Fog's optimisation manuals (check this)
	* ARM: ???
	
## optimizations
* avoid unnecessary work
* avoid unnecessary copies
* avoid unnceessary function calls
* inline functions
* use std::variant /CRTP instead of virtual functions
* constexpr all the things
* template metaprogramming
* fast approvximations

low level manipulation in c++
* alsiaing rules
* alignment rules
* ..

* use powers of two for sizes (compiler will replace div/mod with bithsifts)
* undefined behaviour can be your friend: UB & the optimiser
* [[asume]] - in C++23; inject more undefined behaviour into the compiler
* [[assume(x >= 0)]]; <-- just assume, don't measure
  * optimizes to just 3 lines of assembler
* assume also for audio data that it is not null or negative .. good
* sorting before std::count_if will help; just one mispredict
* [[likely]] and [[unlikely]]
  * don't affect the branch predictor, can affect the code layout
  * see amir kirsh and Tomer vromen: c++ likely and unlikely: a journey through branch prediction and compiler optimizations (talk, 2022)
* avoid data dependencies (andrei alexanderescu: writing fast code, 2015)
* SIMD: ARM NEON; sometimes auto-vectorizations, explicit vectorisation using SIMD libraries/intrinsics, SWAR (SIMD within a register)
  * different elements of the same array in a loop prevdnts auto-vec.
* when you go away from the CPU you have memory and memory hierarchies
  * registers and ABI
  * non-trivial destructor: prevennt register optimizaions (for clang)
* miniise data cache misses
  * data localitiy, avoid node based containers, cache friendyl associate containers: std::flat/std::flat_map
  * "almost always vector" 
  * mixins, CRTP?
  * keep the cache warm: data case - periodicaly poke data on a timer
  * isntruction cache: periodically run the critical path with dummy input/output (wow, quite interesting)
  
## Targetting low latency
* what not do do in the critical path
* dynamic memor allocations
i/o
blocking the hread
context swiches/mode swithes (kernel/user space)
syscalls/calling into unknown code
loops without definite bounds
algorithms > O(1)

* bad algos which allocate memory:
  * stable sort
  * stable partition 
  * inmerge format?
  
* static_vector<T, capacity>
* custom allocators: TCmalloc from google is optimized
* C++17: monotonic allocators, pool allocators
* frame allocator, arena allocator, double-ended allocator
lock free allocators
* avoid blocking: std::mutex, but use std::Atomic
* alternative: spinlock with progressive back-off (efficient try_lock is lock-free)

### sharing data between threads
* read copy, update (RCU): wait-free reading "CAS loop"
* wait-free writin: double-bufferin or SeqLock (talk coming in 2023)

### error handling
* no exceptions
* error codes (not great)
* std::optional (not great)
* std::expected (reat, comng in cpp23)

* prevent memory form being swapped out
  * lock adress range into RAM: mlock (POSIX), VirtualLock (Windows)

* avoid context switches/mode switches
  * thread priority
  * deterministic thread scheulder for real-time operating systems
  * Kernel bypass: for ether net adapters
* turn off hyperthreading
* pin criticl path thread to ne cpu core (just in case you dont care about the efficiency of the other threads)

* chekc later: github.com/crill-dev/crill
