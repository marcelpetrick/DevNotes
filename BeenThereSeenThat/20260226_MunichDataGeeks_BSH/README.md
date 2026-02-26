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

* development wih v modell, system engineering approach

## 1st talk: Philip Koene and Saif Addin Ellafi - AI-Assisted Requirements Engineering
* v modell: drecrease project risk and ost by increasing efficiency and quality
majaority of stm engineering has to do with language artifacts
* application of genai support thgouhout the v model workflow withing and across proces steps
* funding oproject by the bavarian state: BayTp plus
* rais workstreams: providing sstem context to individual workflow steps; ai angets for inteface between proces steps
* multi agent ssystem
chatbots as system engineer companion
multi model approach with crss verification
* requirements emanagenet: basis for systems engineering, syntxa chek, smenatic cuqlait check of single requirements, correctness of requirements in system context, generation of requirements from project ressources
* software develoet: genertion of embeddd source code; api generation, testcode generation, ai supported code anylsis and bugfixing, genertion of docue documentation, bsh knowledge base generation, automated translation of gui texts

* expectations: indeitification and automation of re-curring and time consuming tsks
* expected productivity gains n alle workstreams
higher quality of producted outcome in all worksteams
* fewer errors in requirements
 more comlete requirements
 
 * raise RM: requirements with strcit syntax
 * iming for intersubjhective comprehensibility
 
  write and then review by some other requirements engineer
  * s the right nomenclature used, keywords used, snetence conxstruon, preconditions, spelling errors, passive versus active voice
  * done witha quick web frontend
  
  * also check against clarift, atomicit, completeness, itnernal consistency, ambiguit, verificabilot, quantifiabiity, unspecific on implementation, .. to refine individual items and improve the overall count
  * requirement context quality check: consistency, completeness, correctness, feasibility..
  * vounsws refinement loop: for ssntax check. if after five runs this is not fitting, then something else is wrong. after two or three reruns is wrong so it vannot be fixed
  * polarion as authoring tool, apache velocity, java and js
  * but polarion database is mirrored, thne some vector db is done. also the topic of data security; need to know priciple - is not helpful for the llm use cases
  * runs on backend ai platform
  
  * zaid as next presenter; barbara ammer as writer of the next slides?
  * why a central ai  platform in bsh?
  * ai platform globally: a governance model for service
  * onboard a product/team to cdl
  * review of the user asses srequest processes and automatized them
  * focus on the steps which bring value
  * standardizing is hard
  * POCs are fast, see vibecoding
  * but when this is proofed and then wanted, how to do this: 
  * cant afford mistakes like user is asked to press buttons which dont exist
  * RAGs are on way to handle this; semantinc chunking, but has to e standardize
  * doing rag for each department would make them automatically unprofitable! wow
  * standard rag boilerplate
  * need traceabilitx, because thex need accountability!
  * RAG ingestion..
  getting data AI ready ..
  * model routing handled by gateway: stay flexible; liteLLM as key
  * one key, zhis then provided to proper handling - check that litellm
  * speed is key
  * their solution: a single, secure, and compliant entry point for all llms
  *observability: define scope, build golden data dataset; set evalatuon metrics, evaluate during development, monitor post-deployment; continuous improvement loop
  * promtflow . not langsmith anymore
  * guardrails control wht comes in and out of the llm models, to filer and deflect invalid user requeets
  * lots of examples for used tools. but based on platform engineering


## 2nd talk: Patricia Goldberg - From Chaos to Control Automating BI Tools with Pydantic and Python
* from brazil
works at wmeolo: simplified setp: personio, python then some outout, python adn dachs, achsa?
* everyone in the comoany has access for self handling services: metabase is used
  * business intelligence tool and also self service analytics
* why need automatic governance: automatic permission system: give permission to users according totheir position at any point in time
* documentation snschronization; version controlled yml file
* names change, ideas change of the column, etc.
* daxter? as scheduler for python - have to check, looks like a blue octopus

* baRBARA AMMER as orgnizer, at least appeared in the talk slides from first presentation; and she arranged things, good.
