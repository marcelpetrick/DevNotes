# 20240410 - Securely connect Demo Badge to the AWS cloud - Embedded World

```
LIVE AI training at Embedded World – Get a Dev Kit and Software Package
EVENT OPENS IN
0d 10h 52m 40s
REGISTRATION CONFIRMED

    M
    Marcel Petrick
    Price
    $30.00
    Not Marcel Petrick ? Click here

EVENT DETAILS

    When
    Wednesday, April 10, 2024 · 10:00 a.m.
    Paris (GMT +2:00)

    Add to calendar
    About
    Date: Wednesday April 10, 2024
    Start Time: 10:00 AM local Germany time
    Where: Nuremberg Messe, NCC Mitte, Munchen 2
    Duration: Three hours

    Attend this three-hour training session and walk away with the latest hardware and software to serve as the foundation of your Edge AI application development. Work with AI-native compute solutions and be among the first developers to use the Synaptics Astra™ Developer Kit, which offers you a chance to get ahead of the curve in a classroom environment. You’ll be trained on the tools that enable real-world AI capabilities to be deployed on your IoT solutions.

    By the end of the workshop, you’ll understand that developing and working with AI-enable machine vision applications do not have to be overly complex. The workshop will focus on inferencing using SyNAP™, a proven and secure neural network development and optimization framework that is foundational to Synaptics Astra, the AI-native compute platform for the IoT.

    Giveaway
    Sponsored by Synaptics, each attendee will receive a Synaptics Astra™ Developer Kit to keep, along with all the associated software, libraries, and algorithms, and live hands-on training that’s required to implement an AI use-case (total value of hardware and software is approximately $2000).

    Cost to attend: $30US (approximately 27 Euros)

    Tentative workshop agenda:

    1. Introduction
             a. Workshop goals
             b. Introduction: Synaptics Astra Platform
    2. Getting to know your hardware and software
             a. The Astra Developer Kit and System-on-Chip
             b. Embedded Software and GitHub repos
    3. SyNap Edge AI framework with selected use cases
    4. Break
    5. Hands-on development time
             a. Inferencing demos with pre-installed models
             b. Working with SyNAP on vision-based models
                  i. Model conversion
                  ii. CLI to run model
                  iii. Visualize results
    6. Q&A, Next Steps
    7. Wrap-up

    Price
    $30.00
    Language
    English
    OPEN TO
    Open to developers on a first come, first served basis, up to 40 registrants. We have the right to refuse participation after registration and payment is received and a credit will be given.
    Dial-in available
    (listen only)
    Not available.

FEATURED PRESENTERS

    Webinar hosting presenter
    Michael Pan
    Sr. Director of Engineering for the IoT Processor division at Synaptics
    Michael Pan is Sr. Director of Engineering for the IoT Processor division at Synaptics, responsible for product planning, BSP & kernel development, security, and DevOps. With over two decades of experience in embedded systems, Michael leads...
    Full Profile
    Webinar hosting presenter
    Abdel Younes
    Director, System Architecture and Machine Learning Frameworks, Synaptics
    Abdel Younes leads the AI/ML system architecture team at Synaptics, as well as the development of the company’s SyNAP framework that supports AI on Synaptics’ edge SoCs. Abdel has 20+ years of experience leading projects and teams in various...
    Full Profile
```

* Windows user shall use WSL and then install any Ubuntu
* second option: or a true virtual machine, virtual box
* unwrapped the board and set up everything, including wifi
* Rich Nass gave the introduction

* Adel Younes and Lorenzo, located in Lausanne
* Astra platform
* `really excited to be here` xD
*

# angeda
* worskhop goals
* snyaptic astra platform
*code repos overview: yocto linux, syNAP
* first hour long session is an overview with selected AI use cases
* hands on development
* quick pulse of te room: Qr-code, then office.forms
  * 71 beginner, 17 intermediate, rest advanced
  * most prefer linux over rtos and android and windows: 50% versus rest
  * major hurdles: proprietary software, and the SoC are not designed for AI, lack of standards only 17%
* they want to develop awareness about openSource toolkits
* get familiar with Edge AI workflow and pipeline stages
* how to promote more standards and best practices
* workflow: sense, process, connect
* 8 TOPS NPU machine for the Astra-SoC we got (wow)
* core board where additional board can be plugged in
* Synpatics SL1680; 4 cores ARM
* abstraction layers for the synaptics sdk: below RTOS, Linux, Android
* stong background for synpatics for AI: first finterprint, then pc trackpad palm prediction, then multi-modal capable SoC, to fleible platform nowadays
* what does Synpatics offer?
  * BYO data
  * BYO model
* BYO data
  * generate production modesl from snypatic refernece models
 * post training compiler optimizations
securely deploy with guaranteed highest performance metrics across portfolio

## How to install
* WSL2 with Ubutnu 22.04
* Docker
* SoC has already an image with basic wayland shell
* SocC has already some apps, like quad-video player
* video for linux api
* single object detection, dual obect, pose estimation (working out of box, more or less fluent - 15 fps?)
  * even running three video streams and doing pose estimation works without performance challenges
* for

## github
* https://github.com/synaptics-astra
* getting started guide
* also: Astra Yocto Linux User Guide; default image can be downloaded on github as well
* synpatics Astra SDK: not doing open development yet, but main branch and release 0.9.0 can be found
* also minimum number of layers to get an functional image
* `crops` as docker container - reproducible environment; clean environment for the whole org
* import the two tar.gz to docker ..
* import from TFLite, TesnorFlow, PyTorch, Caffee, ONNX is possible
* docker and python based tooling and process, enabling cross-platform support
* network graph and metadata generation for target NPU
* best is TFLite quantized
```
 1475  sudo docker load -i ../docker-images/synaptics-astra-crops-0.9.0.tgz\n
 1477  sudo docker load -i ../docker-images/synaptics-synap-toolkit-3.0.0.tgz\n
    /run/media/mpetrick/D241-940D/Workshop USB stick/docker-images 
```
* yolov5s model, face detection
  * generate out of that a synpa-file
* optimization by pruning and applying pre-processing steps for the training is possible
TODO add image of the slide
* syNAP Driver Architecture
* C++ application with 10 lines of code (ok, this has to be proven ..)?
* trusted execution environment: SyKure Truseted application
  * NPU is completely isolated into the secure environment
*




## where do i start?
* go to these model repositories: ultralytics
* either use v5 or v8 for yolo; usual detection - pick the model (step1)
* yolov5 is flexible enough to recude the use-case only to faces: 80 class model
* TODO image for the hgh level workflow
* what to do first: install te toolkit
* runtime launches .synap file, delivering key benefits
  * graph-slitting, heterrogenous infering across NPU, CPU, GPU, DSP
  * qualtzation: mixed-precision, entropy optimized, per chnalle
  * pre-processing: input data format conversion on NPU
* SL1680/SL1640 functional block diagram
* PPU can run OpenCL oor OpenVL code
* PPU - ConvCore (NN) - Tensor processor (TP)
* ghcr - github contaner registry
* quanitzation: floating point arithmentic or integer; for maximum precision floating point is better, but interger is faster - especially 8 bit
  * then you have to refer to a typical dataset typical for your use-case
  * extract range of the floating point values, result is min and max integer
  * quatize to int8
### TODO
* how to use docker for the dvelopment workflow for c++?
* how to build own yocto/poky/bitbake?
  * how to add custom layers?

* took today less goodies, but more knowledge from the exhbition
