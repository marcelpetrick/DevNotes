# 20231128 Qt World Summit 2023 - Day 1

----------------

kate gregory - am i a good programmer
wants to be a good programmer

people filled with doubt and worry
paying her since 1979 to write code. says nothing about today
not architect, manager, cybersecurity, not a good person or not
but typing code does what you have planned for
pipes don't leak, table sturdy for table
dnd people..lawful good, lawful evil
not about capable or competent
or about great
worst person in the room thinks they are the best person in room
dunning kruger skills
being good causes you to not evaluate well
if you can't tell you are successfully singing a note
but if asked to throw baseball.
misestimates skill by largest round. the worst
if you think you are a 8. then maybe 7,8,9 or 10
for self assessments
people think they are great when they are awful..also awful when they are great
everyone got the same sized humble, but different ones. this is how teams work
in order to learn do something you did not know how to do it
their little faces light up for learning
learn with joy and delight and pride
good tutorial, teacher, framework,..
being uncomfortable does not mean you are learning
learning and growing: the more you learn and know, the more you know you have to learn
is wondering actually enough?
bad programmers exist
just wanting to be good does not make you good
same people will do better in a different job
green bathroom tile not a good metric
not any meaningful way of self evaluation
non metrics: github records, who hired you, time as an independent, 
the mere passage of time does not prove anything, some things can be used as proxies
# how can you know?
a test by three questions: do other people ask your advice, do you enjoy it, have you avoided the most outrageous catastrophes?
outrageous catastrophe for developer:
problem production - no
realizing after months of work that a basic assumption does not hold
creating something unmaintainable so that nobody wants to touch it
failing to consider to test something vital (security, scaling, ..)
others ask you advice; did they apply it?
people follow your twitter or blog, ..
the real key: enjoying it, do you like writing code?
does this person enjoy programming? second part: doing it in their free time? would you even do it when you won the lottery?
* emotions in code?

----------------

data processing
2.8 gbyte/s 160 ms end to end delay
identifying the right partnerships is key
qt quick good to hit the ground running good, also convenient
mix of qt3d and opengl
want to build the future of cardio imaging
direct transfer between the 3 gpu. share textures. get everything really efficiently to screen

----------------

marko mklementti, eficode - dev ops pipeline
strongpoint for ci/cd
streamlining the devops pipeline
    1. agile feedback loops: conways law..complicated architectures for complicated companies: team topologies lead to building services as api: self-organized teams are allowed to release more often
    2. creating new embedded products is not synchronized: software and hardware meet on the same maturity levels. then ship, but sw continues to improve
    3. build automation and traceability: ci is perfect place to collect sbom
    4.
security shift left
5. cognitive load for developers. team topology, platform topology, focus on the core business
6. measuring success
dora devops metrics often fall short
mean time to recover deployment frequency
change failure rate
lead time for a release candidate - else you keep the organization slow
automated test coverage
cost of delay
ratio of modular dependencies

----------------

qt will continue to support strongly cross platform
os versions release and qt timeline for feature freeze have that in mind
qt6 for direct hardware platform support
multimodal user interfaces..multiple users in the same application..speech interfaces.
text to speech api, speech recognition is also researched

qt6 and RHI: efficient integration with openxr
qt quick 3d..create 3d scenes with qml and js
create more in less time!
ready made solutions, from ui to network
high level modules for visualizing data
not want to reinvent the wheel
integration to 3rd party solutions like opencv, tensorflow, authentication frameworks
connected first. gRPC, MQTT, coap, http, qt remote objects, opc UA
cybersecurity..eu resilience act, usa cybersecurity act..for connected devices. guidelines for qt, for things which could be problematic..also for compliance
four eye principle for every commit..at least reviewed by someone else..anybody can contribute, but everything is reviewed..also runs through the CI
also fuzz testing for things which handle untrusted data, hardening those interfaces
if there are CVEs. they will be analyzed, the maintainers are informed, then disclosed
language wise security: cpp committee, make the language more secure and safer to use
language development cpp20 or cpp23, also for rust and python
qt6 as cpp17 requirement
tension between on the edge developers, and regulated areas
questions:
qt qml or widgets? qt quick as first class technology. highly declarative, designer friendly, hardware accelerated. but qt focuses on qt quick.
printing to the qtpdf module?
problem with qt macros and the cpp23 modules
whole rat tail of things to handle for new widgets. cross platform, ...
effective css support in qt widgets
but can be compute heavy. after prototyping review
efficient: implement own style

