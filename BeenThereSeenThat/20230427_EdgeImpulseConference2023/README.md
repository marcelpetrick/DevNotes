# 20230427 intro talk for the conference from Amir Sherman
* some guy behind me recognized my face from last years presentation :hugginface:
* Amir Sherman is Chairman for Edge Impulse, he worked for 20 years for Arrow Electronics
* things like tensorflow, keras, openai, chatgpt, edgeml come and stay. but a lot of noise
* image recognition, speech recognition, NLT, fintech and insurance, predictive maintenance, robotics
* the semis are focussing a lot on AI: 90% of a room full of engineers will say: nvidia ..
* but qualcomm, intel, etc. would say otherwise
* cloud ai <-> edge ai <-> endpoint ai: not everything can be done on the cloud
* not everything will have 5 G, because it is draining the battery
* every sensor (camera, gyro, acceleration, ..) needs already energy
* in 2025 95% ofte indistrial IoT deployments wil include analytics or AI components .. Gartner
* the problem: quite a lot of different architectures; especially if you could choose freely
* goal for EI is to use all those technologies in one platform
* companies start their models with nvidia, but later realize they need something less pricey and less power consuming
* EI has royalty-free business model, so no impact on the BOM cost, total explainability, no black boxes; ML solutins in minutes, not months
* workflow: collect -> design -> test -> deploy -> edge device
* move from tensorflow to tensorflow lite
* this is not new, know for 10 years
* but with EI you get C++ code or some linux lib for deployments
* good data, goog modelling, shitty data, shitty modelling ..

## overview over edge impulse studio
* even expert ml engineers can use their studio to pick the proper model, etc.
* has suggestions for boards
* tunig is really unique

### BYOM - bring your own model
* customers wnated to bring their own model
* usable with pip,  used in a notebook
* runs on literllay on any device under the sun
* TODO also try this out

### exmaples
* RAM-1; poer line monitoring application; 
* nordic Thingy:53 is already flashed with EI firmware flashed; you hae an app as well; via the app you can sample, build and deploy the models
* brainchip: as neuromorphic IP, Akida platform; will just sample necessary sensory inputs instead of everything
* cortex m7 is comnig, m55 plus u55 uplift up to 55x faster and 25x less energy for voice sampling
* Alif E will be 22x faster than a RPi with image detection
* Oura (ring) uses also the EI latform to improve their algorithm
* packaging handling: how to make sure packages are handled with care?
* also for non invasice glucose measurment: know labs (apple said later they want to do the same)

* how does EI make money? everything is free; 20 min of compute time, 4 GiByte of data
* SaaS-company; uses AWS in the backend

#--------------- talks from TI and Alif -----------
* check neuromorphic processors
* TODO: check brainchip & mercedes for car overwatch
#------------------- break -------------------------

# sleep stage prediction
* with Oura ring
* previously they collect the data, labelled it manually and then had a gold standard
* later they used the Our ring t collect the data and create a fitting model, which gave the same results
* getting gold standard label data is really hard
  * super expensive, lots of data (both on device and later), multiple sensor, time-alignment issues, requires interaction with research labs
  * idealy: very short feedback loop
* several ways to collect data: amazon S3, google cloud or azure
* first collect data, then set up pipelines, then fetch it
* do someML on it: Sagemaker, notebook, ..
* when doing the ml-engineering, don't focus on the energy consumption - the engineers will compress it
* JAX: google project which can compute python compute into an efficient compute graph
* EON compiler compiles the graph to c++, then it runs on the device
* this shortens the feedback loop
* possible to use h5 models, also onnx, pytorch ..
* EON compiler is fully open source

## Zapotek
* how they struggled to come to such a polished product?
* 2 years ago they created HW-prototypes, tried to integrate teh cloud, because it ws crushing pressure
* so they tried to do it from scratch, inhouse machine learning capabilities: not the way to got
* there is no complete hw ecosystem, sink for time and money, because migrating models and firmware was hard
* this was not the focus: so the oculd not become hardwre and ml-experts at the same time
* so they searched for a partner, who could help with the ML
* first: created a workplace organizer with nvidia jetson
* they simplified the model then, after seeing results with EI
* tried also some recyclable material sorter: bottles, jar, alu can
  * good detection but some problems with milk cartons until they added quickly machine vision
* customers had requests, but did not like answers with "cost money, takes time, .."
* gas detection with the nordic thingy91 for oil platforms
* (all the projects are public, so they can be found on the expert material on the EI page)
* vineyard pest detection: only bugs, not flies

* free to use for prototype
* all major hardware supported
* labeling data is super easy
* retrain and redepoly was fast

## Nordic Semiconductor - Advantages of low power consumption for ML edge devices
* Kristian Kurz
* market leader in Bt and low energy solutions
* Matter over Thread or Wifi: both possile
* devzone.nordicsemi.com as community
* nordic has a special approach: no special AI/ML hardware implemented
  * powerful cpu, helps to do machine learning
* on device processing mackes it possible to process more data and then send just the rsult
* information not data 

## workshop - TI board
* sk-tda4vm board
```
ping 172.20.157.128
```
not working
* use the edgeimpulse network, not the hotel network (clear)..
* goal for today: connect device, collect data, make an impulse, then flash to baord
* mine: marcelpetrick / EdgeImpulseConf_HandOn_TI 
* collect first he data: from the laptop of the current laptop; just needs access via browser
* then "create impulse": create basic image processing, use sqre input, then also generic obejct detection, then save impulse
* yolox for tvi4dm as model
* training can take some time ..
* no visible loss function
* cloned a project: marcelpetrick / Person-Detection-ML-Show-Demo_clone
```
    ~  ssh -oHostKeyAlgorithms=+ssh-rsa root@172.20.157.131                                             255 ✘ 
The authenticity of host '172.20.157.131 (172.20.157.131)' can't be established.
RSA key fingerprint is SHA256:t6pFYc6PUVurkno2Qv6QHoGY3BfwEc43j7sJ0u4n3L4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added '172.20.157.131' (RSA) to the list of known hosts.
root@tda4vm-sk:/opt/edge_ai_apps# 
```
* copy the file via scp to the board: 

```
root@tda4vm-sk:/opt/edge_ai_apps# pwd
/opt/edge_ai_apps
root@tda4vm-sk:/opt/edge_ai_apps# cd 
root@tda4vm-sk:~# cd workshop/ 
root@tda4vm-sk:~/workshop# ls
commands.txt  workshop.eim
root@tda4vm-sk:~/workshop# cat commands.txt 

udhcpc -i wlp1s0

edge-impulse-linux-runner --model-file workshop.eim --force-target runner-linux-aarch64-tda4vm
root@tda4vm-sk:~/workshop# 
```
* on top of the output you can see also an ip adress for the local network; where you can see the stream in your browser, with inference, etc.

#------------------- break -------------------------
## next workshop:
* docu: tinyurl.com/edgeml-workshop
* since the transprent case of the serial.connector does block my second usb-port, I can't continue with the demo :/
* but, connect and power on, then use putty or whatever
* 115200 as speed

#----- end of the session -------
