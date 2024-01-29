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
## organi computing - luis hohman
* the futre of embedded systems ..
* motivation: increasing complexty, Moore's law .. integrated circruits increase b factor of 2 every 2 years
* todo img of him speaking
* engineering embedded systems on ways observed in nature: self-oranization
* example: ant colony: self-cnfiguration, self-optimization, self-healing, self-protection -- self-X properties
* organic computing as systems science, paradigm shift
* "move design time decision tun run time"
* arfificatl hormone ytem circulatory system; core c1 -c2 - c3
* if core c3 crashes, task4 cnat be finished: artificial hormones

## c++ patterns for non saftey ... - antons jelkins
* 2024 work on remote software update
* principal engineer - staff sofware engineer for bigger it-tech companies
* what is automotive software: low lvel, safety critical (intrumetn clusters, autonomous driving stack), misra, Autosar
* cars are complex dynamic, hevily asnchronous and nterconnected osftware systems
* cares are in a constant communication with the cloud
* the nature of these interactions is highly asynchronous
+ cars constif of many interconnected ECUs (electronic control untis)
* many ecus run Linux
* interconnected applications:
  * each ECUs runs multiple applications
 * tey interact withother applcaitions
 * on the same ECU, on other ECUs, ofboard services
* separation into two major classes split: safety critical and non safety critical
* can harm people and prpoerty, and has much stricter, c++11 or maybe 144, uite limited, no dynamic memory allocation
* non saftey critcal: c++17 or 20, mostly iobound, implements some bmw specific busines logic
  * most of the time, waits until something happens
  * examples: infotainment, navigation, speech, augmented reality, time temperature, light, system infrastruture, software update

### their c++ application framework
* common problems:
    * doing asynchronous software righ is hard
    * no industry standard to do it
    * risk that teams would reinvent the wheel
    * people onboarding and communicarion; each team an isolated island, because they can't communicate
* its in everyone best interest to solve a prolblem really well once and then adopt the solution
* this helps team to focus on business logic
* common instructions, shes how (todo add from photo)
* design goals: car's software is still embedded software, cant deploy a quick fix to production. costs of software errors are high. this affects design decisions
* no scaling vertically or horizontally: prioritize, robustness, easy to use APIs, hard to misuse APIs; make it harder to make a mistake; mitigate asynchronous programming difficulties
* framework consits of two distinct parts
*business agnostic code
* built on top of the standrd c++ to support our needs
and also business specific code: specific bmw behaviour
* execution flow: applications are primiayl single threaded, yet asynchronous; if necessary use worker threads
* asyncrhony via event loops and concept of executors
* each thread runs a specialized version of event loop: executable tasks
* anyone can enque thread-safely a task
* tasks run in sequentce
* not mutexes, no synchroisation needed
* threads do nt comunicate directly
* executores represent an event loop of a specific thread: treadsafe way to post taks to be exected
* managing oject lifetimes is hard: especially with async systems
* execution context similar to lifetime of various entry
* context binds callables (lambda) to the object; the lambda becomes a no-op; ths prevents problems
* naive approach fr callbacks: to use callbacks
* vin number: some car identificiation
