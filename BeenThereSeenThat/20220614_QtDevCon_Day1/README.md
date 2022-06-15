# 20220614 Qt Dev Con - day 1

## Qt 6.3 and beyond? - Maurice Kalinowski
* overview on Qt with web assembly
* qt quick compiler ist becoming better in terms of performance
* Qt Speech (text to speech)
* physics/collision
* Multimedia: 3d audio possible again; before problem with codecs
* http server: new in qt 5.12; big feedback; small thin layer as plan; but qt did not know what to do with that?
* qt location: was gone in Qt6, but how to bring it back? in the way of Qt5 or reduced to the basic parts?
* qt vnc (?)
* debian: Qt6 is now inside debian 11, therefore also in ubuntu..; libqt6
* android mobile

* he says "cute" for Qt; 8-10 yers availability for Qt6

* Strengthen embedded, connected first, accelerate design/develop/test, adaptation to new android versions and features faster
* qt language server support (for qt creator): 
* how to make it easier to connect to webservers? REST current, GraphQL (?), protobuf support is coming in Qt6
* Qt learning portal will be imoroved
* conan and vcpackage as package manager: conan has now qt-packages

### questions:
* qt api is stuck in cpp11? qt5 with cpp98 in mind, qt6 with 11: problem with existing projects which can't upgrade the compilers
* analysis what to do with cpp20 is underway: blogpost coming

--------

## the jouney to the cloud has to go through the edge - Dario Freddi
* 5 stages of grief: denial, anger, bargainin, deperession, acceptance
* technology is nothing, but a mean to enable a use case
* technology is something which should not get in the way to do something
* techn. and customer demand evolve fast than ever; turns out the learning curve is still there
* framework dev versus application developers
* demand for technology is increasing
* **Done is better than perfect!**
* technology providers should thrive to provide easier and faster frameworks in an everchanging deployment scenario
* embedded devices span nowadays the whole span from "quickly moving companies" to "companies which still try to figure out what the cloud does"
* data privacy and ownership is growing
* what is the edge? anything which has a cpu inside: mcu to some im6-board
* ompany: SECO; handles the whole chain from data ollection, hardware, cloud solution: due t the fragmentend market no two customers want the same thing
* key take-aways: the secete sauce
  * acquiring assets and know-how vs. building them in house
  * staying ahead of the curve while still ensuring commodity market can be served
  * focus on technology but lead and assit customers in their evolution
* keeping up with ten years of advance when the next big thing is 6 month away is quite hard
* gitlab as example for great product (open source company) of the last ten years; codebase was crap, but it got fixed over time - te product matters
*the tricky bit in the one size fits all:
  * lock-in is a major issue
  * tradeoff betweend speed and ctrol canges over time
* why open source matters:
  *  when you control data, you control the usage of your product
  * giving the users back their data is one of the best reward concepts for users (and for keeping them)
  * trusting a single provider isn't easy, open source helps
* kubernetes as successful choice for them; because it helps to avoid specific providers
* Qt is still the go-to choice for embedded evelopment
* containers haen't killed Qt, android has not, html5 has not
* customers still focus on Qt being Open
* how does technology play a role
  * non-tech companies are getting increasedly exosed to technology
  * learning curve matters
  * keeping it simple doesn't mean you shouldn#t keep it technical: simplyfying does not mean to strip out all details
* the gap between "framework develoopers" and "application developers" will further extend

--------

## Proteins, microscopes and Qt - How modern Biotech fights Cancer - Anne Ruess

### use cases
* MICS technology - MACSima Imaging cyclic staining
* hundreds of markers are acquired and what now?
* MACS iQ View: image analysis software, gives meaning to the MICS data
* segmentation; Gating: breast cancer; distance maps
* data workflow editor for analyzing data

