# 20230221 celonis - breaking dependencies in cpp - klaus igelberger
* celonis, 11b 2021, more than 2k employees, 
* no entreprise eady tooling, academic tools wwere not scalable (?), BI tools were missing required features? what do they do t all?
* db is optimized for process mining use-case .., dashboards and monitoring tools
* saas provider, runs the software on their own platform

# breaking dependencies: the path to high-quality software
* trainer, consultant, author of the blaze cpp math library, co-organizer of the munich c++ user group, chair of the cppcon back-to-basics-track
* klaus.igelberger@gmx.de

### what is high quality software?
* his definition is easy to change, easy to extend, and easy to test (and of course also fast)
* the truth in the industry: software must be adaptable to frequent changes (soft-ware as in soft: it can be canged)
* what is the core problem of adaptable sw?
  * dependencies ..
  * other common thing is: software design
* `software design is the art of managing interdepdendencies between softwae components. it aims at minimizing (technical) dependencies and introduces the necessary abstractions and compromises` (his own definition from his book)
* sw design is the art of managing abstractions
  * this is not entirely new!


#### example: fictuous project, completely new
* new project, nothing existing, really high development speed (100%), no hindrances, no obstacles
* so management makes promises to the customers
* quality of code starts to degrade; things are getting more difficult to change, new features become more difficult to add, less time is left to care about the code
* quality drops further, people get frustrated, more time is wasted in debugging, even less time is left to careabout the code
* more developers are hired: the new developers need to be trained, less time for the old developers (more frustration)
* frustration is high, key developers leave the team/company ..


* quality matters!
* small things are more beautiful than big things
* but the structure/organization of the code (the design) matters even more
* robert nystrom: `they were so ocussed on features, that organizatio went overlooked` - came from gmee design
* then ´: of course: rewrite the code!

* joel spolsky: `they made the single worst strategic mistake that any software company can make: they decided to rewrite the code from scratch` (see Netscape..)

* keep your code easy to change, easy to extre´´end and easy to test (loved by managers)
* how to do this?
  * the solution: design patterns
  * dinosaur-book, gang of four, from 1994, 23 most commonly used pdesign patterns
  * gave them a name, their intent and how they help to manage dependencies
  * `design patterns are everwhere`Klaus Igelberger
  * there ae not enough talks (like at the cppcon) about sw design, more than an order more about features
  * reasons1: we know already everything about design patterns
  * reason 2: no one does OOP anymore ..
    * why is this wrong? example: factory-method (class defer instantiation to subclasses) (from the book, GoF
	* add here the factory method example, but this is commony wrong
	* another example: strategy design pattern: the design pattern is above the line, above the architectural boundary (would need a photo now..)
	* the command design pattern: again above the "line"; in the schedule-method
	* the factory method desin pattern: again separation of concers, function pointer, see the Generator
      * difference between factory function and factory method; f-method is customizable factory function
  * but we do not know now everything about design patterns
  * about the second thing: design patterns are for OOP, but we do not do this so much any more .. naja
* examples from the standard libray:
  * std::unique_ptr: has a strategy, the deleter; the cleanup behaviour can be substituted
  * vector uses a strategy: which allocator to use; this can be injected from the outside
  * std:Set uses three: hash, keyequal, allocator - you can define how those things work
  * std::accumulate: fourth parameter defines how the elements are combined: add, multiply?
  * strategies are the most common designpattern in the std-lib! (more than 200..)
  * let's talk about the most controversial pattern: the singleton: only one instance and single point of access
    * common form is the Meyer's Singleton: implemented with static keyword .. is then destroyed at the exit function
	* but most developers are not fond of this pattern: but there is trouble, if you make anything particularly accessible from any part of your program, because they represent a _gloabl_ state!
	  * bad, because: they represent a mutable state; read&write operations are difficult to control, especiylly in a multi threaded environment, hard to reason about, and also the Static Initialization ORder Fiasko (SIOF)
	  * so the comon advice is: don't use singletons
	  * but some things are inrinsically gloabl like te logger; system-wide donfituartion, or audio and display device, time, memory..
	  * but: singletons create dependencies! serious dependencies on concrete implementation details, so if you change something, everything has to recompiled ..
	  * bad dependencies that make change and extension more difficult
	  * they make it difficult to extend, change and test
	  * high level in architecture are things which are stable (like datbase), frequently changing things are low-level; std-lib is high level
	  * is a database at the same level as the STL? no, this is not at the sam level; database is a low level detail!
	  * singletons destroy architectures!
	  * std::pmr:null_memory_ressource - does not give something back 
	  * note: immediately invoked lamdba expression (IILE, from the std-lib) - withh (); at the end of the lamdba
	  * dependency inversion (for instance via the strategy design pattern) is the necessaey first step to an "acceptable" singleton
	    * a testable singleton isounds acceptable ..
		* is this now the invetion of a new design pattern? no, this is the service locator-design pattern

### summary
* sw design is not an afterthought, but esential for the success of a project
* let's stop pretending that c++ is all about feature and standards
* let's start to talk about the structure of code..
