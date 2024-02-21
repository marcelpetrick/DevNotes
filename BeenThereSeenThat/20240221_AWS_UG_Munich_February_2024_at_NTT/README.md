# 20240221 AWS UG Munich February 2024

```
Details

"Everything GenAI" is definitely a strong topic of the year 2024. After the first PoC wave in 2023 we're now at a point where we see more and more stories about real world applications. We as the AWS User Group Munich are very happy to have access to knowledgeable speakers who are able to tell us more about those GenAI solutions and how they were built with AWS.

This time we meet at the NTT Data office and thankfully get food and drinks provided.

AGENDA:
18:30 - Doors open, networking, drinks, food

19:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:00 - Fuad Ibrahimov & Michael Loibl (NTT Data): Building Scalable Gen AI RAG Applications with AWS Serverless
Retrieval Augmented Generation (RAG) applications provide valuable opportunities for leveraging the power of Generative AI. However, building enterprise-grade RAG applications can pose significant challenges. Although Amazon Q can offer quick solutions, managing the scale and complexity of such applications often requires more control than Amazon Q can provide. In this talk, we will explore how AWS Serverless services can be utilized to build a robust, scalable architectures that meet the needs of enterprise-grade RAG applications. Join us to learn how to achieve greater innovation and productivity in your RAG applications with AWS Serverless services.

21:00 - Andreas Jadrin (NTT Data): AI Companion: A Serverless Travel Copilot
Do you dream of a travel experience that's effortless and tailored to your every need? With the help of an AI copilot, that reality is closer than you think. Picture a companion providing you with proactive guidance and information while you are focusing on driving. We incorporate an LLM into a serverless application that is able to detect intentions and trigger suitable events in the cloud, resulting in a human-like and user tailored communication/conversation. Our serverless architecture, hosted on AWS employs services such as AWS Lambda, AWS IoT Core, Amazon DynamoDB, Amazon S3, and AWS StepFunctions. Join us as we explore the transformative potential of AI and Cloud and the future of travel.
```

## intro - Markus Ostertag
* Chief AWS TEchnologist @ adesso SE
* 180 announcements since the last meetup
* NTT has an AWS hero in their ranks
* u-9tb1.112xlarge (9 TiB RAM) now available in Stockholm (SAP Hana certified)
* Mac M2 and M2 PRo availalbe in Frankfurt
* attribute based price selection for auto-scaling: based on a percentage (like "I want to save always 40% to the following instances type")
* storage: higher read IOPS for EFS: up to 250k read IOPS for frequently-accessed data
* container: ECS announced managed instance draining for EC2
* Amazon Q data integration in AWS Glue in preview: Q is something like GPT
  * "Woe does not know who Amazon Q ist?" - asked twice
* Finch is AWS's docker; because the docker license has changed; is available n Windows
* IaC generator for CFN and CDK - no more clickops, but not new, because everyone uses Terraform ;)
  * scan current config, then scan, get a template, select template and get IaC for cloud formation
  * pretty huge and cool improvement
* use CodePipeline for Github Actions
* CodeCatalyst is introducing pull request approval rules: like 2 people of this and that team
* SageMaker Automatic Model Tunicn supportsnow Delete API
* next AWS UG event 14.03. AutoScout24
* AWS Community Day DACH: smartville Bogenhausen, 17.09.

## Fuad Ibrahimov & Michael Loibl (NTT Data): Building Scalable Gen AI RAG Applications with AWS Serverless
* Michael: part of the genAI-core-team
* cloud SME - subjectmatterexpert (what is this)
* November 2022 ChatGPT was released, bi hype about genAI started
* they built their own chatbot - GoodGPT
* small frontend: vue.js - backend with LangChain
* next step: RAG application: document intelligence slution to also execute Prompts against private non publicly known documents
* they needed more advanced genAI functionalities
* they needed a document-intelligence tool: GPT is trained with public data, but you want to use your own data
* RAG for retrieval augmented generation:
  * RAG is used for comple and knowledge-intensive tasks
  * RAG is also used for tasks, that are not nown by the LLM
  * external sources are used to obtain specific additional information This information are then added to the prompt.
  * both, te additional nformation as well as the prompt are itself sent to the LLM

### RAG - deep dive
* 1. how to upload private data and documents
* 2. how to use prompt engineering against your private data
* for 1: genAI backend application: split the dpcument
  * what is a word embedding? mathematical impression of text
  * those are put into a highly dimensional vector space
  * semantical closeness for similar things like: apples and banans, because both are fruits
  * the distance between two vectors (embeddings) measures their relationship
* GenAI applied backend: puts the result into the VectorDB: so the indexing was successful
* for 2: document prompting part:
  * VectorDB: cosine-search: determine angle between vectors and fetch them - retrieve similar documents
  * on top of that the prompt is used wth the chat-completion model:
    * LLM is providing now some answer based on the provided (four) results
    * result is sentd back to the frontend
* first you index your private documents (confluence, jira pages, code ..): then prompt engineering against the vectordb

### implementation
* AWS cloud with kubernetes, langchain, python, milvus, ..
TODO add the image ![](img00.png)
* but the result of the first load tests were not so good: two main issues: challenge were the max tokens and also rate-limits
* so big prolems with scalability, limited ressources and cost management
* thinks ike LangChain and LLamaIndex provide already a lots of functionality
* a jupyter notebook works, but not with 2000 employees
* even with load balancing this did not work out

#### first approach
* separate endpoints: fr document upload and the splitting, parsing, ... embedding generation
  * used Weaviate
* RFP file: request for project - how to summarize this?
* why not expand the pipeline, by doing a summary as well? so the summary will be found in the vector-search? good approach - very clever!
* business csalability: how? by adding more fancy indexing and so on ...

### demo time
* the GoodGPT has self-awareness: has access to its own code base?
* really great speed; impressive results and dogfooding for the company - impressive
* uses GPT on Azure as backend for the LLM
* their developer's knowledge has the same value like "before GenAI", because it matters to verfi the result
* chat-completion-models versus embedding-models
* chose openAI because they wanted to go live as fast as possible


## Andreas Jadrin (NTT Data): AI Companion: A Serverless Travel Copilot
TBC



 7
