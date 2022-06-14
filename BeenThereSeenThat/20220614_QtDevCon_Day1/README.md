# 20220614 Qt Dev Con - day 1

## Qt 6.3 and beyond? - Maurice Kalinowski
* oreview on Qt with web assembly
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
* 5 stages of grief: denial, anger, bargainin, dperession, acceptance
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





