# Qt Embedded Days (13th and 14th of April 2021)

## Day 1 (20210413)

###  “Hands-On: The easiest way to set up a development environment and build a modern UI for Raspberry Pi” by Filippo Scognamio, FELGO 
[partially missed, because of parallel meeting]
* FELGO cloud builds? for deployment
* FELGO Live Client for the machines; deployment saves 10-20 hours per developer month
![](img00.png)
#### FELGO SDK
* provides functionality on top of Qt
![](img01.png)
* plugins for monetization, analytics, engagement, cloud
* example
![](img02.png)
* currently just Qt5; Qt6-transfer is in progress, but since Qt6 has some missing components, this is an ongoing task ..

### “Demystifying C++ for C embedded developers” by Giuseppe D’Angelo, KDAB
![](img03.png)
* quite easy-going approach: instead of fully diving into C++ immediately, just use it as "C with classes" first, maybe. Much advantage: inheritance, destructors, ..
* in C++ you don't pay for what you don't use
* also disable stuff you don't use, like RTTI (dynamic_cast), exceptions, ..: -fno-rtti; or -fno-exceptions
* shrink code-size
![](img04.png)
* maybe limit usage of templates: to fight code-bloat
* C99 can be ugly (name-clash), C11 has generics, but super awkward!
![](img05.png)
![](img06.png)
* auto-destruction on leaving a scope .. prevents resource-leaking
![](img07.png)
* "the ability to define destructors is one of the most important features of C++"
* several return-paths inside a function are allowed and possible without any resource-leakage
* manage failures also by exceptions (but this would more bytes to the code; around 100 byte for one function, i386 - opt-in or opt-out, if affordable)
![](img08.png)
* type-system: casting is given to make the human aware of what it does; the compiler would not need it .. C assumes stuff (and  let's things explode; C++ requests affirmation)
* helpers for comfort .. grouped digits, ranges
![](img09.png)
* conclusion
![](img10.png)
* C will prevail due to the interoperability .. there is for almost all languages an API to interace with C

### “Containerize your Qt embedded application” by Valter Minute, Toradex
* containers are not virtual machines
[not much time to listen..]

![](img11.png)
![](img12.png)
![](img13.png)

!![TODO] check this talk later, because it is also about the containerization of Qt5

### “What to Do When It Is Already Too Late? – Crash Dumps in Embedded Projects.” by Christoph Sterz, KDAB
!![TODO] check this talk later

![](img14.png)
![](img15.png)

### “Maps, Routing and Navigation with QML” by Justin Marina, General Magic
* checked, but unless I want to do an (embedded) app with some kind of routing or geo-information not really necessary for me

--------------

## Day 2 (20210414)

### “How to Set Up QtCreator for Cross-Compilation with CMake in 5 Minutes” by Burkhard Stubert
[todo]

### “Designing UI’s for Embedded Devices, in 3.5 “simple” steps.” by Nuno Pinheiro, KDAB
* an application style guide can be helpful to set boundaries
* prototyping

### “Dealing with physical units in modern C++” by Nikola Jelić, Zühlke
* embedded devices interact with the real world and either receive or emit data with physical units 
![](img16.png)

### “Get inspired by web development – A story based on the example of the Flux pattern” by Marius Meisenzahl, Semasquare GmbH
[todo]

### “Creating Automated GUI Tests for Embedded Applications” by Tomasz Pawlowski, froglogic
![](img17.png)
* froglogic established 2003, owned since yesterday by Qt company
* widely used
![](img18.png)
* squish can be crosscompiled for other platforms: like on Linux for ARM-platforms
* Qt-widgets, QML and also QtQuickControls: also Qt-webengine-stuff
* access to signals and all controls
* app not started, but just attached to already running application* talk via tcp/ip, also internal squish protocol
![](img19.png)
![](img20.png)
* third way: builtin hook
![](img21.png)
* Squish takes 'only' 120 MB for an iMX6 (with just 8 GB storage)
* Recording: record user interactions with AUT(?)
* or: manual scripting
* or hybrid approach

* scripting tests or BDD-approach 
* for this presentation just simple scripting

### “Simulator Training for Hardware Pilots – Case Study: simulating CAN-Bus attached hardware” by Alexander Trica, DATA MODUL & Kevin Krammer, KDAB
![](img22.png)
![](img23.png)
![](img24.png)
![](img25.png)
![](img26.png)
![](img27.png)
![](img28.png)
![](img29.png)
![](img30.png)

### “What reliability means to you?” Sami Kassimäki, Tuxera
![](img31.png)