----------------

change i was afraid of that - kevin henney

even english language changes, just lacks the version number
sandman neil gaiman - brief lives
how do you know time is happening? change
humans are allergic to change, grace hopper
architecture represents the significant design decisions that shape the form and the function of a system - grady booch
a view of the architecture. not the architecture. 
drawing air is architecture. because not a small change
measurements in costs, time and pain
“cpp developers are unique in their tolerance to pain” 🤣
97 things every software architecture should know
simplicity before generality
architecture changes. scales to humans
half life of code quite high. see winxp
code has no decay. does not rot. 
maintenance is fixing wear and tear. not fixing bugs. this has been there always. perform an optimization
look at it from a higher context. do it with focus.
definition of focus. ignore everything else
features are mode of software. software mode of code. so company success is based on code. therefore they should focus else they lose money
managing debt..total control. not intrinsically a problem.
unmanaged debt, that's the problem.
the handling of the debt is the question.
technical neglect
can't point to the absence of change. just pointing to the change is possible
dependency structure for security
## issues:
not refactoring before change. big problem..prepare the space!
not refactoring change.
not testing. avoid breaking peoples assumptions.
not reviewing code.
not recording decisions.
not revisiting decisions.
not updating technology. to draw from a large portion of the population. and chatgpt has been trained up on.

----------------

from code to influence - jonathan courtois
* how to become a leader without becoming a manager
* since 2010 freelance developer, studied many different industry sectors
* tech lead, architect, solver, right hand: see photo
* does the title matter: yes..because it will give you credibility, unlocks you the room, compensation boost, role transition, confer authority, but lasting impact is derived from approach and skill
* strategies for success: operating at the staff level
* learning curve: slow feedback loop, strategic work over instantaneous gratification of coding
* prioritize your impact
* strategy crafting
mentorship and growth, shift focus from proving personal capability to empowering and growing the team
diverse networking: talk to people inside the company learn from the departments
recommendation lead dev.com good starting point. 4. to 5.12..2023.
also two book recommendations
slack channel for free as well
todo check leaddev
check his linkedin
heavy advertisement for sky as company

----------------

mathematical segue
delivering Wayland and Qt
plan is to have 60 fps
wayland quite abstract
mercedes does not produce content
hard to ask netflix to adapt their drm apps to mercedes ui
maximizing the potential of qt by running system ui and compositor in one process
stability risks

----------------

qt academy
before missing bigger picture..18 months
put limited amount of content and made some prototype. would it work? surpassed the expectations. in 4 months results..went all in
badges, can do webinars, also partner content
scythe studio and kdab added content as well
todo: check the qt cmake course 
sponsored learning path?
more pedagogical understanding
also: working with real life examples

why do you see a career in tech worth pursuing.
mathematicians, programmers, coders ctos

the ceo of FYI

if you want to solve problems on the highest level..apply yourself to the language, coding or protocol

dreamers, ideators have the task to do great things


----------------

andreas aal
optimized hardware software co-design

integration of ux into the co-design

digital twins enable vr experience at any project stage

can run algorithms especially for autonomous driving on a design, which is not even produced..arm based, ip protected architecture..
good for measurement of power consumption

----------------

is software making the lives of developers easier?

genai
kevlin: you made yourself a legacy maintainer. because you have not led the development, unknown defects are hidden
not good culture to create good tools for developers
observe how developers use git?
is it designed as a consumable product?

people are doing things they can check..emails, write text, convert code..good use cases because checkable

but what about taking code from stack overflow and then convert into unknown language, no clue how to debug. dangerous

can we check the result..do we have enough time to check the result?

discussion rotated much around the usage of generative ai.

and accountability.
get better by repetition..by understanding. once you have done you can automate the stuff

no generations of who used genAi
you can't engineer yourself out of a cultural problem..volker

the tools facilitate something.
