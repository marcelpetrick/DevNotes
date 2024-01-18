# 20240118 AWS UG at neglght

## first the intro by markus about all the changes
*  SAP Hana certified: 9 TB of RAM
* Storage: on demand replication across AWS regions and accounts
   * helpful for desaster recovery
* ECS and fargate now integrate with Aamzon EBS
* AWS lambda now scales up t 12times faster: scaling at account level, but 300 concurrent executions in the first minute, then 500 concurren executions per minute afterwards
  * also ClaiemdAccountConcurrency
* database: EMR on EC2 now supports already; Aurora PostgreSWL: integration with Bedrock, so that Amazon Aurora ML exposes ML models as SQL functions
* CloudWatch alarms adds AWS Lambda as an alarm state change action
* DevTools: EC2 Instance Connect supports now RHEL, CentOs and macOS, CodePieplne supports GitLab self-managed; CodeBuild now support X-large Linux compute type
* CodeDeploy provides zonal deployment for Amazon EC2
* SecretsManaer announces a 99,99% SLA per region per month
* Cognito user pools allows now to customize access tokens
* AWS CloudShell now supports Dockerin many regions: in the console
* AWS: customer-obsessed; sure there is a customer request for that

### dates
* AWS Summit May 2024; Gleisdreieck Berlin; still open CfP
* AWS Community Day DACH 17th in Munich, smartvillage Bogenhausen
* next meetup AWS UG; 21.02. at NTT Data

## 1st talk: genAI - how to bring ideas from paper to production
* presenters: pablo restrepo (salsa dancer, backend, cloud, mlops, working wth NLPfor several years), florian siegel (always AWS, fullstack cloud developer)
* question: can you deduce from a portrait photo of a person if they are waerer of glasses?
## what is NLP?
* sentiment analysis, translation, summariziation, manemd entitiy recognition, classification question answerring, text eneration
* there are so many cool things you could do within your application ..

* history of NLP:
  * journey starts in he 80s: RNN, LSTM, classic methods,markov chains (super intereting concepts)
  * looked cool, did not work: everything changed when the fire nation attacked ... 2017 transformers were proposed
  * NLP was doable and also fast: 2018 brought BERT as foundational model
  * 2020 GPT-3: end of 2022 ChatGPT: lots of people understood what it can do then everyting took off
  TODO: img of pablo poiting towards teh timeline

### nlp nowadays
* check: article llm-privacy.org
* drawback: LLMs are really expensive and slow compared to smaller models;
* nowadays creating a GenAI POC is super easy; but taking the PoC to production is not so easy ..

### chapter 1
* how to create a PoC
* start with  your values& discover a meaningful idea
* gather people that are involvedin infrastrucure, nferecen, frontend, backend
* define success metrics
* ship incrementally and fail fast

### the idea
* make internal knowledege accesible to: intenralusers and end users
* provide fast response times
* humanlike interactions
* chatbot on static webpage, deployed with CDK tpescript; python for application code &langchain, ephermeral environemtns for development, all components on AWS
* chatbot architecture
  * start with xour data source; mirror data into an S3 bucket
  * RAG-based application
  * chunk content
  * create embeddings
  * insert intovector store
TODO image of the chatbot architecture
* bedrock titan for embeddings
* Amazon RDS with pgvector extension
* users were not happy that they had to wait 25s for the first result, then it failed with 50x .. not happy
* tried to containerize LangChain, 250MByte, integrated FASTAPI, Lambda Web adapter
  * not a solution; startup times became loner; users partially happy
*  several iterations of the architecture, to optimize
* what would have changed toda?
  *  raw data -> amazon bedrck knowledge base -> open search serverless (1 day down to 20 minutes)
  * hint: shut down the opean search serverless
  * testing the models can be done wthpub building any lambda!
  * bedrock knowlege bases are the foundation for bedrock agents (TODO check this)

### productionizing your product
* simplea arhitecture as abstract: frontend -> LLM powered app -> model -> informaton retrieval system
* becoming production ready: human loop (wave function9 and prmptlayer (cake)
* what is prompt versioning? can't i use git - yes, can, but maybe people have problems with git?
  * prompt engineer can do experiements withut being really tech-savvy
  * different prompts for different environments
* adding a answer-safeguarding-layer GuardRails for Amazon Bedrck; filter teh tresponses the user should not see
* LLMOps: monitoring, debugging, test and evalute - tools like LangSmith; PromptLayer, Weights&Biases
* LangChain: can be become quite complex; like chaining or prompt ruting -> hwo to debug: LangSmith - will simplify life a lot (in case of faulty prompts); traces ..
* DevOps: CI/CD, Automatic teting, Security ..
* if you want to fine-tune models, tehn you shift to MLOps: data management, model training, model deployment and inference, model monitoring
* fine-tuning: you can't remove knwoledge by a model; shakespeare; juliet; not able to gaslight the model
* makin a model better, like fun-tuning for swl-output from natural langue - this is possible; or speaklike how our company does speak
* LLMOps with AWS: TODO add photo
* Amazon Glue to move the data around using those tools is super simple: check Amazon Lambda, cloudwatch, Sagemaker, ..
  * results come as jupyter notebooks, which can be used to play around
* if you want to finetune foundation models: no proble, but finetuning your own models - not possible, have to be deployed, serverless not working anymore

### take awys
* genAI allows ou to do coll new things and "prompt your way around" - be aware of drawbak
* you can now fail fast using genai: AWS allows you to move fast during your PoC
* after the poc you will have to think about additional compoentns and llmops. Here, AWS can make your life easier

* LangChain as a cool repository of things and ideas: if you need a solution, heck langchain and also what people did with it
  * not necessarily needed in production
* in September it was not very well adapted for AWS bedrock, so using the raw endpoints would have been better; but this is just a hndsight

* 2nd talk will be replaced with a  lightning talk due to missing Richard from AWS

# 2nd talk: How we made document processing 955 faster with genai - Matesuz (from netlight)
* 1h preparation only for the talk
* motivation & scope: aws fast start client
* five weeks for the POC.goal:cleint isurance company trying to optimize te process
* goal: enhance the efficency of questions answering and attribute extraction from usiness document thogh gernative ai
* project overview: develop a proof of concept system to demonstrat teh caparbilits of our information retrieval system
* used: langchain, AWS bedrock, anthripic claude as llm
*just to support the agents, not to replace them
* 12 documents: as source; 21 questions; 5 high-prio attributes
* genAI excels in extracting information from structured tets, such as databased, or document swit clear fomatting
* preprocessing of the PDF documents with MAthPix (heck this)
* capable of processing text an dimage based PDFs
* TODO add images for the POC idea and the AWS architecture
* extraction results: either result or some "not available" to prevnt hallucinations; this helped a lot; also temperature to zero
*  garbage in, garbage out
* really small set of document (12); very similar, some from the 80s, some handwritten - so a lot of dependance on mathpix
* time required to extract information form documents reduced by 95% compared to the manual process: 120 minutes to 5 minutees
* processing time: 1-2 days -> 6-12 hours
* reduced extraction time has 100% trust n results as a prerequiste

### poc learnings
* input consistency: how good was the latex; a consistent input format was crcial for a stremalined and automated information retrieval solution
* pipeline optimization: key elements of the pipeline, including input preporcessing, latex splitting, embeddings inference, context retrieval via similarity search, prompng, and post processing signiantly influnece outcomes
* prompt instruction: effective instruction of promp, especially given the expressive nature of large lnauge models (LMS), ensures ositen results
* context matters
