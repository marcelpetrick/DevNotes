# 20240118 AWS UG at Netlight

* original agenda
```
This time we meet at the Netlight office and get food and drinks provided.

AGENDA:
18:30 - Doors open, networking, drinks, food

19:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

19:45 - Florian Siegel & Pablo Restrepo (Netlight): Gen AI - How to bring Ideas from Paper to Production

20:45 - Richard Träbing (AWS): The AWS Well Architected Framework
```

## First, the intro by Markus about all the changes
* SAP Hana certified: 9 TB of RAM
* Storage: on-demand replication across AWS regions and accounts
   * Helpful for disaster recovery
* ECS and Fargate now integrate with Amazon EBS
* AWS Lambda now scales up to 12 times faster: scaling at the account level, but 300 concurrent executions in the first minute, then 500 concurrent executions per minute afterward
  * Also ClaimedAccountConcurrency
* Database: EMR on EC2 now supported already; Aurora PostgreSQL: integration with Bedrock, so that Amazon Aurora ML exposes ML models as SQL functions
* CloudWatch alarms add AWS Lambda as an alarm state change action
* DevTools: EC2 Instance Connect now supports RHEL, CentOS, and macOS; CodePipeline supports GitLab self-managed; CodeBuild now supports X-large Linux compute type
* CodeDeploy provides zonal deployment for Amazon EC2
* SecretsManager announces a 99.99% SLA per region per month
* Cognito user pools now allow customization of access tokens
* AWS CloudShell now supports Docker in many regions: in the console
* AWS: customer-obsessed; sure there is a customer request for that

### Dates
* AWS Summit May 2024; Gleisdreieck Berlin; still open CfP
* AWS Community Day DACH 17th in Munich, Smartvillage Bogenhausen
* Next meetup AWS UG; February 21 at NTT Data

## 1st talk: genAI - how to bring ideas from paper to production
* Presenters: Pablo Restrepo (salsa dancer, backend, cloud, MLOps, working with NLP for several years), Florian Siegel (always AWS, full-stack cloud developer)
* Question: Can you deduce from a portrait photo of a person if they are a wearer of glasses? <-- check: Can you deduce whether a person wears glasses from their portrait photo?
## What is NLP?
* Sentiment analysis, translation, summarization, named entity recognition, classification, question answering, text generation
* There are so many cool things you could do within your application...

  * History of NLP:
    * The journey starts in the 80s: RNN, LSTM, classic methods, Markov chains (super interesting concepts)
    * Looked cool, did not work: Everything changed when the fire nation attacked... 2017 transformers were proposed
    * NLP was doable and also fast: 2018 brought BERT as a foundational model
    * 2020 GPT-3: end of 2022 ChatGPT: lots of people understood what it can do then everything took off
    TODO: img of Pablo pointing towards the timeline

### NLP nowadays
* Check: article llm-privacy.org
* Drawback: LLMs are really expensive and slow compared to smaller models;
* Nowadays, creating a GenAI POC is super easy; but taking the PoC to production is not so easy...

### Chapter 1
* How to create a PoC
* Start with your values & discover a meaningful idea
* Gather people that are involved in infrastructure, inference, frontend, backend
* Define success metrics
* Ship incrementally and fail fast

### The idea
* Make internal knowledge accessible to internal users and end-users
* Provide fast response times
* Humanlike interactions
* Chatbot on a static webpage, deployed with CDK TypeScript; Python for application code & LangChain, ephemeral environments for development, all components on AWS
* Chatbot architecture
  * Start with your data source; mirror data into an S3 bucket
  * RAG-based application
  * Chunk content
  * Create embeddings
  * Insert into a vector store
TODO image of the chatbot architecture
* Bedrock Titan for embeddings
* Amazon RDS with pgvector extension
* Users were not happy that they had to wait 25s for the first result, then it failed with 50x.. not happy
* Tried to containerize LangChain, 250MB, integrated FASTAPI, Lambda Web adapter
  * Not a solution; startup times became longer; users partially happy
