# 20240312 Unlocking Edge AI: Advanced Features of Edge Impulse

```
Unlocking Edge AI: Advanced Features of Edge Impulse

Take your edge AI projects and solutions even further with our advanced features workshop. In this webinar, you will learn about the latest, most powerful capabilities of Edge Impulse such as enhanced model tuning and optimization, new deployment options, BYOM (bring your own model), visual anomaly detection, and more. Throughout this workshop, you’ll learn how to manage machine learning for the edge, including data pipelines, signal processing, ML training, model testing, and creating a deployable model that can run efficiently on any edge device, from MCU to MPU to GPU.

Join the workshop, “Unlocking Edge AI: Advanced Features of Edge Impulse”, and learn from Edge Impulse lead engineer Louis Moreau, connect with other developers, and get your questions answered. Register early and get a chance to win a Jetson Nano.

Learn how to:

    Handle complex data pipelines
    Use the latest advanced features of Edge Impulse such as model tuning and optimization, visual anomaly detection, and new deployment options
    Reduce RAM and ROM usage in ML models without sacrificing accuracy or increasing latency
    Deploy ML models to any edge device, gateway, or Docker container

Louis MOREAU Speaker
Lead Engineer, Edge Impulse @ Edge Impulse
Louis started his career developing a low-power and GPS-based IoT solution to protect rhinos in an African conservancy. He is now leading the Developer Relations team at Edge Impulse. When not hacking hardware or automating tasks, you can see him riding an electric skateboard in Lille, northern France, or scuba diving in tropical islands.
```

* Linda Watkins, SVP of Marketing

## notes
* todays tasks
1.  data pipeline
2. model development & optimization
![](img01) TODO

* how familiar are you with EI-pipelines? questionnaire
* example Industrial ML pipeline

## 1. How to automate data pipelines?
* getting gold standard labels is hard - catch errors early
![](img02) TODO
* add a cloud bucket: is a S3 bucket; region, access key, ..
* create organizational database
* validate data: are all files present? do all files start/end at the same time? are all expected labels present?
* advanced checks: correlation between different devices?
* catch errors early
how to do this? use transformation blocks
* preparation of data can be done with a data-pipeline as well
  * their github repo contains data for that as well
* Multi sensor fusion: multi impulse: run two different projects on the same target: how to merge it to the same c++ library:
  * glass breaking sound -> then check the camera image

* training set: wood images - anomaly detection
* check for machinery piece
* EON Tuner search spaces: combine also several parameters to one

## Deployment options
![](img03) TODO
![](img04) TODO
* edgeimpulse cli: EIM or even docker

## announcement
* EON compiler: RAM optimized - save even more RAM
* developed because most customers report that they are RAM-constrained: less RAM -> smaller MCU -> smaller BOM-costs ..
* tradeoff is a higher latency
![](img05) TODO
