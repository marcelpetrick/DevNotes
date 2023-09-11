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
* also maybe just te builder pattern

* completion signatures: why not eror messages at compile time?
  * PR2300R7 only supports a query, but most of the senders know their signatures beforehand

## Main talk - concepts, ranges and views
*
