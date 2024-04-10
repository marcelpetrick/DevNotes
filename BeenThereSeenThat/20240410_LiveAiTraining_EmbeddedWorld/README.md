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
* what is heterogenous AI inference?

## Hands-on tutorial
* setup is running


```
The error you're encountering, invalid reference format: repository name (library/USB) must be lowercase, usually occurs when Docker interprets part of the command as a repository name when it shouldn't, often due to an unexpected space or character. In this case, it seems like the issue might be related to how the current working directory ($(pwd)) is being interpreted or passed into the command.

Given your command structure, if the working directory ($(pwd)) or $HOME path contains spaces or special characters, it can lead to this error. In UNIX-like systems, paths with spaces must be quoted or escaped properly.

Try modifying your alias to ensure that paths with spaces are correctly handled:

bash

alias synap='sudo docker run -i --rm -u $(id -u):$(id -g) -v "$HOME":"$HOME" -w "$(pwd)" ghcr.io/synaptics-synap/toolkit:3.0.0'

Notice the addition of quotes around "$HOME":"$HOME" and "-w "$(pwd)"". This should ensure that paths containing spaces are interpreted correctly by the shell and passed properly to Docker.

After updating the alias, try running the synap help command again.
```
* synapsis haptics - synpatics; last 2-3 years the company was transformed into the IoT space
*  MPUs - a class processors; MCU - M class processors; all tied together with unfied software
* security unified across all platforms
  * chromecast was initially snyptics SoC

* go to github, find model, convert it
`synap convert --model yolov5s_face_480x640.onnx  --meta yolo_q.yaml --target sl1680 --out-dir compiled`
```
    ~/repos/synpatics_ai_tutorial  synap convert --model yolov5s_face_480x640.onnx  --meta yolo_q.yaml --target sl1680 --out-dir compiled
    ~/repos/synpatics_ai_tutorial  ls -lah                                                          ✔  35s 
total 28M
drwxr-xr-x  7 mpetrick mpetrick 4.0K Apr 10 12:25 .
drwxr-xr-x 47 mpetrick mpetrick 4.0K Apr 10 12:19 ..
drwxr-xr-x  2 mpetrick mpetrick 4.0K Apr  4 21:24 code
drwxr-xr-x  3 mpetrick mpetrick 4.0K Apr 10 12:26 compiled
drwxr-xr-x  2 mpetrick mpetrick 4.0K Apr  4 21:24 extra-models
-rw-r--r--  1 mpetrick mpetrick 4.0K Apr  5 04:23 README.txt
drwxr-xr-x  9 mpetrick mpetrick 4.0K Apr  4 21:24 ref
drwxr-xr-x  2 mpetrick mpetrick 4.0K Apr  4 21:24 sample
-rw-r--r--  1 mpetrick mpetrick  394 Apr  5 04:23 yolo_od16.yaml
-rw-r--r--  1 mpetrick mpetrick  433 Apr  5 04:23 yolo_odmqt2.yaml
-rw-r--r--  1 mpetrick mpetrick  496 Apr  5 04:23 yolo_odmqt.yaml
-rw-r--r--  1 mpetrick mpetrick  432 Apr  5 04:23 yolo_odmq.yaml
-rw-r--r--  1 mpetrick mpetrick  394 Apr  5 04:23 yolo_od.yaml
-rw-r--r--  1 mpetrick mpetrick  112 Apr  5 04:23 yolo_q.yaml
-rw-r--r--  1 mpetrick mpetrick  27M Apr  5 04:23 yolov5s_face_480x640.onnx
    ~/repos/synpatics_ai_tutorial  cd compiled                                                              ✔
    ~/repos/synpatics_ai_tutorial/compiled  ls -lah                                                         ✔
total 7.0M
drwxr-xr-x 3 mpetrick mpetrick 4.0K Apr 10 12:26 .
drwxr-xr-x 7 mpetrick mpetrick 4.0K Apr 10 12:25 ..
drwxr-xr-x 2 mpetrick mpetrick 4.0K Apr 10 12:26 cache
-rw-r--r-- 1 mpetrick mpetrick 1.1M Apr 10 12:26 model_info.txt
-rw-r--r-- 1 mpetrick mpetrick 5.9M Apr 10 12:26 model.synap
-rw-r--r-- 1 mpetrick mpetrick  63K Apr 10 12:26 quantization_info.yaml
    ~/repos/synpatics_ai_tutorial/compiled 
```

```
    ~/repos/synpatics_ai_tutorial/compiled  sudo adb wait-for-device                                        ✔
* daemon not running; starting now at tcp:5037
* daemon started successfully
    ~/repos/synpatics_ai_tutorial/compiled  adb devices                                                     ✔
List of devices attached
SL16x0  device

    ~/repos/synpatics_ai_tutorial/compiled 
```
* adb just simpler than ssh and scp



#### linkedin pretext

-----------

𝐎𝐤, 𝐈 𝐜𝐚𝐧 𝐠𝐨 𝐡𝐨𝐦𝐞 𝐧𝐨𝐰. 𝐈 𝐬𝐚𝐰 𝐞𝐯𝐞𝐫𝐲𝐭𝐡𝐢𝐧𝐠.*

Travel worked well, found a parking spot immediately - only ten minutes from turning off the car to checking in with my printed voucher (#germanThings 🙈). Therefore, I had some minutes to check the exhibition itself. Visited booths from #nvidia, #greenhill, ... ran into my former esteemed coworker @elmar (what a surprise!) and entered the seminar room. Funny coincidence: traveling from Munich and get trained in "Munich 2".
The workshop by Synaptics revolved around their #edgeAI platform, Astra  Machina, which features an SBC with the Astra SL1680, which NPU offers up to 8 TOPS. They offer a framework, which enables developers to customize any given classification model and convert it to their *.synap format, which offers some benefits. The SBC is preflashed with a #yocto Linux, ...
So, while doing the hands-on on the gifted hardware, we were walked through several setup steps, converted a #yolov5 model, and ran some inferences. Choosing a proper quantization improves performance. Also, the whole team was super helpful, and in the end, everything was working. This was a great experience. Thank you, Abdel Younes, Lorenzo Keller and everyone else who was involved.

(Sidenote: this yolov5-model-usage reminds me to publish my #yolov5 driven catcam. It's been running for almost a year now :3)

Now I can enjoy a short break with more exploration and then the next training starts. Looking forward.

*Just kidding. The day just started!

#neverstoplearning #embeddedworld2024 #ew24 #classification #ai #yolo #synaptics #astra

-----------------

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
