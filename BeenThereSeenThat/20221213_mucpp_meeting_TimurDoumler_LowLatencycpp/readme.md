# 20221213 mucpp meeting: Timur Doumler - Low latency C++
* developer for CLion, ReSharper C++, Rider
* CPP 17 and 20 standardization meetings; refresh knowledge what CPP20 and 23 brings to the table
* http://timur.audio

## Performance
* various different concepts: throughput vs. latency
* and what is "real time": not only means t produce the correct result, but it also has to produce it within a certain amount of time
* orthogonal ends of a spectrum; and depending on which side you care more, then different optimizations
* high throughput; optimize the average case performance
* versus: low latency: optimize the worst cast performance
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
* scalable zero-cost abstractions: templates, algorithms
* huge body of existing libraries and frameworks (in comparison to Rust)
  * JUCE for audio, Unreal Engine for gaming

* two categories:
  * targeting efficiency
  * targeting low latency
* most crucial thing: measuring!
  * you donÄt know if something is efficient, fast, etc. unless you measure it
  * recommendations: Fedor Pikus, the art of writing efficient programs (book, 2021)
  * Dave Rowland: optimising a real-time audio processing library (2022; talk)
* performance analyse: measuring cache misses, branch mispredicts, syscalls ...
* inspect the generated asembly: compiler explorer
* benchmarking: google benchmark gperftools, Nonius
* actual code vs. microbenchmarks
  * microbenchmarks are tricky: warm the cache, randomize the heap, measure release build, be mindful of optimizations changing what code you are measuring
* writing efficient code requires:
  * knowledge of the programming language,
  * .. the libraries used
  * .. of the compiler
    * x86: Agner Fog's optimization manuals (check this)
	* ARM: ???
	
## optimizations
* avoid unnecessary work
* avoid unnecessary copies
* avoid unnecessary function calls
* inline functions
* use std::variant /CRTP instead of virtual functions
* constexpr all the things
* template metaprogramming
* fast approximations

### low level manipulation in c++
* aliasing rules
* alignment rules
* ..

* use powers of two for sizes (compiler will replace div/mod with bithsifts)
* undefined behaviour can be your friend: UB & the optimiser
* [[assume]] - in C++23; inject more undefined behaviour into the compiler
* [[assume(x >= 0)]]; <-- just assume, don't measure
  * optimizes to just 3 lines of assembler
* assume also for audio data that it is not null or negative .. good
* sorting before std::count_if will help; just one mispredict
* [[likely]] and [[unlikely]]
  * don't affect the branch predictor, can affect the code layout
  * see Amir Kirsh and Tomer Vromen: c++ likely and unlikely: a journey through branch prediction and compiler optimizations (talk, 2022)
* avoid data dependencies (Andrei Alexanderescu: writing fast code, 2015)
* SIMD: ARM NEON; sometimes auto-vectorizations, explicit vectorisation using SIMD libraries/intrinsics, SWAR (SIMD within a register)
  * different elements of the same array in a loop prevents auto-vec.
* when you go away from the CPU you have memory and memory hierarchies
  * registers and ABI
  * non-trivial destructor: prevent register optimizations (for clang)
* minimize data cache misses
  * data locality, avoid node based containers, cache friendly associate containers: std::flat/std::flat_map
  * "almost always vector" 
  * mixins, CRTP?
  * keep the cache warm: data case - periodically poke data on a timer
  * instruction cache: periodically run the critical path with dummy input/output (wow, quite interesting)
  
## Targetting low latency
* what not do do in the critical path
* dynamic memory allocations
* i/o
* blocking the thread
* context switches/mode switches (kernel/user space)
* syscalls/calling into unknown code
* loops without definite bounds
* algorithms > O(1)

* bad algos which allocate memory:
  * stable sort
  * stable partition 
  * inmerge format?
  
* static_vector<T, capacity>
* custom allocators: TCmalloc from google is optimized
* C++17: monotonic allocators, pool allocators
* frame allocator, arena allocator, double-ended allocator
* lock free allocators
* avoid blocking: std::mutex, but use std::Atomic
* alternative: spinlock with progressive back-off (efficient try_lock is lock-free)

### sharing data between threads
* read copy, update (RCU): wait-free reading "CAS loop"
* wait-free writing: double-bufferin or SeqLock (talk coming in 2023)

### error handling
* no exceptions
* error codes (not great)
* std::optional (not great)
* std::expected (great, coming in cpp23)

* prevent memory form being swapped out
  * lock address range into RAM: mlock (POSIX), VirtualLock (Windows)

* avoid context switches/mode switches
  * thread priority
  * deterministic thread scheduler for real-time operating systems
  * Kernel bypass: for ether net adapters
* turn off hyperthreading
* pin critical path thread to ne cpu core (just in case you don't care about the efficiency of the other threads)

* check later: github.com/crill-dev/crill - plan to make a lib for low latency features
