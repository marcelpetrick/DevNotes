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



  