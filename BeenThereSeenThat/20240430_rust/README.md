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
![](img10.png)

## modules and crates
![](img11.png)
* project management features: structuring your code
* crates as collection of modules
* modules are either physical files or logical Rust constructs
* module with submodule

## embedd unit tests directy into code
![](img12.png)
![](img13.png)
## rust ecosystem
![](img14.png)
* crates in rust are packages or libraries in other languages
* cargo is the single dependency tool: like a swiss army knife
* cargo.toml to add versions, run tests, retrieve crates
* the rust book!
![](img15.png)
![](img16.png)
* rust by example: by doing coding .. less formal as well
* Hightec is an open source compiler provider (have to check what this means)

----------------
```
    Webinar staffto everyone

Q:
    I'm hoping to find out how Rust compares with Python and why I might wish to use Rust over Python
A:
    Python is a much simpler language to learn but it is an interpreted language. Unfortunately since python does not have strong data typing, Python programs don't scale up very well. So if you want quick development and easy you should stick with python. If you want fast/small/safe/scalable you should look at Rust
11:09 AM

Webinar staffto everyone

Q:
    Hi, what about the debugging facilities in Rust ?
A:
    Same as what you have with C/C++, GDB, LLDB, and all the rest.
11:10 AM

Webinar staffto everyone

Q:
    Does GNU-GDB support RUST
A:
    Yes, lldb too
11:11 AM

Webinar staffto everyone

Q:
    Does gnu-gcc provide compiler for RUST What processor/controller toolchain support porting of RUST
A:
    Not at the moment as far as I know. Rustc uses LLVM compiler infrastructure. There are also commercially available compiler tools if you need cerified tools
11:12 AM

Webinar staffto everyone

Q:
    Do we have a size comparision between C program and RUST program
A:
    Generally on par. I have seen that highly optimised C code can be 10% smaller that Rust. But sometimes it is the opposite.
11:13 AM

Webinar staffto everyone

Q:
    in C / C++ better to use the -Wall -Werror to avoid us of unintialised values
A:
    You are right there are a few options you can use with gcc to get you warnings about your code. I'll be honest though, the Rust compiler static analysis and error messages are next level compared to what you get with gcc.
11:15 AM

Webinar staffto everyone

Q:
    I think Python is normally compiled to bytecode?
A:
    Yes python can also be compiled instead of interpreted but in all fairness, Its code size and execution speed is nowhere near what the Rust compiler does. Having said this, sometimes you don't need speed of a small binary. Rust is a systems language so these aspect are super important

Webinar staffto everyone

Q:
    What if a variable is assigned a value in a different process? How does the compiler know if it will be assigned before it is used?
A:
    The rust rules prevent the direct use of a shared variable accross two threads. Having said that, there are mutex based types that would give you this ability.
11:20 AM

Webinar staffto everyone

Q:
    Does Rust also do runtime boundary checks?
A:
    Yes both, compile time and run-time if it can't be detectect at compile time
11:20 AM

Webinar staffto everyone

Q:
    How do usually rust binaries compare to C binaries in size? What is the overhead of some of these abstractions?
A:
    Abstractions are generally free! optimised away by the compiler. rustc uses the same back-end as clang. in general highly optimised C code can get you about 10% smaller image but in a normal setup C and Rust have a similar image size. The key difference between C and Rust compilations at the moment is compile time. Rust takes longer because of its sophisticated static analysis
11:24 AM

Webinar staffto everyone

Q:
    What type does that vector have?
A:
    a vector is basically an array of values that reside inside the heap
11:24 AM

Webinar staffto everyone

Q:
    basically an array is static but a vector is dynamic ?
A:
    You can say that yes
11:25 AM

Webinar staffto everyone

Q:
    How does Rust help achieving ISO 26262 certification compared to qualified C/C++ toolchain? Is there already MISRA like guidelines for Rust which could ease getting certification?
A:
    Intersting question. Our partner for this video https://hightec-rt.com/en/rust provide a commercial solution for ISO 26262 / ASILD compliance
11:26 AM

Webinar staffto everyone

Q:
    so the run time range checking must come with a performance hit compared to c. Right?
A:
    Fair point, run time assertions will have this effect indeed.
11:27 AM

Webinar staffto everyone

Q:
    Dynamic flagging of error, does it mean every RUST executable has this debug information as part of executable file?
A:
    Rust executables can be generated in Debug and Release. In Debug you will get run-time assertions and debug symbols. In release you have far less available

    Webinar staffto everyone

Q:
    What is that environment you use on the slides. Where you can change values and the code and it shows immeditealy the result. Compiler explorer like godbolt für c++? Thank you in advance
A:
    Well spotted! it is indeed compiler explorer https://godbolt.org/ Do you like this type of IFRAME based slides?
11:35 AM

Webinar staffto everyone

Q:
    Returning a string is good for humans but less good for handling in calling code
A:
    Fair point
11:35 AM

Webinar staffto everyone

Q:
    What if there's no enough heap memory for vec!? Will the program panic in runtime?
A:
    Yes this error will typically come from your OS when it fails to allocate a page of memory with its MMU. But yes you will get a runtime assertion in this case
11:37 AM

Webinar staffto everyone

Q:
    Is gprof can be used to track overhead in Rust, or any other tools to get memory use analysis over time ?
A:
    Any tool that you normally use for gcc/clang generated objects/images can be used with rust. I haven't actually used gprof but I have used the typical gnu binutils without any differences
11:39 AM

Webinar staffto everyone

Q:
    Is something like MISRA even necessary for Rust?
A:
    Rust static analysis and owneship model does get rid a lot of MISRA requirements. Having said that, MISRA isn't totally redundant
11:41 AM

Webinar staffto everyone

Q:
    is having one owner per heap allocated variable means you need to make copies across application to retain a value ?
A:
    Well spotted! it's nice to see that you are already thinking about memory management costs. In Rust we can use something called references (a bit like shared pointers and unique pointers in C++) that solves this problem
11:43 AM

Webinar staffto everyone

Q:
    Are there any tools to help convert from, say Python, to Rust code?
A:
    Have a look at those two tools cbindgen and bindgen. They are designed specifically to facilitate the automated creation of Foreign Function Interfaces.
11:44 AM

Webinar staffto everyone

Q:
    Is the runtime check similar to the sanitizer features in C/C++ compilers?
A:
    Yes a lot of those static and run-time checks are similar to what you can find in eseparate C/C++ tools. The nice thing about Rust is that, this is all there by default no need to hunt arround for the right tool to check specific things. (maybe not for performance profiling though)

    Webinar staffto everyone

Q:
    why is law_maker moved rather than just copy? IT was assigned to new_law_maker but was not itself modified
A:
    Sorry I am a bit behind the slides... If my memory serves my right law_maker is not a copy type! (two types families in rust : copy, non copy) the complex types are non-copy types so when you assign variables of non-copy types, the ownership of that memory location is moved! very different from other programming laanguages.
11:50 AM

Webinar staffto everyone

Q:
    C/C++ has a lot undefined behavior. I have encountered this many times e.g. in situation where everything works in debug build but optimized build behaves differently. Does Rust guarantee it works same way in unoptimized and optimized build?
A:
    I know what you are talking about with C and optimisations. I can affirm that Rust is always better than C in that respect because they are too many variaitons. For instance in rust debug if you overflow a value, you will get a runtime assertion but the release version of the code will do a wrap arround. There are simple ways to get the same behaviour in both cases but this possibility exist. Also you have all sorts of additional concideration with things like volatile values, synchronisation and the likes.
11:54 AM

Webinar staffto everyone

Q:
    What online compiler did you use in this webinar ?
A:
    Do you like it? it is: https://godbolt.org/ but you can also try: https://www.rustexplorer.com/b or https://play.rust-lang.org/?version=stable&mode=debug&edition=2021 all are great tools to get started with rust!
11:56 AM

Webinar staffto everyone

Q:
    The godbolt iframes are pretty cool!
A:
    I love it! we use it a lot in our training classes
11:57 AM

Webinar staffto everyone

Q:
    what happens if the s: string in the take_ownership function has the same name as the passed variable. I mean instead of s the name was law_maker
A:
    Ouch sorry Mehdi I will have to run the code to try thing out. Name have a scope though so if you have a variable inside a function with the same name of a variable in the outer scope, they don't conflict. (not the same for global constants...
11:59 AM

Webinar staffto everyone

Q:
    First // Reading photocopy1 is wrong? Reading law_maker?
A:
    Thanks for the tip Mark. I'll double check
12:00 PM

Webinar staffto everyone

Q:
    is Rust recommended for microcontroller and RTOS based embedded systems programming ?
A:
    Rust works very well in the embedded world even on tiny MCUs like a Cortex-M0. There are a lot of project templates on crates.io to get you started with an MCU project of your choice.
12:01 PM

Webinar staffto everyone

Q:
    How/do the panics works with microcontroller without (RT)OS? Or in this case rust have less functionality than rust for pc programms ?
A:
    In an embedded scenario, you have to specify to the compiler how to handle a panic. like, halt the code's execution (BKPT), run an infinite loop, generate a semi-hosted message and anything else you may think of
12:03 PM

Webinar staffto everyone

Q:
    Isn't borrowing in that case increasing the memory consumption specially for embedded devices such as microcontrollers ? what will happen to the first instance of the variable ?
A:
    Borrowing only creates a pointer to the original value in memory. that handle is destroyed automatically when it gets out of scope. So strictly speaking I would say no.
12:05 PM

Webinar staffto everyone

Q:
    Can Rust call into modules written in 'more risky' languages e.g. C libraries?
A:
    Yes it's very easy. You will have to declare an unsafe{} block to do so but besides this Rust has a well defined Foreigh Function Interface and providing that your targetted language supports a C ABI, you are in business!
12:06 PM

Webinar staffto everyone

Q:
    Are there experiences with build time of Rust projects that are comparable to C or C++ projects?
A:
    There are a few conference papers on this. In general very optimised C gives you about 10% smaller images but that about it
12:08 PM

Webinar staffto everyone

Q:
    so perhaps module resembles to module in an HDL?
A:
    Somewhat similar to what you have in VHDL yes
12:09 PM

Webinar staffto everyone

Q:
    I guess (hopefully possible) we can mix C / C++ with Rust code used in a library ?
A:
    Yes it works very well. Rust has a well defined FFI and automated tools like bindgen and cbindgen to help you too
12:10 PM

Webinar staffto everyone

Q:
    Isn't outer_module private?
A:
    The very top module is public by default
12:10 PM

Webinar staffto everyone

Q:
    Is a file a module by default ?
A:
    yes files and physical modules
12:10 PM

Webinar staffto everyone

Q:
    is embedding unit tests would be part of the compiled code ?
A:
    No it is removed at compilation

```

----------------

todo
* add the images
* fix the text
