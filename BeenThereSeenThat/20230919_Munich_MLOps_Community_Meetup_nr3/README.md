# 20230919 Munich MLOps Community Meetup #3

* Sadiu Bakiu, Cesare Bosi, Diana Artiom
* host: JetBrains Munich

## Agenda
```
18:50 - 19:00 - Opening talk from the host of the event

19:00 - 19:45 - Eric JoAchim Liese: E2E MLOps platform at BSH

19:45 - 20:20 - Saahil Ognawala: Fine-tuning in the Era of Large Models

20:20 - Onwards - Beer, pizza & networking

More about the talks:

    Talk #1: E2E MLOps platform at BSH
    While most companies are now familiar with the requirements of a good DevOps process, the situation is still not on the same level of maturity for end-to-end MLOps processes that are required to train, test, deploy, run, and monitor ML models in production.
    Generally, MLOps can be considered as an extension of DevOps. The same principles that are valid for professional software development, also apply in the context of ML development, but the complexity is much higher.
    For complete reproducibility of the status of an ML product, at least two artifacts are needed in MLOps (versioned code & model), and ideally, versioned data as a third artifact, while in DevOps only one is required (versioned code).
    Additionally, model training and optimization need special tools for experiment tracking. And finally, the behavior of productive models needs to be monitored with new concepts and tools, in contrast to traditional application monitoring.
    To bring our ML use cases faster into production, we designed and implemented a concept for a generic, modular end-to-end platform that provides components for all the necessary steps from initial data preparation, over-training, experiment tracking, testing, deployment, running, and monitoring in production.
    In my talk I want to answer the questions of why we decided to build our own platform as well as how we built it, i.e. I'll give a short overview of the current state of our platform.
    Talk #2: Fine-tuning in the Era of Large Models

About our speakers:

    Eric JoAchim Liese (LinkedIn)
    After receiving his Degree In Mathematics and Computer Science with focus on Machine Learning and AI, Eric worked as a Senior Data Scientist, ML Engineer and Consultant for several years. He designed concepts to automate the development of AI products by creating End-to-End MLOps Pipelines, as well as strategies to help companies to become data- and AI-driven. Before that, he worked as a Software Engineer for over a decade and later as a Lead Developer on many projects.
    Eric is currently a Lead Architect & Advisor for AI & Data, helping BSH to shape a strategy to become a data and AI driven company. His previous responsibilities also encompassed designing Data Lakes of BSH, with his main focus on concepts for automating data ingestion, ETL, data quality, and productionization of ML/AI processes (MLOps) on AWS.
    
    Saahil Ognawala (LinkedIn)
    Saahil Ognawala is Senior Product Manager at Jina AI, a cutting-edge Multimodal AI startup founded in 2020 that has already appeared in Forbes AI30 and CBInsights AI100. Saahil has previously worked as a data scientist and product manager for Munich Re. Prior to that, he finished his M.Sc. and PhD Computer Science at the Technical University of Munich, specializing in deep learning and software engineering.
```

## Sergey from JetBrains
* IDEs, TeamCity, uTrack, ..
* developing currently a tool to run MLOps in the cloud, will be presented next time this event takes place

## Eric Liese - An End-to-End MLOps Platform - Practical experiences
* works for BSH Home Appliances Group; now 100% daughter of Bosch; mission
* Lead Architect and also Advisor and Lecturer
* oven cooking, surface cooking, cooling, dish care, laundry care, small appliances
* all new devices have something like a rapsberry pi: system-master; all devices can be connected to the internet
* one question o answer is maybe: make the device self aware: fridge can answer if you can still eat something
* starting with computer vision; before already cameras in fridge
* they noticed: we need some validation and quality gates: so they needed an MLOps platform
* what is this and why do we need it?
  * why omnipresent if sw engineering?
  * three stages: CI/CD/run
  * reproducibility, teamwork, automated test & deploy, check current status of code; does it work as intended; monitoring when it runs (performance, robustness)
* MLOps:
  * still versioned code, but also versioned model, vesioned data snapshot: three artifacts now
  * logbook for all the experiments which have been run
  * CD: model behaviour and performance, expected predictions on well known data points; concept drift, data drift
  * Run: monitoring, model monitoring
### why did they build their own platform?
* have hterogenous use cases; slow and fast moving data
* images and NLP
* sensor data from IoT, IIoT/I4.0
* flexible and verastile, modular end-to-end-platform
* handling complexity: many code versions on lost jupyter notebooks
* hundreds of users, high turnover (fluctuation) of employees in data science
* ready made platform often not sufficient:
  * black box
  * fast to apply but also reaching ast its limits and often difficult to extend
  * we had to combine mlflow with aporia and benefit from each strengths -> allows to cchange plarts of the platform for better tools (drop in replacement)
  * -> stainyg flexible, no vendor lockin
### how is the platform used?
* 5 stages:
  * process management: freedom to choose libs and tools; ubuntu vms in the cloud, AWS E2 instances ..
  * data ingestion: streaming/batch; storage; best practice: basic quality checks and monitoring (use case agnostic); storage optimizations for faster queries, anonymization/pseudoymization (see also governance: certain type of data can't be stored longer than ten days)
  *  training: model selection, training, evaluation; GPUs/CPUs/TPUs cluster for deep learning
  *  experiment rracking - mlflow
  *  model versioning - mlflow
  *  test&deploy: automated deployment stage; blue/green; automated re-training; one-click-deployment - mlflow; quality & security testing gateway; model compilation containerization - tagret specific deployment
  *  run & serve:  infrastructures and software monitoring; model monitoring (performance/feedback), data drift, generic API for inception, high availabilty; all provided by a secure REST API
  *  governance layer
### practical considerations
* first get a good understanding between current and future demands
*fexibility to replace tools because they grow out of scope fast
* still staying lean, but not planning too far ahead into the future
* fail early/fail fast - start with small PoC and grow continuously
* always look for generic solutions for specific use cases
* reserve time for data governance
### pitfalls
* aoid technology islands to reach quick wins
* tool evaluation is time consuming and expensive, important to do in a structured way
* avoid vendor lock-ins

![](img03?)
* about the islands: better a general solution with 20% overhead instead of 3 times 100%
* data science teams are very close to the application, centralised data lake
* in the beginning 2 people, now 10-15 for the whole company; maybe 120 engineers worldwide dealing with it
* AWS ECS platform for the containers
* maybe every si month a release until now (aiflow, aporia, ..) - but with LLMs it can drastically change
* 2 years ago some sentiment analysis: talk about differnt products in social media
* goal: models on edge devices
* octoml - shrink the models
* or nvidia: shrink and pooling; as different approach
* 

