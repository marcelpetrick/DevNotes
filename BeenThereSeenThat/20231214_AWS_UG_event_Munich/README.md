# 20231214 AWS UG event Munich - AWS re:invent re:cap

```
As every year the AWS User Group Munich ends the year with our infamous AWS re:Invent Highlights meeting!
Please note that due to the expected high amount of content we open doors already at 18:00 and will start the talks at 18:30 this time!

This time we meet at the AWS Office near Odeonsplatz and get food and drinks sponsored by AWS.

For office security please provide your real first and last name during the registration!

AGENDA:
18:00 - Doors open, networking, drinks, food

18:30 - Victor Vedmich (AWS), Markus Ostertag (AWS Hero): re:Invent Highlights

20:00 - Hugo Mineiro (AWS), Daria Aleshkova (AWS): re:Invent Highlights in Database and Analytics

21:00 - Markus Ostertag (AWS Hero): Closing the year
```

## Markus Ostertag: Intro & GenAI-Stack
* Problem with getting back from re:Invent
* Overwhelming with all the different services and things
* Apps that leverage FMs; tools to build with FMs and LLMs, infrastructure for FM training and inference

### Amazon Q
* Amazon Bedrock as a tool to build foundational models
* Adam Selipsky's keynote: Apps which build on FM...
* "Amazon Q": Trained on 17 years of AWS knowledge
  * Assists you wherever you work; the console, IDE, and documentation
  * Works with you to build new features, refactor and troubleshoot on AWS
  * It is also built into all CLI tools - like Clippy from Microsoft Office... can be seen as an annoying popup (hey, you can chat with me)
* Tom sees lots of potential to help people get started; because you have to read tons of documentation to figure out code and architecture, yadda yadda...
* Q has problems with weirdly phrased questions: It should be open-minded; like for asking about running short-lived functions (Lambda), but phrasing it in a way to ask "Is XYZ a good way to run short-lived functions?" - then it might agree
* Helpful to lower the barrier to get started with AWS
* Will get more powerful in the future as well
* ... But you need to log in
* Question if available in Europe? Some say, yes
* Amazon Q is embedded in Code Catalyst
### Code Catalyst can do PR: open them up and solve/review them
  * Some companies have guidelines which prevent this
  * Automatic upgrade of older Java applications is possible
  * Enhance the security and performance of your code
  * Accelerate the migration from Windows to Linux
  * Helpful if you have test-cases you can run on your code afterward
* Amazon Codewhisperer: Support for cloud formation (YAML, JSON), AWS CDK, and HashiCorp Terraform
* Available in Visual Studio (in preview)
* You can open up your private repos to teach Codewhisperer how your company writes code

### Bedrock
* Broad choice of foundational models (not just one - like for OpenAI)
  * Use Claude, Llama2, Stable Diffusion...
* As well as all those Amazon Titan models: Titan Text Embeddings, Titan Text Lite, Titan Text Express, ...Titan Image Generator
* Knowledge bases for Amazon Bedrock: Automatically convert text documents into embeddings
* Store embeddings in your vector database
* Retrieve embeddings and augment prompts
* Agents for Amazon Bedrock
  * Execute multi-step tasks across company systems and data sources
  * Break down and orchestrate tasks and execute API calls on your behalf
  * Securely access and retrieve company data
  * You can instruct the agent to search for specific information just in your local silo, not somewhere else; rest can be retrieved from <wherever>
* As a replacement for LangChain? Yeah, same idea
* Guardrails for Amazon Bedrock: Easily configure harmful content filtering - own rules
* Can be applied to any foundational model or agent
* Redact personally identifiable information (PII) in model responses (coming soon)

#### PartyRock
* Decoupled from AWS
* Influenced by internal tool
* See: partyrock.aws
* App builder -> User interface for input -> Edit the conversation starter
* Nice way to play around with different models
* How to train for the 1 million dollar? Play around with it
* Free (with some credits); log in via Google, Amazon, or Facebook

## AWS Management Console MyApplications
* Monitor and manage costs; health, security posture, and performance of your applications
* Moves away from the pure monitoring view, but gets some trusted advisor recommendations for the applications

## Victor: The Frugal Architect
* FinOps phases: Inform, Optimize, Operate
  * Inform: Visibility & Allocation
  * Optimize .

* Werner Vogels: You build it, you run it. Expanded with "You pay for it" - by Victor
* Billing and cost management combined in one account
* Also: AWS Cost Optimization Hub
* AWS Free Tier Usage API: Enable budget limits to prevent overspending
* Programmatically track free tier usage against monthly usage limits
* Lots of EC2 instances: More than 700
* Graviton4: R8g instances for EC2
* 30% faster than Graviton3... and more sustainable
* Also: AWS Trainium2: Purpose-built chip for generative AI and ML training; coming in 2024; 4 times faster than Trainium
* EC2: P5e instances: Based on NVIDIA H200 Tensor Core GPUs

### AWS Application Composer in VS Code: Drag and drop and connect AWS resources using Visual Studio
* TODO: Try this out
* Just drag the blocks and it adds the configuration!

* Create Cloud Formation based on Git(Hub)
* AWS SDKs for Rust and Kotlin
* Amazon SageMaker Studio Code Editor
* Amazon CodeCatalyst
* Amazon CloudWatch Infrequent Access Class: Half the price than lowest tier until now; best suited for logs that require infrequent querying, e.g., for forensic analysis
* Amazon CloudWatch Application Signals: Like "Golden signals"

[end: left event in the break - missed db-related talk]
