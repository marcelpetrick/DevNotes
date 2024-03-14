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
*if someone is interested, he shall talk to Maria from "talent acquiston - not HR""
*AWS backup restore testing: really cool feature: test the retore on a certain schedule
* who uses .NET on Lambda: obviously nobody
* Eentbridge API destinations calling 3rd party aPIS ina nutshell
* amazon neptune: i/o optimized now GA - zero charges for read and write i/o operations ->  potentilly cost savings
* 99.999% durability - five-nine durability as spoken
* cloudformatio now 40% faster a stack creation
* AI/ML: Bedrock: mistral AI foundation models now GA
  * Anthropic Claude 3 Sonnet model now available

## Sana Shah (Founder AWS Women's UG Berlin & Cloud Operations Lead @ DEMICON): GenAI on AWS - Exploring Amazon Bedrock Knowledge Bases and Agents
* special focus on: bias
* cloud operations lead; at demicon; platform automation..
* why genaI? is so effective; uses pretrained models; use it to increase productivit, automation, ..
* traditional Ml allows to handle only one task on labelled data; but with FM you can adapt to several tasks with unlabelled data
* building a FM (foundation model) bears challenges
  * costs: very expensive
  * clusters of GPU and CPU
  large amount of data: like internet-scale data
  * performance s a problem: inaccurate, unreliable answers, hallucinations
* challenge: biaes and toxicity: without adressing these risks
* for the customization of FMs there ae differenoptons:
  * prompt engineering
  * in context learning? to optimize the output?
  * while picking a model, read the docuentation: best way to interact with the model
  * retrieval augmented generation
  * continued pre-training: more epensive
  * build your own model
* RAG mitigates the problem of lacking actual information; also can be used to use concurrent information

### genAI applications on AWS
* two approaches: Amazon Sagemaker Jumpstart versus Amazon Bedrock
* ML hub with foundation models, built-in algorithsm - verss a Service: fully mananged service to build and scale generative AI application with FMS
* Amazon Bedrock really easy to use:
* amazon bedrock - a signle API call
* Bedrock - build knowledge bases: fully managed support for end-to-end RAG workflow
* securely connect FMs and agents to data sources
* easily retrieve relevant data and augment prompts
* provide source attributions
* workflow: 1. data source -> 2. document chunks - 3. embeddings model -> 4. vector store
* buidl agents with amazon bedrock
* agent action group description, API schema, lambda function
* AMAZON BEDROCK - give it a try: ASAP!
* how to do augmentation:  how to create a knwoledge base?
  * so ver esdy to create a knwoledge base; really easy to create something like this - also can attribute source!!!
* cloud computing has 14% of women in the field; AI has 36, enineering like 20, according to the world economic forum

### risks in GenAI - Bias
* examples for bias in AI:
  * amazon recruitment tool: gender bias
  * google photo misclassification: racial bias
  * compas recidivism prediction: racial bias
* based on data: selectn bias, measurement bias, sample bias, lael bias, observer bias, historical bias
* algorithmic bis: algoithm ias, model bias, interaction bias, confirmation bias

## amazon sagemaker clarify
* will not mitigate bias, just create a report
* shared repsonisiblity model!like always

## conclusion
* data is your differentatior - data strategy is key to any successful AI application
* mitiarting rsisk is your continued rsponsibility
* costs, costs, costs, -> know ROI
* availability of features in regions
* keep learning + trial&error approach
* keep staying informed about trends


## Evelyn Osman & Anastasios Vomvylas (AutoScout24): Scaling k8s services based on custom metrics: From discovery to delivery
* TBC