* Several iterations of the architecture, to optimize
* What would have changed today?
  * Raw data -> Amazon Bedrock knowledge base -> OpenSearch Serverless (1 day down to 20 minutes)
  * Hint: shut down the OpenSearch Serverless
  * Testing the models can be done without building any lambda!
  * Bedrock knowledge bases are the foundation for Bedrock agents (TODO check this)

## Productionizing Your Product
* Simplified architecture as abstract: frontend -> LLM powered app -> model -> information retrieval system
* Becoming production ready: human loop (wave function) and prompt layer (cake) <-- check: "wave function" and "cake" seem like placeholders or specific terms
* What is prompt versioning? Can't I use Git? - Yes, you can, but maybe people have problems with Git?
  * Prompt engineer can do experiments without being really tech-savvy
  * Different prompts for different environments
* Adding an answer-safeguarding layer GuardRails for Amazon Bedrock; filter the responses the user should not see
* LLMOps: monitoring, debugging, test, and evaluate - tools like LangSmith; PromptLayer, Weights & Biases
* LangChain: can become quite complex; like chaining or prompt routing -> how to debug: LangSmith - will simplify life a lot (in case of faulty prompts); traces...
* DevOps: CI/CD, automatic testing, security...
* If you want to fine-tune models, then you shift to MLOps: data management, model training, model deployment and inference, model monitoring
* Fine-tuning: you can't remove knowledge by a model; Shakespeare; Juliet; not able to gaslight the model
* Making a model better, like fine-tuning for SQL-output from natural language - this is possible; or speak like how our company does speak
* LLMOps with AWS: TODO add photo
* Amazon Glue to move the data around using those tools is super simple: check Amazon Lambda, CloudWatch, SageMaker...
  * Results come as Jupyter notebooks, which can be used to play around
* If you want to finetune foundation models: no problem, but finetuning your own models - not possible, have to be deployed, serverless not working anymore

### Takeaways
* GenAI allows you to do cool new things and "prompt your way around" - be aware of drawbacks
* You can now fail fast using genAI: AWS allows you to move fast during your PoC
* After the PoC, you will have to think about additional components and LLMOps. Here, AWS can make your life easier

* LangChain as a cool repository of things and ideas: if you need a solution, check LangChain and also what people did with it
  * Not necessarily needed in production
* In September, it was not very well adapted for AWS Bedrock, so using the raw endpoints would have been better; but this is just a hindsight

* note: the 2nd talk will be replaced with a lightning talk due to missing Richard from AWS

# 2nd Talk: How We Made Document Processing 95% Faster with GenAI - Matheus Jacques  (from Netlight)
* 1h preparation only for the talk
* Motivation & scope: AWS fast start client
* Five weeks for the PoC. Goal: Client insurance company trying to optimize the process
* Goal: Enhance the efficiency of question answering and attribute extraction from business documents through generative AI
* Project overview: Develop a proof of concept system to demonstrate the capabilities of our information retrieval system
* Used: LangChain, AWS Bedrock, Anthropic Claude as LLM <-- check: "Anthropic Claude"
* Just to support the agents, not to replace them
* 12 documents: as source; 21 questions; 5 high-priority attributes
* GenAI excels in extracting information from structured texts, such as databases, or documents with clear formatting
* Preprocessing of the PDF documents with MathPix (check this) <-- check: "MathPix"
* Capable of processing text and image-based PDFs
* TODO add images for the PoC idea and the AWS architecture
* Extraction results: either result or some "not available" to prevent hallucinations; this helped a lot; also temperature to zero
* Garbage in, garbage out
* Really small set of documents (12); very similar, some from the 80s, some handwritten - so a lot of dependence on MathPix
* Time required to extract information from documents reduced by 95% compared to the manual process: 120 minutes to 5 minutes
* Processing time: 1-2 days -> 6-12 hours
* Reduced extraction time has 100% trust in results as a prerequisite

### PoC Learnings
* Input consistency: How good was the LaTeX; a consistent input format was crucial for a streamlined and automated information retrieval solution
* Pipeline optimization: Key elements of the pipeline, including input preprocessing, LaTeX splitting, embeddings inference, context retrieval via similarity search, prompting, and post-processing significantly influence outcomes
* Prompt instruction: Effective instruction of prompt, especially given the expressive nature of large language models (LLMs), ensures positive results
* Context matters
