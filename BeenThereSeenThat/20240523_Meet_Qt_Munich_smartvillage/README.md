# 20240523 Meet Qt Munich - smartvillage

## Intro by Jakub: about next events
* Qt World Summit in 2025 in Munich

-------

## Maurice Kalinowski

### Qt on the desktop and mobile
* cross-platform is more important than ever:
  * ongoing ARM revolution
  * upcoming OS fragmentation
* tighter integration with OS services
* connecting to cloud services
* cover 90% of the active Android Market (Vladimir does this): always the next Qt version to come will cover this; 6-month evaluation; not just "putting a finger into the sky"

### Qt and XR
* Qt has always been about cross-platform
  * target Apple Vision Pro 3
  * Meta Quest 3
  * from CES: Asus, Sony, xReal, and TCL will come
* new design domain - spatial computing

### Goals
* become the reference framework to create XR experiences
* multi-platform Qt support

### GenAI is everywhere
* ![]() - image of the GenAI todo
* generate all test cases when you have introspection: should be easy - Qt company looks into those fields

### Open platform
* software architecture is getting more complex every day: different frameworks, platforms, languages
* vision: make QML and Qt Quick the modern UI framework for everyone
* seamless integration without any glue
* available already:
  * Qt for Python
  * Qt/.NET/C#
  * CxxQt/Rust

### Qt on Embedded
* Qt provides true chipset independence
* new hardware: from NXP, TI, Boundary Devices, Infineon, StarFive (RISC-V) - scale through partnering
* update operating version support
  * embedded Linux/Yocto/Debian, QNX, Integrity, VxWorks
* Performance Evaluation App: an image, which "just" has to be flashed, run and gives "all" the results

### Qt Development in the cloud
* Boot2Qt AMI in AWS marketplace
* shift hardware selection to the right
* accelerate prototyping
* harmonize your development setups
* cloud scalability on your needs
* EC2 Development Host <-> AWS Graviton ARM vECU <-cloud-> Boot to Qt Software Stack
* stream the UI via WebGL to the user
* this can put the hardware decision into the right point in time
* what if I could have something running in the cloud?

### Qt Design Studio Strategic Goal
* Figma integration
* 3D UI integration
* 2D UI creation
* enable smooth workflow between Qt Design Studio and QtCreator
* optimize QML code for selected Qt target: Qt6/Qt Quick Ultralight (?)

### Qt Creator strategic goals
* productivity: capability of handling projects with thousands of files, quick startup time, AI-boosted suggestions
* user experience: easy configuration and customization, modern UI that supports productivity
* scalability: possible to extend the functionality via extensions, a wide selection of tool extensions available, additional LLMs, support for additional programming languages
  * preview for changes of the ABI

## QA tools
* better insights into legacy code bases
* aggregating test data and identifying failures
* typical challenges our customers are facing:
  * time and budget constraints
  * cost of issues
  * manual testing
  * transition to automated pipelines (CI/CD/CT)
  * manual testing: mundane - boring
  * changes in the software team
  * security and safety
  * scalability and performance

-------

𝙋𝙝𝙤𝙩𝙤 𝙙𝙪𝙢𝙥: 𝙈𝙚𝙚𝙩 𝙌𝙩 𝙈𝙪𝙣𝙞𝙘𝙝

Time to assign some purpose to a free day..
This is a raw, unedited, unfiltered photo dump.
Only the first ninety minutes have passed and I got a refresh for the product pipeline for the Qt ecosystem, reconnected with a former colleague, take my notes - wonder what the rest of the day will bring.

Shoutout to @michael zuchtriegel, @jakub, @mauricce and everyone attending and making this event possible. Thank you.

Btw. Qt World Smmit 2025 takes place in Munich, woah!

#neverstoplearning #bestpractice #meetqt #qtws

-------

# basyKom - Frank Meerkötter
* since 2004 they have been developing applications using Qt, Qt Quick, and C++
* is Qt Service partner
* OPC UA, umati, open62541
* OPC UA is a central component of Industry 4.0
* customers are machine builders, plant builders, medical, measurement equipment

### Benefits of using Qt - what makes it a great framework
* longevity, performance, efficiency, cross-platform, rich framework, easy integration, FOSS (scratch your own itch), ability to create high fidelity HMIs and great user experiences
* basyskom is part of the UX group - like imago; mago helped them to create a measurement device and upgrade its embedded HMI
* narda fieldman: embedded Linux on an i.MX7 (no GPU), battery powered, not touch controlled, has buttons, (hardware keys), HMI is done using Qt Quick and the software renderer, 20k lines of code, custom charting implementation
* narda-tsx as evaluation tool: is Qt Quick based, which is an unusual approach
* shared codebase: shared UI code
* Qt as common SDK enables a shared mindset for all developers involved
* lack of GPU required some "tight" programming and custom graphing code
* creating a desktop application with Qt Quick that behaves platform native is extra work; custom charting needed as well

-------

## Performance Improvements - Profiling - Qui Shen
* QML profiler and compiler
* CMake profiler
* QML bench (?)
* Qt Graphs as replacement for QtCharts
* Performance Evaluation App: to be used as base for 2D desktop performance application
  * example on some Raspberry Pi
  * released: integrated in next Qt version as demo (6.8?)
* Building Optimized Qt: see as part of the Qt 6.8 docu
* Qt Lite: 15% of original ROM footprint: static linking, Link Time Optimization and strip-command and Qt Lite

-------

# TeamViewer - Korbinian Kram
* 2.5bn installations, 630,000 subscribers
* global player, but national to Germany
* TeamViewer Tensor Product: bringing this to embedded products
* 150k+ installed embedded agents
* after-sales support: instead of regular IT handling this

-------

# Cyber resilience with Qt - Maurice Kalinowski
* cyber resilience act - legislation to ensure safer hardware and software
* PDE - product with a digital enhancement; SaaS is already covered by other legislations
* obligation to provide a duty of care for the entire lifecycle of products: this includes planning, design, development, and maintenance stages
* embedded Linux/Yocto stack: handle all libraries and knowing where to get them
* legislation impacts all vendors operating or selling in the EU
* topics:
  * secure development: secure development cycle, secure privacy practices, fuzzing and safety testing, code analysis tools
  * documentation: product manual, technical documentation, contribution verification and processes, risk assessment
  * incident handling: vulnerability management, notification responsibilities
  * process/certifications: CVE management, audits by customers, archiving, ISO27001 (Ongoing)
* hint: Qt docu should tell which implications in regard to cyber security it has
* "a rough sketch"
* applies for open source and also the commercial version
* documentation improvements: product manual, technical documentation, SBOM, transparent issue tracking, conformity assessment
* LTS phase: strict or very strict
* incident handling: reporting support, guaranteed response times, early warning list
* CVE dashboard (new), LTS-releases, extended support
* CRA classification: levels:
  * self-declaration
  * class 1 or 2
* it is easier to certify something if all components already are class 2
* once you have the certification you can only change very minimal things, else you have to re-certify
* discussion about LTS support changes: 3 versus 5 years, third party dependencies
* the ISO standard around the CRA has to be built in the next 3 years
* question: does the certification apply to self-built binaries?
* the product is a software, rolling out an update is not a new product
  * what is with a major update: definitely has to be done
* Rust: open platform discussion for Qt, but not plan to reimplement Qt in Rust
* push away from memory-unsafe languages like C++ ... but Rust has no certifications yet
