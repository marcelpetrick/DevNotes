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
* 