### Lab Automation System
* automated whole blood HT platform
* analyse SARS-CoV-2-samples
* CD8/CD4-T-cells can be detected quite a while, even if the antiboies decrease
* lab automation system: liquid handling robot, automated incubator, centrifuge, ..
### Tyto cell sorter
* gentle to cells, full sterility, full safety, fast&easy
* detecting cells by laser; sorting cells based on positive/negative: little valve opens and closes then
* 20k cells per second
### Prodigy - current blockbuster
* used for some blood cancer treatment
* use of certified version of Qt: no version like this; one of te components in the project; pre-qualification and preparation for processes and helped by their supporting company
* how are the interfaces for data exchange set up? Who is defining the API? 
  * checks for the tech lead) James Turner
  * data manipulation on the device and also on the laptop; overall user-experience is distributed
  * Python automation, API and format is fluent; scientists write their own converters

--------

## Keeping Qt based embedded devices up to date - Stefan Eichenberger

* business case: how to update the whole software landscape of embedded devices
* embear: software made in Bern - one man company; before working for Toradex
* not just for Torizon
* why updates? fix bugs in the field; if customer unhappy, then you will lose him; security threats (third party component)
* secure is not safe; fail-safe is not secure; powerloss is a problem; secure means only signed versions
* also lock the device against threats, not just use a secure update
* technologies: packagaging; partition swapping; OS-tree (new technology); also container-based approach (just like packaging again)
* explanation of his naming convention; failsafe+recoverable, double recoverable

### packages
* deb/rpm/ark
* desktop applications
* service technicians: if something failes, then technician has to be sent to recover; therefore manual recover is necessary
* application updates
* see: github.com/goreleaser/nfpm: does the packaging, uses yaml, several targets

### partition swapping
* widely used; swupdate/RAUC (but also just a simple shellscript)
* embedded systems
* failsafe if partition swap is atomic!
* recoverable if boot into rootfiles-fs b and it crashes, then scroll back to the old version A (but instead of investing into recovery, invest in testing)
* to check: cpio them together? also scpn - what this?

* sw-update also has C-lib to check the process of the update

### recovery image
* android also has used this mechanism
* advantage to partition swapping: much less smaller
* however: you have to maintain two systems
* most of the times some initramfs

### always use  initramfs
* used by desktops
* supportive method
* used by other mechanisms (e.g. OSTree)

### OSTree
* git for binaries; huge repository of file names
* also allows diff-updates
* also used by RedHat to do failsafe package-management
* qtotaupdate from code.qt.io: qt-ostree script
* after first run n target it will create a distributio of the current state (after user-merge), then sends it to the OSTree-repo
* on target the server, which was just started on the host (laptop), can be selected, and then the newly offered version be used
* just fetches then what has changed
* also allows a roolback in case of need! but does not use double the space

### container based
* container runtime: and then twice the container A and B; good for fleet management; normally they take care of failsafety and sometimes of recovery
* always able to recover system: 
* balena, torizon, pantarcor and others use this
* docker also does diff-updates: so it just switches the difference between the filesystems
* looked quite comfortable; had a fleet-manager

### summarum
* only packaages in case of technician
* partition swap and OSTree: both failsafe, both work very well; don't have to think about oartitioning in advance (more flexibility)
* container: fleetmanagement is helpful: good for separation between teams; also good for small companies
* why was reboot required for the OSTree-hardlinks-change? boot into the new system; usualy keep the previous version, but also thousand versions cn be left; cleanup has to happen manually
* for uboot also some kind of partition swapping is possible, but unfortunately not all eMMC support this
* looks like OSTree just replaces the whole file; no diff on file (but maybe possible with squashfs)

--------

### Community driven coding guidelines for QML - Furkan Umzumcu (Autodesk)
* why guidelines?
  *  pool experiences from vastly different industries
  * sane defaults for new comers to the language
  * base for tooling
* experience differs between platforms: but depending on how qml is used, it can be deployed in both environments
* mindshift for declarative approach

* yet another guideline?
  *  official best practices for qml and qt quick; qml best practices search
  * he noticed that something is down, unstructured first, then community-driven (initially by him)
### Guidelines are not
  * unchangeable
  * see emerging patterns in code and adopt to it
  * the absolute truth
