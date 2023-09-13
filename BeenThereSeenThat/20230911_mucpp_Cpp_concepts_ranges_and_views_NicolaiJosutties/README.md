# 20230911 C++ Concepts, Ranges and Views - Pretty cool; but no, what’s that?

```
On September, 11th, for the fourth time, we have the great pleasure to welcome Nicolai Josuttis to our user group. Nico (http://www.josuttis.com) is an independent system architect, technical manager, author, and consultant. He designs mid-sized and large software systems for the telecommunications, traffic, finance, and manufacturing industries. He is well known in the programming community because he not only speaks and writes with authority, but is also an innovative presenter, having talked at various conferences and events. He is the (co-)author of the world-wide best sellers

    The C++ Standard Library (www.cppstdlib.com),
    C++ Templates (www.tmplbook.com),
    C++17 - The Complete Guide (www.cppstd17.com)), and
    C++20 - The Complete Guide (www.cppstd20.com).
```

```
Agenda:
18:00: Open doors und get together with catering
19:00: Lightning talk by Daniel Eiband
19:15: Main talk by Nicolai Josuttis
~20:30: Get together and open discussions
22:00: Official end
Sponsor: Brainlab (brainlab.com)
```

## no match for sync_wait(talk_title())
* Daniel Eiband, snke os, working since 2007 for Brainlab/snke os
* * P2300 std::exectuion, ex:sync_wait)talk_title())
* what are snders: lazy and asynchronous programming model
* sender consumer <-< sender factory
* async. and lazy
* GCC 11.3
* segmentation and registration of medical images
* develop sfotware in a way to maximize utilization of the hardware
  * thread pools?
  * accelerators?
  * clusters?
* why cpp? beause fast, but think twice in a cloud environment
* also: coroutines
```
auto talk_title()
{
  // see more in img00.png
}
```
* why not use a statemachine instead of functional composition?  unclear
* also maybe just the builder pattern

* completion signatures: why not error messages at compile time?
  * PR2300R7 only supports a query, but most of the senders know their signatures beforehand

## Main talk - concepts, ranges and views
* add a constraint to allow template overloading: img01.png
* constraints with concepts: overload resolution prefers more specialized function
* spelling error leads to: not accepted constraints
* now you need test-code for concepts:
  * static_assert(HasPushback<std::vector<int>>); //.. and so on.
* now use auto to hide the template: much simpler
![](img02)
* use std:: decay: strip cv-references; ref ..
* how to concept a container which is a sequence container?
  * add a list of requirements: how to define proper functions?
* concepts cost compile-time
* requires expression can use the requires clause
* simplicity is so much key
* if constexp (requires { coll.push_back(val); }) {
  coll.push_back(val):
  }
  else
  {
    coll.insert(val)
  }
* "in C++ once you understand the error-message, you understand the error"
* live example in godbolt.org
* comparison of gcc (bad), clang (short and readable), msvc19 (quite good)

### Ranges
* so requirements can't be added to existing algorithms, therefore std::Sort gets superseded now by std::ranges::sort(..)
* stdd:ranges::sort(coll1);
* ten ways to call sort (various ways to call algorithms)
* but there is a problem, because there is no policy to clean up c++ --> namespace mess

#### Views
*  const auto& should be replaced with auto&& (forwarding auto)
* using a filterview can create a problem, because begin() is cached: which leads to unexpected behaviour: cpp-committee declared this also as undefined behaviour if the resulting value does not satisfy the filter predicate -> "explicite statement"
  * std-lib: fucks the stuff up
 ```
 for (auto& m: monsters | std::views::filter(isDead)) {
  m.ressurrect(); //undefined behavior: because no longer dead
}
  ```
* when an expert group discusses something for three years, then they think everything is fine. Because they know the rules. But not everyone knows the rules.
img04

* zip_view: a pair of elements: should be combined ... const has no meaning, because it does not propagate
* most containers are broken by views

* recommendation: don't use the views-library, because it is broken by design
* except when you never modify something, then multiple use of views is not useful, but broken
