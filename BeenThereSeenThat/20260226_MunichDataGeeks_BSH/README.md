# 20260226 Munich Data Geeks - BSH

```
Munich Datageeks February Edition

Veranstaltet von Torsten S. und 3 weitere

Munich Datageeks e.V. . ist ein Super-Organisator
Photo of Munich Datageeks group
Munich Datageeks
4.7
1.973 Bewertungen
Details

We are thrilled to announce our next Meetup on February 26th at BSH Hausgeräte GmbH.

Please bring a valid ID card or Lichtbildausweis(some id with a photo like driving license) due to BSH location restriction guidelines!

Format:

    2 talks (each ca. 40 min incl. discussion)
    Time for networking + food + drinks before, in between, and after the presentations
    Talks are held in English
    We will be taking photos and/or film footage at the event. These will be used to share news about our meetups and to publicize upcoming events.

The lineup:
First talk:

Philip Koene and Saif Addin Ellafi - AI-Assisted Requirements Engineering

Abstract:
This talk outlines usecases and methods to improve requirements engineering processes through LLM integration. It focuses on enhancing quality and efficiency through automated syntactic and semantic quality checks, semantic similarity analysis and requirements generation. The goal is to reduce manual effort and build a reliable requirements baseline, while also addressing the challenges of integration into existing corporate processes and toolchains.

Bio :
Saif Addin Ellafi is currently a Technical Product Manager of the AI Platform at BSH, to support internal global BSH stakeholders for the development of machine learning and AI related use cases. My background is in Data Engineering and Data Science, generally working as a bridge between business needs and technical requirements.
Bio:
Philip Koene is currently the project lead of the funding project RAISE, where the recent advances in language generation through LLMs is applied to the systems-engineering process at BSH to increase its productivity and output quality. My background is Systems Engineering and Human Machine Interaction, working also as the owner of the technology field HMI, a network of specialists across BSH and Bosch Corporate Research that collaborate to drive HMI strategy and extend their knowledge of interaction technologies.

Second Talk:

Patricia Goldberg - From Chaos to Control Automating BI Tools with Pydantic and Python

Abstract:
Maintaining Business Intelligent Tool (BI) governance, managing permissions, syncing documentation, and handling schema changes, can be chaotic. This talk explores how Python, Pydantic, and smart design patterns automate these tasks, ensuring seamless BI tool governance. Learn how to auto-sync table metadata, adjust queries on column renames, and enforce permissions effortlessly. With real-world examples, discover how to transform BI maintenance from a headache into a streamlined, automated process

Bio:
Patricia Goldberg is a Data Engineer based in Munich, passionate about data and technology. She has actively advocated for women in tech since 2017, participating in groups like Women in CS@TUM and Female Tech Leaders. She holds a bachelor's degree in Information Systems from the University of Sao Paulo and a master's degree in Data Engineering and Analytics from the Technical University of Munich. Patricia is currently an Analytics Engineer at Wemolo.
```

-------

* development with V-Model, systems engineering approach

## 1st Talk: Philip Koene and Saif Addin Ellafi - AI-Assisted Requirements Engineering

* V-Model: decrease project risk and cost by increasing efficiency and quality  
* majority of systems engineering has to do with language artifacts  
* application of GenAI support throughout the V-Model workflow within and across process steps  
* funding project by the Bavarian state: BayTP Plus <-- check: BayTP+  
* RAISE workstreams: providing system context to individual workflow steps; AI agents as interface between process steps  
* multi-agent system  
  * chatbots as system engineering companions  
  * multi-model approach with cross-verification  

* requirements management: basis for systems engineering  
  * syntax check  
  * semantic quality check of single requirements  
  * correctness of requirements in system context  
  * generation of requirements from project resources  

* software development  
  * generation of embedded source code  
  * API generation  
  * test code generation  
  * AI-supported code analysis and bug fixing  
  * generation of documentation  
  * BSH knowledge base generation  
  * automated translation of GUI texts  

* expectations  
  * identification and automation of recurring and time-consuming tasks  
  * expected productivity gains in all workstreams  
  * higher quality of produced outcomes in all workstreams  
  * fewer errors in requirements  
  * more complete requirements  

* RAISE RM: requirements with strict syntax  
* aiming for intersubjective comprehensibility  

  * write and then review by another requirements engineer  
  * is the right nomenclature used, keywords used, sentence construction, preconditions, spelling errors, passive versus active voice  
  * done with a quick web frontend  

  * also check against clarity, atomicity, completeness, internal consistency, ambiguity, verifiability, quantifiability, and being unspecific on implementation to refine individual items and improve the overall count  
  * requirement context quality check: consistency, completeness, correctness, feasibility  
  * continuous refinement loop for syntax check: if after five runs this is not fitting, then something else is wrong; after two or three reruns, if it is still wrong, it cannot be fixed automatically  
  * Polarion as authoring tool, Apache Velocity, Java and JS  
  * Polarion database is mirrored, then a vector DB is created; topic of data security; need-to-know principle is not helpful for LLM use cases  
  * runs on backend AI platform  

  * Zaid as next presenter <-- check: Saif Addin Ellafi?  
  * Barbara Ammer as writer of the next slides <-- check  
  * why a central AI platform in BSH  
  * AI platform globally: a governance model for services  
  * onboard a product/team to CDL <-- check: Corporate Data Lake?  
  * review of user access request processes and automation  
  * focus on the steps which bring value  
  * standardizing is hard  
  * POCs are fast, see vibe coding <-- check: vibe coding  
  * but once this is proven and then wanted in production, how to do this  
  * cannot afford mistakes like users being asked to press buttons which do not exist  
  * RAGs are on the way to handle this; semantic chunking, but it has to be standardized  
  * doing RAG for each department would make them automatically unprofitable  
  * standard RAG boilerplate  
  * need traceability because they need accountability  
  * RAG ingestion  
  * getting data AI-ready  

  * model routing handled by gateway: stay flexible; LiteLLM as key  
  * one key, which is then provided to proper handling  
  * speed is key  
  * their solution: a single, secure, and compliant entry point for all LLMs  
  * observability  
    * define scope  
    * build golden dataset  
    * set evaluation metrics  
    * evaluate during development  
    * monitor post-deployment  
    * continuous improvement loop  
  * Promptflow, not LangSmith anymore  
  * guardrails control what comes in and out of the LLM models, to filter and deflect invalid user requests  
  * lots of examples of used tools, based on platform engineering  


## 2nd Talk: Patricia Goldberg - From Chaos to Control: Automating BI Tools with Pydantic and Python

* from Brazil  
* works at Wemolo  
  * simplified setup: Personio, Python, then some output, Python and DAX <-- check: DAX?   Dagster? Daxter?!?
* everyone in the company has access for self-handling services: Metabase is used  
  * business intelligence tool and also self-service analytics  

* why automatic governance is needed  
  * automatic permission system: give permissions to users according to their position at any point in time  
  * documentation synchronization; version-controlled YAML file  
  * names change, column names change, ideas change  

* Dagster as scheduler for Python <-- check: Dagster  
  * looks like a blue octopus  

* Barbara Ammer as organizer, appeared in the slides of the first presentation and arranged things  