* making code easier to read, undertand, write and maintain - if the guideline does not support this, then what is the use? just imposing the will?
* `qmllint`?
* the newcomers to a project will also benefit from it

### how to read qml code
* first read the filename: what to expect from the class/interface?
* id, which proerpties are exposed?, which signals - this is the interface
* then comeas the implementation; rectangle and mousearea ..

### code order
* designers don't work the way xevelopers work; so a given structure is helpful forthem to understand and to handle their changes
* check his good/bad examples
* function ordering - functions not really important, therefore at the bottom
* states and transitions at the bottom before the signal handlers
* quite focussed about the readbility of the code
* not go on the hunt for things, you just see the things

### bindings: declarative > imperative style
* js-function can be used inside a bnding and this would still be declaratie style; even when this is not recommended
* unnecessary evaluation of bindings

* on how many ways a qml object can be exposed to cpp: cntext proerpties, global object, signletones, instantiated ojbects (last one preferered)
* singletons for API-access only
* "if you look at QML, you should just look at one block of code, no other files"
* prefer instantiated types over singletones for data

### watch out for ownership rules
* use a proerpty for exposing, but not directly

### memory: profile first! needs contributions
* functions use imperative form; signals tell you that something has happened (wording)
* rule of thumb:
  * when communicating up, use isgnals. when communicating down, use functions.

### one size does not fit all
* todo: check for the photo from the phone
* implicit size: space occupied when no explicit size or anchors are set
* explicit size: space occupied when an external size like width, heith or anchors are set
* content size: space occupied by the contentsof a view
* padding: space between the content item and the edge of a component
* margin: space between two controls
* inset: space between background and the edge of a component

### javascript
* latest supported ecma-script-version: 6; but with some new features from 7 and 8
* use const, use let instead of var

* todo: check the github repo from him: github::furkanzmc/qml-coding-guideline
* qt-documentation can also be changed and adjusted

--------

# lightning talks

--------

## Five things out of KDToolBox - Guiseppe D'Angelo

### KDSignalThrottler for Qt
* reduce the frequency; also debounce, ..

### model view stuff
* shove tablemodel into qlistmodel

### tab interface
* move tabs, reattach them

### qt is transitioning from qmake to cmake
* "cmake-project" with -qt 5 as param: createds a cmakelist.txt

### ui watchdog:
* detect frozen mainthread: instead of writing it yourself
* add to code and to the cnetral main
* and if the UI is blocked, then just add handler code or a debugger .. two lines of code
* toContainer: 

--------

## porting qt application to webassembly - benjamin Deuter
* "geek in business"-company
* comes from the tradition of compiling stuff to javascript and to run it then in the browser
* why would you want to do this?
* porting via emscripten; follow the guideline
* example: simple statemacine first, ten porting some snake-game; check the pro-file first
* runs snake and arqiver - compiled with Qt
  * but file-access not possible: because sandboxed

--------

## handling large amount of text in QML - Shantanu Tushar
* customer request: not show just te last 1000 lines, but the whole big file?
* "textarea sucks" - does not work when you use lots of lines in textedit
* this worked fine for widgets, but not for qml
* firststep was profiling: resizing 
* webview was working, but does not scale
* listview with delegate: textarea was working 
  * but now the scrollbar would be wrong (slightly), but selecting across delegates did not work

--------

## setup a shareable dev environment in docker - julian grube
* semasquare
* the problem: it works on my machine
* development on embedded system always require a big tooolchain: now bigger teams, but the usual case is now: it does not work on all machines
* lots of time is also wasted on onboarding; setting up systems, ..
* requirements:
  * dockerfiles
  * makefile
  * CI/registry
* and then you would have three build-targets

--------

## why energy consumption matters and how to eco-certify your software
* KDE Eco
* what does paper products and software have in common? the blue angel
* production of devices takes 45% and 55% is for the usage of those devices (ICT)
* efficiency (achieving the same result with less energy) and conservation (avoid unnecessary consumptions)

[end]
