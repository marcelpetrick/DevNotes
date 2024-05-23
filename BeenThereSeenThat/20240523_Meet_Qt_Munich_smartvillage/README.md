# 20240523 Meet Qt Munich - smartvillage

* shoutout to Michael Zuchtriegel for recognizing me :sweat:

## Intro by Jakub: about next events ..
* Qt World Summit in 2025 in Munich

## Maurice Kalinowski

### Qt on the desktop and mobile
* cross platform is more important than ever:
 * ongoing ARM recvolution
 * upcoming OS fragmentation
* tighter integration with OS services
* connecting to cloud services
* cover 90% of the active Android MArket (Vladimir does this): always the next Qt version to come will cover this; 6 month-evaluation; not just "putting a finger into the sky"

### Qt and XR
* Qt has always been about cross platform
  * target apple vision pro 3
  * meta quest 3
  * from CES: asus, sony, xReal and TCL will come
* new design domain - spatial computing

### goals
* become the reference framework to create XR exeperiences
* multi-platform Qt support

### GenAI is everywhere
* ![]() - image of the genai todo
* generate all test-cases when you have introspection: should be easy - Qt company looks into those fields

### Open platform
* software architecture is getting more complex every day: different frameworks, platforms, languages
* vision: make QML and Qt Quck the moder UI framework for everyone
* seamless integration without any glue
* available already:
  * Qt for Python
  * Qt/.NET/C#
  * CxxQt/Rust

### Qt on Embedded
* Qt provides true chipset independence
* new hardware: from NXP, TI, Boundary devices, Infineon, StarFive (RISC-V) - scale through partnering
* update operating version support
  *  embedded linux/Yocto/Debian, QNX, Integrity, VxWorks
* Performance Evaluation App: an image, which "just" has to be flashed, run and gives "all" the results

### Qt Development in the cloud
* Boot2Qt AMI in AWS marketplace
* shift hardware selection tot he right
* accelerate prototyping
* harmonize your development setups
* cloud scalability on your needs
* EC2 Development Host <-> AWS Gravitron ARM vECU <-cloud->Boot to Qt Software Stack
* stream the UI via WebGL to the user
* this can put the hardware decision into the right point in time
* what if I could have something running in the cloud:

### Qt Design Studio Strategic Goal
* figma integration
* 3d UI integration
* 2D UI creation
* enable smooth workflow between Qt Design Studio and QtCreator
* optimize QML code for selected Qt target: Qt6/Qt Quick Ultralight (?)

### Qt Creator strategic goals
* productivity: capability ofhandling projects with thoussands of files, quick startu time, ai-boosted suggestions
* user experience: easy configuration and customization, modern ui that supports productivity
* scalability: possible to extend the functionality via extensions, a wide selection of tool extensions available, additional LLMs, support for additional programming lnauges
  * preview for changes of the ABI

## QA tools
* better insights into legacy code bases
* aggregating test data and identifying failures
* typical challenges our customers are facing:
  * time and budget constraints
  * cost of issues
  manual testing
  * transition to automated pipelines (CI/CD/CT)
  * manual testing: mondane - boring ..
  * changes in the software team
  * security and safety
  * scalabilty and performance

---------
𝙋𝙝𝙤𝙩𝙤 𝙙𝙪𝙢𝙥: 𝙈𝙚𝙚𝙩 𝙌𝙩 𝙈𝙪𝙣𝙞𝙘𝙝

Time to assing some purpose to a free day..
This is a raw, unedited, unfiltered photo dump.
Only the first ninety minutes have passed and I got a refresh for the product pipeline for the Qt ecosystem, reconnected with a former colleague, take my notes - wonder what the rest of the day will bring.

Shoutout to @michael zuchtriegel, @jakub, @mauricce and everyone attending and making this event possible. Thank you.

Btw. Qt World Smmit 2025 takes place in Munich, woah!

#neverstoplearning #bestpractice #meetqt #qtws

----

# basyKom - Frank Meerkötter
* since 2004 they have beend developing applications using qt, qt quick and c++
* is Qt Service partner
* OPC UA, umati, open62541
* OPC UA is a central component of Industry 4.0
customers are machine builders, plant builders, medical, mesaurement equipment


### benfits of using qt - what makes it a great framework
* longevity, performance, efficiency, cross platform, rich framework, easy integration, FOSS (scratch your own itch), ability to create high fidelity HMIs and great user experiences
* basyskom is part of the ux group - like imago; mago helped them to create a measurement device and ugrade its embedded hmi
* narda fieldman: embedded linux on an imx7 (no GPU), battery powered, not touch controlled, has buttons, (hardware keys), hmi is done using Qt Quick and the software renderer, 20k lines of code, custom charting implementation
* narda-tsx as evaluation tool: is qt quick based, which is an unusual approach
* shared codebase: shared ui-code
* qt as common SDK enables a shared mindset for all developers involved
*
