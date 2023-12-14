# 20231214 AWS UG event Munich - AWS re:invent re:cap

* TODO add the meetup description
* Tom, victor (I talked to); karim, ovi (?)

## Ostermann: intro & genAI-stacl
* problem with getting back from re:invent
* overwhelming with all the differnt services and things
* apps that leverage FMs; tools to build with FMS and LLMs, infrastrcuture for FM training an infernece

### Amazon Q
* amazon bedrock as tool to build foundational models
* adam selipskises keynote: apps which build on FM ..
* "Amazon Q": trained on 17 years of AWS knowledge
  * assists you whereever you work; the console, IDE and documentation
  * works with you to build new features, refactor and trobuleshot on AWS
  * it is also built in into all CLI tools - like Karl Klammer .. can be seen as annoying popup (hey, you can chat with me)
* Tom sees lots of potential to helppeople to get started; because you have to read tons of documentation to figure out with code and architecture, yadda yadda ..
* Q has problems with weirdly phrased questions: it should be open minded; like for asking for running short lived functions (Lambda), but ohrasing it in a way to ask "is XYZ a good way to run short lived functions?" - then it might agree
* helpful to lower the barrier to get started with AWS
* willl get more powerful in the futre as well
* .. but you need to log in
* question if afailable in europe? some say, yes
* Amazon Q is embedded n Code Catalyst
### code catalyst can do PR: open them up and solve/review them
  * some companies have guidelines which prevent this
  * automatic upgrade of older Java applications is possible
  * enhance the security and performance of your code
  * accelerate the mgiration from Windows to Linux
  * helpful if you have test-cases you can run on your code afterwards
* amazon codewhisperer: support for cloud formation (yaml, json), AWS CDK and hashicorp terraform
* available in visual studio (in preview)
* you can open up your private repos to teach codewhisperer how your company writes code

### bedrock
* broad choice of foundation models (not just one -like for openAI)
  * use claude, llama2,stable diffusion, ..
* as well as all those Amazon Titan models: titan text embeddings, titan text lite, titatn text express, ...titan image generator
* knwoledge bases for amazon bedrock: automatically convert text documents into embeddings
* store embeddings in your vector database
* retrieve embeddings and augment prompts
* agents for amazon bedrock
  * execute multi-step tasks across company systems and data sources
  * break down and orchestra tasks and execute API calls on your behalf
  * securely access and retrieve company data
  * you cn instruct the agent to search for specific information just in your locaol silo, not somewhere else; rest can be retrieved from <whereever>
* as replacement for LangChain? yeah, same idea
* guardrails for Amazon Bedrock: easily configure harmful content filtering - own rules
* can be applied to any foundation model or agent
* redact personally identifiable information (PII) in model responses (coming soon)

#### PartyRock
* decoupled from AWS
* influenced by internal tool
* see: partyrock.aws
* app builder -> user interface for input -> edit the conversation starter
* nice way to play around with different models
* hot to train for the 1 mio dollar? play around with it
* free (with some credits); log in via google, amazon or facebook

## AWS Management Console myAplications
* monitor and manage costs; health, security posture, and perfrmance of your applications
* moves away from the pure monitoring view, but get some trusted advisor recommendations for the applications

## Victor: the frugal architect
* FinOps phaes: inform, optimize, operate
  * inform: visbility & allocation
  * optimize .

* Werner Vogel: You build it, you run it. Expanded with "you pay for it" - by victor
* billing and cost management combined n one account
* also: AWS cost optimization hub
* AWS free tier usage API: enable budget limits to prevent overspending
* programmatically track free tier usage against monthly usage limits
* lots of EC2 isntances: more than 700
* graviton4: R8g instances for EC2
* 30% faster than graviton3 .. and more sustainable
* also: AWS Trainium2: purpose-built chip for generative AI and ML training; coming in 2024; 4 times faster than tRainium
* EC2: P5e instances: based on nvidia H200 tensor core GPUs

### AWS application composer in VS code: drag and drop and connect AWS ressources using visual studio
* TODO: try this out
* just drag the blocks and it adds the configuration!

* create cloud formation based on git(hub)
* AWS SDKs for Rust and Kotlin
* Amazon SageMaker Studo Code Editor
* Amazon CodeCatalyst
* Amazon cloudwatch infrequent access class: half the price than lowest tier until now; best suited fr logs that require infrequent querying, e.g. for forensic analysis
* Amazon CloudWatc Application Signals: like "Golden signals"
