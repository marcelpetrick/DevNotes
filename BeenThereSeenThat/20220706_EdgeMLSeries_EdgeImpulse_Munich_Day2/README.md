# 20220706 EdgeMLSeries EdgeImpulse Munich Day 2

## Where does it make sense to do edge ML projects vs. where not?
[todo: ask for slides]

## Welding quality assessment using sound
* acoustic emission monitoring as an in-process quality method for welding processes - Koen Faes
* welding as most important fabrication technique
* inherently generate defects due to the process complexity
* detected after fabrication
* presence of defects: wasted production time, energy or raw materials; increased production costs, delivery delays; safety consequences
* vital to detect defects as soon as possible: during the production process; to intervene quickly and repair
* weld quality is becoming more important: customer expectation increase
* quality inspection: expensive, time-consuming, selective, done off-line, after production; sometimes not possible in a non-destructive way
### acoustic emission monitoring
* detecting low level sound waves, which are produced during plastic deformation; can be detected using piezo-eletric sensors
* AE source: cracks
* investigation of AEM because of: real-time inspection technique, small sized sensors, cost effective
* AW signal analysis: wave stream data:
[img for AE signal analysis]
  * vast amount of signals captured; AI allows a more efficient analysis
  * AVANGARD-project did this for arc-welding: trying to find correlation between weld- defects and the AEM measurements
  * test-series: tried different welding modes and parameters to gather data
  * another series: fillet welds with pulsed welding
  * recorded sounds: 20 min; converted to spectrograms
  [img]
  * prediction accuracy of 85%: of the used welding condition -> not a direct way to detect defects
  * most important defects: lack of penetration or lack of fusion
  * 20 min of data is quite low for such an analysis -> more data would lead to increased accuracy
  * model accuracy for bead-on-plate welds: 85%; fillet welds: 70%  
  * of course this analysis was done for a certain material and a certain sensor; also the positioning of the sensor has to be "correct" (not too far away)
  * challenge: done in a lab environment - so quite calm, but what about a noisy industrial environment?
* is there something in EdgeImpulse for removing a known ambient noise: no, has to be done as apart of manual preprocessing

## Renesas introduction: what can they do for MPUs and MCUs?
* 21k employees, 1k billion yen revenue 20221
* core markets: automotive, industrial, infrastructure, IoT
* AI building blocks: motion detect, vibration detection, upside down detection, fall detection
  * done by sensor fusion
* you can have the best hardware, but if the ecosystem is not fitting, then you will not go far
* currently they used a translator (DRP-AI) to convert ONX-models to their embedded target -> will provide tooling for EdgeImpulse soon

## Edge Impulse and Nordic Semiconductor: Kevin Kotinkar
* intro: fabless semiconductor companies, focus on low power wireless connectivity; 2.4GHz range, bu also LTE-M
* 1200 employees, 1.5 billion revenue
* 2018: nRF91: first cortex M33 + ARM TrustZzone security
* every BLE device has to be listed: Nordic still with 40% market leader
* synergy:
  * low power edge devices
  * connected devices, analyze data easily with great UX
  * limited development effort
  * R&D costs show that they are more a software company, even when revenue comes from hardware
  * requirement for smartness in energy constrained devices
* classifying images possible (M4 on legacy products), M33 on newer ones - is possible
* air quality, recognizing sounds, audio input
* nRF connect SDK (already used yesterday xD)
* 75% of customers run battery-powered devices
* idea to reduce what you have to send over the air
* nRF9160: voids cellular modules; already certified for use around the world
* nRF connect SDK: based on zephyr RTOS (by Linux foundation)
* scalable SDK: fits single, but also multi-core SoCs
  * one code base and toolchain for nRF52, nRF53, nRF91 series; includes Bluetooth LE, MLE mesh, thread, homekit, matter, zigbee, LTE
  * Visual Studio Code as supported platform; cmake, git ..
  * integrated edgeimpulse support for all boards
* DevKit are mostly nice for testing the cpu, but you have to add sensors
  * more important are the "thingies", which come pre-equipped with sensors
  * Thingy: 52, Thingy:91 and Thingy:53 (some weeks ago); is pre-programmed with firmware to work directly with edgeimpulse-studio; also with smartphone app via bluetooth
  * example runs a ml model for gestures and sending the classification result to a MQTT server
[img of the slide: layout of the board]
  * Thingy 53 has a microphone as well
  * nRF edge impulse App - available via app stores




  


todo:
* check how to send MQTT messages - for data logging
* AWS learning paths .. and certificates



.. wip ..
