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

## Notes
* Today's tasks
1. Data pipeline
2. Model development & optimization
![](img01) TODO

* How familiar are you with EI-pipelines? Questionnaire
* Example Industrial ML pipeline

### 1. How to automate data pipelines?
* Getting gold standard labels is hard - catch errors early
![](img02) TODO
* Add a cloud bucket: it's an S3 bucket; region, access key, ...
* Create organizational database
* Validate data: Are all files present? Do all files start/end at the same time? Are all expected labels present?
* Advanced checks: correlation between different devices?
* Catch errors early
How to do this? Use transformation blocks
* Preparation of data can be done with a data pipeline as well
  * Their GitHub repo contains data for that as well
* Multi-sensor fusion: multi-impulse: run two different projects on the same target: how to merge it to the same C++ library:
  * Glass breaking sound -> then check the camera image

* Training set: wood images - anomaly detection
* Check for machinery piece
* EON Tuner search spaces: combine also several parameters to one

## Deployment Options
![](img03) TODO
![](img04) TODO
* Edge Impulse CLI: EIM or even Docker

## Announcement
* EON compiler: RAM optimized - save even more RAM
* Developed because most customers report that they are RAM-constrained: less RAM -> smaller MCU -> smaller BOM costs...
* Tradeoff is a higher latency
![](img05) TODO
