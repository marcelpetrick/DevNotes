# 20240430 - Doulos: the rust journey

## agenda
introduction to rust
safety feature of rust language
mmemory mangen in rust
* the rust ecosystem


* is a modern systems programming language
* focus on safety, speed and cncurrency
* created by Mozilla: in 2015
* is an open source language
* compiled language just liek c/c++, Ada, ..
  * type rich with strong static checks (at compile time)
* spend a lot of time to getting your pgoram to compile
* once it runs, you hve a cast iron guaranteee it is memeory safe
* no runtime or garbage collection
  * with performance and memeory safety guarantees
* enforcing some tight rules enforced by the compiler
* C is over 50 years old and has hardly changed since its creation date
* Rust is a modern language with all the niceties that come with it
* evoluation not revolution
![](img01.png)
* versatile and efficient generics: similar to the type classes in C++
* compiler optimise away the generics inside the object file
* algebraic datatypes
* enums (Option <T>), structures, tuples
* type inference - leave it up to the compiler to work out the type based on the context
* really nice pattern matching
![](img02.png)
* intrinsic memeory safety: static code analysis
* variables mus t have a value before we can use them
* initial example won't work, compiler prevents you and tells you what to do
* checks are done during compiel time or run-time, if necessary
 * runtime-access of index 3 with array with three elements results in a `panic`
 * array fixed; vector can grow and shrink during runtime
* varibles immmutabe by default
![](img03.png)
* intrinsic safety: default immutability
* use the keyword m̀ut`to make them mutable
* immmutability is propagated thought the code's hierarchy
![](img04.png)
* there are no NULL pointers in Rust: any references are guaranteed to be non Null
* no hidden states
* fine grained memory control: heap versus stack
* variables have an intrinsic memory location
![](img05.png)
* in system languges you want to control where to put the memory: heap or stack
* Box-type allows to create heap.-allocationed ressources, like malloc or new in C/C++
* fine grained memory control: custom allocators
![](img06.png)
* when the variable gets out of scope, the allocated variable gets reclaimed
* there is a standard memory allocator, which is efficient for large machines
* but what if you want to run it on a small micro controller?
* lol: the resut's club rules:
![](img07.png)
* you have to follow the rules else it won't compile
* each value in memory has an ownner
* only one owner
* the value gets dropped if it's owner goes out of scope
![](img08.png)
* non trivially copiabe types are moved
* their origininal owner remains on the stack un-initialized
![](img09.png)
* ownership is transferred through argument passing
* pragmatic solutions are availalbe (cloning, shadowing)
* intrinsic safety: borrowing
*

----



* today i cleaned up my skills section
* cancelled my github sponsorshio
* 1 year of chatgpt personal assisstant; ad free
* guy anderson talk
* summary of learnings for April
*

* fetch package dhl
* send the other stuff back
* fetch odo
* buy beard bands
*

-------------




![](img02.png)
