# 20240126 C++ Patterns for Non-Safety-Critical Automotive Software Development

```
Details

On January 26th we have the pleasure to welcome Antons Jelkins to our user group. Antons has been using C++ professionally since 2009. He joined BMW Car IT GmbH as a C++ developer in 2013 and, with interruptions, stays there up to this day. After some years in the company he became responsible for several overarching topics in a major navigation component, such as a build system, an application lifecycle, communication and framework. He later used this experience to help design and implement other applications to run inside cars. Antons truly believes that it is important to have common abstractions, conventions and techniques, that it is in company's best interests to solve a problem really well once and then adopt the solution. With these ideas in mind, Antons co-started a C++ application framework project which now gets adopted by ever increasing number of non-safety-critical applications within BMW.

***
Abstract
In this talk I would like to share how we use C++ to develop non-safety-critical software which runs inside BMW cars, and how a C++ application framework helps us with this. I would like to provide an overview of how a generic C++ application looks like: what techniques, building blocks and patterns does it use etc.

***
Live Stream: No live stream this time.

***
Schedule
18:00 -- Welcome with Snacks and Drinks
19:00 -- Welcome at BMW
19:10 -- Main talk by Antons Jelkins
~20:30 -- Open Discussions
22:00 -- Official End
```

## Organic Computing - Luis Hohman
* The future of embedded systems
* Motivation: Increasing complexity, Moore's Law - integrated circuits increase by a factor of 2 every 2 years
* TODO: Image of him speaking
* Engineering embedded systems in ways observed in nature: self-organization
* Example: Ant colony - self-configuration, self-optimization, self-healing, self-protection -- self-X properties
* Organic computing as systems science, paradigm shift
* "Move design time decision to run time"
* Artificial hormone system, circulatory system; core C1 - C2 - C3
* If core C3 crashes, Task4 can't be finished: artificial hormones

## C++ Patterns for Non-Safety Critical Systems - Antons Jelkins
* 2024 work on remote software update
* Principal engineer - Staff software engineer for bigger IT-tech companies
* What is automotive software: Low-level, safety-critical (instrument clusters, autonomous driving stack), MISRA, AUTOSAR
* Cars are complex, dynamic, heavily asynchronous, and interconnected software systems
* Cars are in constant communication with the cloud
* The nature of these interactions is highly asynchronous
+ Cars consist of many interconnected ECUs (Electronic Control Units)
* Many ECUs run Linux
* Interconnected applications:
  * Each ECU runs multiple applications
  * They interact with other applications
  * On the same ECU, on other ECUs, off-board services
* Separation into two major classes: safety-critical and non-safety-critical
* Can harm people and property, and has much stricter, C++11 or maybe 14, quite limited, no dynamic memory allocation
* Non-safety-critical: C++17 or 20, mostly IO-bound, implements some BMW-specific business logic
  * Most of the time, waits until something happens
  * Examples: Infotainment, navigation, speech, augmented reality, time, temperature, light, system infrastructure, software update

### BMW's C++ Application Framework
* Common problems:
    * Doing asynchronous software right is hard
    * No industry standard to do it
    * Risk that teams would reinvent the wheel
    * People onboarding and communication; each team an isolated island, because they can't communicate
* It's in everyone's best interest to solve a problem really well once and then adopt the solution
* This helps teams to focus on business logic
* Common instructions, shows how (TODO: Add from photo)
* Design goals: Car's software is still embedded software, can't deploy a quick fix to production. Costs of software errors are high. This affects design decisions
* No scaling vertically or horizontally: prioritize robustness, easy-to-use APIs, hard to misuse APIs; make it harder to make a mistake; mitigate asynchronous programming difficulties
* Framework consists of two distinct parts
* Business-agnostic code
* Built on top of the standard C++ to support our needs
* And also business-specific code: specific BMW behavior
* Execution flow: Applications are primarily single-threaded, yet asynchronous; if necessary, use worker threads
* Asynchrony via event loops and concept of executors
* Each thread runs a specialized version of event loop: executable tasks
* Anyone can enqueue thread-safely a task
* Tasks run in sequence
* No mutexes, no synchronization needed
* Threads do not communicate directly
* Executors represent an event loop of a specific thread: threadsafe way to post tasks to be executed
* Managing object lifetimes is hard, especially with async systems
* An execution context defines the lifetime of asynchronous entities, such as callables and future continuations
* A context binds callables (such as lambdas) to an object's lifetime. When the context is destroyed, the bound callable becomes a no-op, preventing it from running against an object whose lifetime has ended
* A naive approach to asynchronous programming is to use callbacks; nested callbacks can make control flow and error handling difficult to follow
* VIN stands for Vehicle Identification Number: the identifier of an individual vehicle. The extra word "number" in "VIN number" is redundant

### Follow-up clarification: futures and promises

Added while addressing [the presenter's feedback in issue #2](https://github.com/marcelpetrick/DevNotes/issues/2).

* A promise is the producer's handle for completing an asynchronous result with either a value or an exception
* A future is the consumer's handle for accessing that result through the shared state associated with the promise
* With standard C++ futures, `get()` waits if the result is not ready, then retrieves the value or rethrows the stored exception. Waiting on an event-loop thread can prevent it from processing other work
* Frameworks that support future continuations can schedule follow-up work when a result becomes ready, rather than blocking the event loop. Standard `std::future` does not provide a `.then()` continuation API
* Future continuations, like other callables, need lifetime management: the execution context determines their lifetime, including when the object they would access is destroyed

References: C++ working draft sections on [promises](https://eel.is/c++draft/futures.promise) and [futures](https://eel.is/c++draft/futures.unique.future).
