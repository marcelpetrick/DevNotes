# 20240314 AWS UG Munich March 2024 @ AutoScout24

```
AWS UG Munich March 2024
AWS UG Munich March 2024
Details

Connecting diverse people is core of what we're doing at AWS User Group Munich and so we couldn't ask for a better speaker line-up for the March event right after the International Women's Day (March 8th 2024)!

This time we meet at the AutoScout24 office and thankfully get food and drinks provided.

AGENDA:
18:30 - Doors open, networking, drinks, food

19:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:00 - Sana Shah (Founder AWS Women's UG Berlin & Cloud Operations Lead @ DEMICON): GenAI on AWS - Exploring Amazon Bedrock Knowledge Bases and Agents

21:00 - Evelyn Osman & Anastasios Vomvylas (AutoScout24): Scaling k8s services based on custom metrics: From discovery to delivery

21:45 - More drinks, more networking
-----
If you have an office or co-working space where we can meet (100-150 people), want to sponsor drinks/food or have a (lightning) talk you want to present - please let us know!

Everyone who participates in an AWS UG Munich event must adhere to the Code of Conduct!
```

## Markus Ostertag (AWS Hero): Recent AWS announcements
* if someone is interested, they shall talk to Maria from "talent acquisition - not HR"
* AWS backup restore testing: really cool feature: test the restore on a certain schedule
* Who uses .NET on Lambda: obviously nobody
* EventBridge API destinations calling 3rd party APIs in a nutshell
* Amazon Neptune: I/O optimized now GA - zero charges for read and write I/O operations -> potentially cost savings
* 99.999% durability - five-nine durability as spoken
* CloudFormation now 40% faster at stack creation
* AI/ML: Bedrock: Mistral AI foundation models now GA
  * Anthropic Claude 3 Sonnet model now available

## Sana Shah (Founder AWS Women's UG Berlin & Cloud Operations Lead @ DEMICON): GenAI on AWS - Exploring Amazon Bedrock Knowledge Bases and Agents
* Special focus on: bias
* Cloud Operations Lead at Demicon; platform automation..
* Why GenAI is so effective; uses pretrained models; use it to increase productivity, automation, ..
* Traditional ML allows handling only one task on labelled data; but with FM you can adapt to several tasks with unlabelled data
* Building a FM (foundation model) bears challenges
  * Costs: very expensive
  * Clusters of GPU and CPU
  * Large amount of data: like internet-scale data
  * Performance is a problem: inaccurate, unreliable answers, hallucinations
* Challenge: biases and toxicity: without addressing these risks
* For the customization of FMs there are different options:
  * Prompt engineering
  * In-context learning? to optimize the output? <-- check: in-context learning
  * While picking a model, read the documentation: best way to interact with the model
  * Retrieval augmented generation
  * Continued pre-training: more expensive
  * Build your own model
* RAG mitigates the problem of lacking actual information; also can be used to use concurrent information

### GenAI applications on AWS
* Two approaches: Amazon SageMaker Jumpstart versus Amazon Bedrock
* ML hub with foundation models, built-in algorithms - versus a Service: fully managed service to build and scale generative AI application with FMs
* Amazon Bedrock really easy to use:
* Amazon Bedrock - a single API call
* Bedrock - build knowledge bases: fully managed support for end-to-end RAG workflow
* Securely connect FMs and agents to data sources
* Easily retrieve relevant data and augment prompts
* Provide source attributions
* Workflow: 1. data source -> 2. document chunks - 3. embeddings model -> 4. vector store
* Build agents with Amazon Bedrock
* Agent action group description, API schema, lambda function
* AMAZON BEDROCK - give it a try: ASAP!
* How to do augmentation: how to create a knowledge base?
  * So very easy to create a knowledge base; really easy to create something like this - also can attribute source!!!
* Cloud computing has 14% of women in the field; AI has 36%, engineering like 20%, according to the World Economic Forum

### Risks in GenAI - Bias
* Examples for bias in AI:
  * Amazon recruitment tool: gender bias
  * Google photo misclassification: racial bias
  * COMPAS recidivism prediction: racial bias
* Based on data: selection bias, measurement bias, sample bias, label bias, observer bias, historical bias
* Algorithmic bias: algorithm bias, model bias, interaction bias, confirmation bias

## Amazon SageMaker Clarify
* Will not mitigate bias, just create a report
* Shared responsibility model! Like always

## Conclusion
* Data is your differentiator - data strategy is key to any successful AI application
* Mitigating risk is your continued responsibility
* Costs, costs, costs, -> know ROI
* Availability of features in regions
* Keep learning + trial & error approach
* Keep staying informed about trends

## Evelyn Osman & Anastasios Vomvylas (AutoScout24): Scaling k8s services based on custom metrics: From discovery to delivery
* Not watched - left early
