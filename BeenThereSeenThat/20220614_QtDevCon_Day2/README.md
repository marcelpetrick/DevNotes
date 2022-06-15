# 20220615 Qt Dev Con - day 2

## how i learnt to stop. eorrying and lobe Unicode - guiseppe d'angelo
* most important part about cpp is tooling, so use all the available tooling (clazy, clang-tidy,..) to make your code as safe as possible

--------

## cross platform CI/CD setup - make it easy - Lukas Kosinski
* retired developer, does not code so much anymore
* he doesn't claim the title of genius: evangelist of ci/cd-pipelines in Qt projects
* happy father of six guinea pigs

### agenda
* CI/CD basics
* example gitlab ci/cd setup for qt project
* introducing ci/cd in legac projects

* a story: former company, he worked as developer, no tests,  no conventions, no ci/cd, much testing by testers, but not ci/cd: but the company did not listen
  * when a new release for mac was prepared, so he struggled to do this; also create a release on friday; .. you know what follows
* but a release should be done on organisational level; on servers, runners, .. not on dev-computers; everyone needs access
* safety, save time and money

### what makes up CI/CD?
* cotinuous integration: code should not be broken when it is integrated
  * unit-tests, static checking, create current documentation
* continuous delivery:
  * create installers, upload stuff, sign installers, ..
* one rule: Keep the software in releaseable state (CI/CD golden rule): take the code and release it at any moment

### Hygiene in work with CI/CD
* despite having the pipeline, always run tests locally before pushing
* even the best setup won't catch everything
* aways optimize pipeline time
### ci/cd tools to choose
* code hosting service
* ci/cd solution
* ci/cd tasks runner
* artifacts repository

### what to choose as CI/CD tasks runner?
* also matter of security (office or shared one?)
* mac mini: android, ios, macos, linux with docker, windows: five types on one machine

### example gitlab ci/cd pipeline
* pipeline; stage; jobs
* qt 6.3, cmake as the build system, ruby scripts
* the example project works on every platform: because it is just a single window xD
* before you need runners: one for ios and mac-jobs, one for window, android and linux
* gitlab-ci.yaml file (goes to root folder of gitlab)
  * defines the stages: build, test, packing
  * put the build-instructions into one script to run it as well locally
  * also move the result to the next folder for test
  * if it succeeds, then a green checkmark, else a red cross
* every job has a job log; 

### gitlab ci/cd variables
* TEAM_ID $ENV{TEAM_ID}
* how to keep sensitive data secret?
* protected variables, make yourself maintainr, only maintainer can push to protected branches and merge on them; so no one can extradit protected variables

* include templates from other repositories:  company wide branded template (which has some benefits)

### why ci/cd in legacy projects is challenging?
* low code quality, huge number of little issues;
* what to utomate first? wat to automatize first? compiling, packaging, then regression tests

ci/cd makes sw engineers more productive and happier; impact on business: either have a high-quality sotware code base which allows easy releases or have low quality code where it is hard to release
* gitlab.com; kosadev; example ci gitlab .. (add from photo)

* relesae for ios is done with fastlane: release app to appstore and google play immedietaly
* google file based istribution for testing
* todo check what means CTA?

--------

## QML Hot reload in practice - Alex Leutgöb (Felgo)
* how to improve review meetings for remote teams
* fueled by the story: pandemic changeed the way of working
* Felgo SDK expands the Qt SDK
* Felgo Live is their hot reload solution
### the virus and challenges
* implications for remote work and collaboration: created new working models
* more overhead of communication, but less knowledge transfer
* felgo powerweek: people work on own projects, once every three months every employee comes to a single location, team-events in the afternoon/evening
  * more about spending time together and interaction
### chalenge in leadership and management
* keeping people motivated
* sustaining team productivity
* creating a hybrid work environment
* challenge;: giving key feedback remotly:
  * keep communication, foster learning and knowledge transfer
  * issue: missing conversational cues in written feedback
    * like body language or tone f voice
	* tipps:
	  * use clear language: so no assumptions are made
	  * use tools
	  * use feedback processes: give feedback based pn Asana's do, try and consider approach
	    * do: find a solution and take actions
	    * try: explore and provide options
	    * consider: thing through and respond
* use collaborations tools: so status can be checked without being directly asked

### summary
* communication is hard if going fully remote
* communication between deprtments even harder
* proper choice of tools can remove a lot of friction


### facts about MQL/QtQuick
* MQL: language, QtQuick: UI Framework
* very mature (more than ten years in the Qt SDK)
* QML is declarative, JSON-like syntax
* node define a tree of objects for visual items andbehaviour, lgoic added via javascript

* QML is reactive
* propery bindings

### Advantages of QML UIs
* help for prototyping, better than a sheet of paper
* easy to maintain and saves paper
* can be tested with squish

### WML code reload
* stop waiting for builds :rocket:
* usual cycle is: code, save compile, deploy, test and repeat
* compile and deploy can take huge amounts of time, but an interrutpion no case how long
* if not just one device, but severalplatforms, then this scales!
* and this is also done multiple times per day
* how to cut those two parts out to save time?

* code reload: changes can e applied automatically to a running program, without build package and deploy steps
* no manual restart required
* QML preview is part of QtCreator and enables automtical reload: [example]; is reloaded after save
  * but this just happens for the dialog (loader) when you really click the button; so the app-state gets lost on reload! this is a problem
