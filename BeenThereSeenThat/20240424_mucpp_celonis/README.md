# 20240424  mucpp at celonis

```

File I/O: Past, Present, and Future
File I/O: Past, Present, and Future
Details

This month we have the great pleasure to welcome Guy Davidson to our user group. Guy has been writing games and using C++ for longer than most people have been alive. After a nearly 25 year stint at Creative Assembly, leaving as Head of Engineering Practice, he is now enjoying the freelance lifestyle and has a couple of exciting projects on the boil.

He is the co-author of Beautiful C++, a voting member of the C++ Standards Committee, a lifelong mathematician and whiles away his copious spare time playing the piano, singing first bass in the Brighton Festival Chorus, and experimenting in the kitchen.
You’ll find him on some of the socials as hatcat01

******
Registration (Important!)
In person attendees need to sign a mandatory form with the required information. You will get per Email an Invite to read and agree to Celonis' Non disclosure agreement (NDA). The registration for the NDA is now closed. If you were unable to sign the NDA in time, we apologize for the inconvenience and are looking forward to welcome you at a future event.

Please note that without the NDA no access to the Celonis Office can be granted.

Thank you very much for your comprehension. We are looking forward to being your host!

******
Abstract
If you have played a game on a computer in the last few decades, you will most likely have encountered a loading screen. This is used to advertise to the player that, among other things, data is being loaded from a storage device into the game. But why does this exist, why does it take so long, and how can we improve matters for the player?

In this talk we will discover the history of games and their development environments, the relationship between address space, RAM and storage hardware, how C++ abstracts file I/O and why it might not be the best fit for game developers, how a 64-bit address space changes everything, how #embed will change everything, and how C++29 (yes, 29) may upset the applecart yet again.

Although this talk is aimed at game developers who are often Windows programmers, it is relevant to anyone who has to read large amounts of data from local storage. Expect tales of woe, discovery and jubilation as I describe every surprising little thing I've learned about file I/O over the past 40 years and how C++ is heading for a great future in games.

******
Lightning Talk

Title: homcc - a traffic-efficient distributed C/C++ compiler

Abstract: homcc is an open-source, distributed C/C++ compiler which tries to minimize network traffic so that compilations can efficiently be distributed in low-bandwidth network environments. This talk will outline how homcc works, what features are available and how it compares to alternatives.

Presenters: Oliver Layer and Simon Pirsch (both Celonis Software Engineers)

******
Schedule
18:30 -- Open Doors
19:00 -- Welcome by Celonis/MUC++
19:05 -- Lighting Talk by Celonis
~19:45 -- Dinner break
20:30 -- Main talk by Guy Davidson (start of the live stream)
22:00 -- Official End

******
+ feature overview: traffic efficient netowrking, tcp messages, compression lzo and lzma, server side caching homcc, compatil with ccache: cache_prefix=homcc
* drop in replacement (distccmon compatible)
* supported compilers: clang2 + gcc3
* multiple configure build servers
sandboxed execution: docker + Schroot
* cross compilation
* fission: split-dward* why is it more efficient compared to distcc:
Sponsor: Celonis (http://celonis.com/de/legal/)

```

## intro about CElonis
* structured process mining
* process intelligence graph
* process mining engine: in memory OLAP database; for read only, uses PQL (process query language) to power process mining; a cloud based database in a modern SaaS eco system with modern C++ at its core
* teams around this process mining engine: first: find all depedencies of the ; file itself is also a dependency
* alsohas load balancing on he client side
* uses the StateFile
*
  *  PQL: bringing the semantics to life
  * orchestrationsquad
  *altform team: setting


  ## homccc - traffic efficient distributed c/c+ compiler
  * oliver layer, SE
  simon pfirsich, SE
  willi mann, principal software engineer

simon pirsch, not

compiling a c++ codebase on your loal machine can take long
* offload te compilation to remote machines
client uploads the source files, server compiles them and retrun resulted
some dsitributed comilers: distcc, goma, icecc
* what is homcc and why do we need it?
*
* willi now: * why was it trigered: 2019 everthing worked fine, but in 2020 the pandemie spread and the cmpile times went up, because their internet connection ws not good
** before distcc without pump mode, means preprocess on the client
* with pump mode: preprocess on the server: doesnt work wth some boost headers, no caching
* work from home due to covid
* limited uplink bandwith at home (10 Mbps)
* distcc becomes your bottleneck: compilation takes longer than building locally
* main problem: repeated transmission of the same files
* has github repo: work from home friendly distcc replacement
* open source, python 3.9
developed in less than a year
compiler wrapper
* $ homcc --verbose +g++ -std=c++23 main.cpp
* developed for SaolaDB needs, developed for celonis
*  first: find all depedencies of the ; file itself is also a dependency
* this means that each file is transmitted separately, not a list of iles
* challenge: recreate the environment like on the local setup
* recreationof file paths based on client environment
* one folder per ongoing compilation
* cache directory contains cached dependencies, LRU eviction of dependencies
* potential issues: different version (compiler, libraries), debug information, special macros (such as __FILE__)
* * but modern compilers support path rewriting: -ffile-prefix-map={old_path_pattern}={new pattern)
* mainly to faciliate reproducible builds

* learnings: type hints are awesome for python: dict[str, str]
  * earlier error prevention + debugging
  * tooling is crucial: pytest, lyint, mypy, black

