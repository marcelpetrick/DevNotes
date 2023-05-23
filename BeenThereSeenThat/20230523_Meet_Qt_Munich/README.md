# 20230523 Meet Qt Munich

## intro
* 25 years of experience in a nutshell
* Framework for HI/HMI, cross platform, appLICATION AS WELL AS MIDDLEWARE AND TOOLS FOR DEBUGGING, ideS, PROFILING, BUILD/PACKAGING/DEPLOYMENT
* E2E lifecyle: for designer snand technical architects, QA engineers and ops, product analysis and moentarization
* Qt product portfolio: design -> develop -> deploy -> insights
### Qt 6
* Qt5 hat 8-9 years of lifetime; problem with api-compability - tough decision for a new major version to cut some leaves
* Qt Quick 3D: particles, esh morphing, level of detail, global illumination, pyhsics integration, collision detection
* miimal Httpserver: quick and lean
* QML lint (todo check this), Qt Quick compilers
* qml: dynamic, static and strict: dynmaic is right now, static is useing ahead of time compilation - for very minimla application, strict mode ist some hybrid (precompiled as much as possible, but engine in background)
* Qt for WebAssembly with Qt 6.4: cunn c++ code in the browser; "webification story" - helpfl for companies to transform apps which run already for 20 years ..; but limitations due to sandbox, for instance for the multithreading-support
* 6.5 is the second LTS release
* every three minorreleases will be an LTS version
* 6.5 addition: dedicated api for the config and permission: checks: previously native code was needed
* QML language server
* Qt for Python: also for Embedded (check this TODO) - deploy all dependencies via ssh or rsync, run against gdb
* 6.6: might have responsive layouts - known from the web
* inux and Windows on ARM is a regional thing, Asia
* Back to Berlin: november 28th and 29th in Berlin

## algoriddim
* federrico tessmann co-founder, frederik seiffert (cto)
* first to iOs (ipad), then windows and android
* certain requirements: high framerate, low latency; also huge music database in the background
* Qt: utilized by large entreprises, stability - great documentation and support
* actively developed and frequent releases
* using GNUstep to support objective-c on non apple platforms
* but you need objective-c runtime for the platform
* Qt Quick and QML

## Qt DEsign workflow
* UI composition -> development -> manage -> test
* Qt Design Studio -> Qt Framework/Qt Creator -> Qt Insight -> Squish UI tester, coco code coverage, avixion static code testing
* Insight: tracker for QML application - provide data, that data is sent to a cloud service, then user flow, etc can be checked, uptime of device, location of device, etc.. - metrics from the field how it is used
### From Figma to Qt Design Studio
* Keean Afrasiabi, tech artist in Munich
* Figma Bridge and Figma Design Practices
* import from PS, blender, adobe, xd, figma, .. to QB -> Design Studio -> QML
* bridge file imported to qt design studio: all you components are there as well
* stats for variants of buttons - very nice
* keyframe almost any property - for best visuals

## benefits of using squish
* simulate end user actions on the application nd then verify if the app behaved like expected
* cross platform
* multi-toolkit: also for windows native, mobile apps, web apps, ..
* cross-device: run test on different machines; simulate the whole workflow
* multi-language: js, python, ruby, perl
* preferred python .. becauae of the 3rd party tools
* individual perspective: simulate user actions, verifying behaviour of the application, appearance of the applicatioon, increasing test accurary, reducing human factor
* organization perspective: increasing the test coverage, high repeatability and scalability reducing feedback time, people focussing on creative tasks