* what is hot reload? applies changes while keeping the current state

### Felgo Live to the rescue
* server and client (like the preview)
* integrates as plugin to QtCreator

* todo test: felgo live IDE; gitlab-expansion: ide.felgo.com
* hot reload should also work on this; model changes also do work instantly!
* how does code reload work: c++ layer with qml engine does the heavy lifting

* fast project with us automotive customer: several workflows tried: nightly bilds, felga cloud builds; 
* split up team nto core development; ad review dev team
* shipped first vrsion in two months; immediate polishing of things; reduced amount of follow-up-meetings; so we only had to work on bugs, not polishing
### my questions
* live ide is completey free (for students)
* for custom sbc (like imx8) they have in the licensed version already some connector

--------

## Hybrid Qt development: boosting your projects with Python - Dr. Christian MAurereia-Fredes

* why is it really cool to add new languages to the Qt ecosystem?
* check his slides on qtinfo.dev/qtforpython_qtdevcon22

* Python and Qt are roughly the same age
* besides their mautrity, both stand out for a common goal: simplicity
* but you can make simple languges complex as well
* idea is not to replace cpp with python
* PyQt already exposed Qt-API to tech people
* but they (Qt) wanted to do more
* but we can not neglect the impact on fields like Data Science and AI; and the many conferences and organizations
* popularity is the reason: many people start to jump into python and start to learn it
* 2022 update for the popularity: ?
* most of the same python has is because of popular modules, which rely on compiled languages like fortran, c, cpp, ..
  * numpy, pandas, pytorch, tensorflow
* initial question was: why just be another binding? there are already some?
  * but casing, for instance, looks different due to casing
  * feature import runtime: snakecase; also use "true_property"
* opaque containers: python containers need to have a c++ containers
* python popping first element of list: use deque instead of list
### project distribution and packaging
* problem with the zipped-shipping, like customers grabbed the business intelligence
* compatible with many freezers and compilers: PyInstaller; works for Qt5 and Linux, macOS and Windows
* he also submitted a patch to make briefcase compatble with qt6
* todo: tomorrow pyside (tomorrow the webinar)
* not only vanilla python; PyPy recommended; on avergae 4.2 times faster than CPython; has JIT
  * a couple of minor releases behind
* add more value for the user, instead of nitpicking "this is mine, that is yours"
### Shiboken - binding generator
* used by PySide: shares large
* libclang for parsing the headers; but codes explodes
  * but how to handle things: like void? what a refernece? how to handle a pointer? -> you can't
* how to use: cmake-file and code; then two shiboken files (bindings.h and the bindings.xml)
* example: a scriptable application; exposed QApplication-interface, can be modified then by python "plugins" (used by autodesk maya)

* QtScrypt: final goal: enable the use of python modules from c++
* Qt 6.3 enables crosscompiling (again): so building for RAspberry Pi is working now
* WebAssembly will be next big thing inside Python

--------

## Qt Design Studio - Bridging the gap between developers and designers
* similar talks before, but will show the results of the last half year
* Figma integration now new; Design Viewer; Qt Creator
* Qt's dedicated Design Tool
* languages behind is QML; 2D and 3D (last one is commercial)
* fast and iterative release approach: now once amonth; before every 3 months
* Figma as design system tools for UI/UX; creating a structured design

--------

## Speeding up compilation using precompiled headers - Kevin Funk
* if build from scratch takes 20 min and someone just changes the global header, then what to do in that time?

### cmake: speeding up compilation
* gcc versus clang: friendly rivalry
* lots of forward includes is great
* no difference between clang/gcc and ninja/make
* in short: can't make general statements because it depences on code base, code complexity, optimization base
* profile the build time of your code base
* therefore what other options are there: ninja instead of make?
  * ninja focusses o speed
  * one single file contains all the instructions: build.ninja; not meant to be human readable
  * compared to the normal recursive make-file-system this is simple
* cmake supports ninja as generator: cmake -G Ninja ...
* example Ruqola: 1200 files: runtime for rebuild with nothing changed: 5s versus immediate return
* how to use ninja: change in "kits" the cmake generator to ninja -> done

### ccache: caches previous compilations of compiler-units
* available for gcc and clang
* reuses the build-support
* prefi compilation commands with `ccache`
* or masquerade ccache as your compiler
* export path to ccache; has alead links to ccache
* or use cmake: compiler_launcher=ccache
* ccache -s for statistics of the caching
* switching branches: now it would rebuild the whole stuff, but with ccache will kick in
* when just recompiling Qt-lib he does not use ccache, because it would add overhead; for that CCACHE_DISABLE=1 make
* configuring ccache memory size, .. (check his slides)

### another approach: using precompiled headers (PCH)
* headers are compiled into a special form, the next time the compiler sees this, it does not have to re-parse it
* 20 year old feature
* reduce compilation time: for instance including QWidget would result in 93k LOC!
* each time a source file includes that header, ithas to be reparsed

* handcrafted versions can save even more time: is part of the KDToolBox: 
* cmake 3.16 is required: tagrget_precompile_headers(ruqola_cora PUBLIC .. PRIVATE ..)
* can also be disabled for specific files

* ccache for projects you actively work on
* ninja for all usages

--------

[end of the Qt Developers Conference - closing words ..]
