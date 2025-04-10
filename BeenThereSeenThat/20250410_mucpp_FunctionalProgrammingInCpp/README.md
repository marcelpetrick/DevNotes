# Functional Programming in C++

```
Functional Programming in C++

Details

Hosted by think-cell (www.think-cell.com)

***
On April 10th we'll have the honor to welcome Jonathan Müller to our user group. Jonathan is a Software Engineer at think-cell. There, he is responsible for maintaining think-cell's core libraries, which include a custom range library, a fast and convenient JSON parser, and many other utilities and data structures to write elegant C++ code. Before working at think-cell, he wrote many useful open-source C++ libraries. He is also a member of the C++ standardization committee, where he serves as the assistant chair for std::ranges, and a frequent conference speaker.

***
Main talk by Jonathan Müller

"Functional Programming in C++"

Abstract
Functional programming is a declarative way of writing programs by composing functions. In many situations, this can lead to code that is easier to write and understand and less error-prone. However, it requires a shift to a more functional mindset.

This talk gives an introduction to functional programming in C++ using the modern standard library. We will cover algorithms using `std::ranges`, composable error handling with `std::optional` and `std::expected`, algebraic data types, and separating IO from computation. In the end, we'll even cover the M-word.

***
Lightning Talk by Dániel Teubl

"The evolution of a configuration system for UAV actuator monitoring: a refactoring case study"

With this talk, I invite you to look at the evolution of the configuration management implementation of a UAV actuator monitoring system. The system has an SD card slot with a file system, a USB port and an I2C connection for additional sensors. Over time, we evolved the system from purely compile-time configuration to mixed compile-time and run-time configurations. The latest iteration of the configuration system allows some parameter and feature flag changes at run-time and can update the local configuration file with actual values.

During the talk, we will highlight the main differences between the two design. We will explore the influence of some literature, the and usage of language elements like static_assert, templates and lambda functions and idioms like RAII and YAGNI. At the end of the talk, we will compare the usability and memory consumption of each design and collect some lessons learned.

***
Live Stream: TBA

***
Schedule
18:00 -- Welcome with Dinner and Drinks
19:00 -- Welcome by think-cell/MUC++
19:05 — Lightning Talk by Daniel Teubl
19:30 — Main talk by Jonathan Müller
21:30 -- Official End
```

* think-cell: provide ome tool for Powerpoint, for 21 ears; all written in C++; combing from Berlin

## Lightning Talk by Daniel Teubl
* the UAV actuator montorigin
* a refactoring case study
* UAV, flight testing; test automoatization
* QR code for the talk on website: good idea
* configuation file: baseline, itertie approach, database approach
* system: actuator control an montiron unit
* stm32 f446RE as MCU for the board
* UAV has six actuators
* baseline as hardcoded magic numbers in the main.cpp
  * thre yrs ago for the state: dead code, etc.
* v1.3: a config file - config.txt, key value pairs; lots of repeated parsing of lines until values are found
* v1.11: loading the configuration in one go
* problems: configuration schema reflects domain; only manual configuartion change possible
* final version was smaller, by some 5k ines of code, but in executio slower? real time impact; almost nothing
* relied on cppcheck and clang-tidy


## declarative programming - jonathan müller from thinkcell; @foonathan
* functional porogramming is declarative programming by composing functions
* you define sthe state and outcome and some magical system figures out how to compute the result
* Haskell: order of functions does not matter
### advantages
* no bugs due to invalid states, broken invariants
* no bugs due to complex intertwined object references
* no bugs due to race conditins, easier to parallelize

* BUT: functional rpgramming does not neatly map to harware
* harder to optimize
* harder to native tools like debuggers adn profilers
* harder to interact with lbraries
* coice is an enginerring tradeoff

* but c++ is nt a pure fnctional progamming langue
* functional programming s all about comoositio
### 1 composing algorithsm; 2 functions, 3, coposing i/O
## composing algorithsm
* inut: non emtpy list of inteers; output biggest magnitude fof an odd integer in a list
* approach iteratie is quite straight forward
* eager composition with std::Range creates lots of intermediate containers
* compute intermediate results even if not needed; have to deal with intermediate steae
* better: lazy range: std::views
* composition shape: RNAGE - RNAGE
* stdv::transfor - called map in other langues
* generate all pairs: stdv::casretsian_rpoduct(rng1, rng2)
* stdv::zip give a tuple of corresponding elements
* problem: longest contiguous list of subsequent numbers
* imperative is quite messy: lots of states, etc.
* stdv::chunk_by - predicatement splits b not-smaller
* stdv::transform(stdr::size)
* std::isAlpha(..)?
* chunk | stdv::reverse <---- what is this?
* stdv::join flatterns a range of ranges
* stdv::join_with: falttens a arnage of range, but inersting a separator into it
* smallest fibonacci number abve a threshold
  * std::generator<in>: then pass this into std::find_if..

* general takeaways:
  * try to identify small building blocks for solving a probrelm
    * creating ranges; transforming ranges, combinign ranges, splitting ranges joining ranes
  * know your algorithms:
    * min/max; find_if

## composing functions
* std::monostate() as replacement for "void"; but can bestored into containers
* in c++ 6 then an optional will become a range of 0,1 ... and then join and other stuff works

* convoluted implicit code leads to unreadability -> where do you finde developer or this kind of code?
    
    
---

todo: check if sansevieria can flower in germany climate

