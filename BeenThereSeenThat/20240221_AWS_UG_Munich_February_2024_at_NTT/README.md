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
*


## Andreas Jadrin (NTT Data): AI Companion: A Serverless Travel Copilot
TBC



 7
