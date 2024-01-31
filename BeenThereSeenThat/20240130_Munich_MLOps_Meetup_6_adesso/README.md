# 20240130 Munich MLOps Community Meetup #6 @ adesso

```
Details

Hello, fellow MLOps Engineers and ML Enthusiasts, and happy new year!

We're announcing our next meetup event - we're back for our first one in 2024 on Tuesday, January 30th at 18:30, at adesso office spaces (close to Leuchtenbergring S-Bahn station).
This time we'll hear from Saumya and Stefan about their experiences with open-source tools and models - from optimizing advanced Machine Learning pipelines to LLM fine-tuning with concrete examples based on NVIDIA HGX™ H100 and Intel Gaudi2 accelerators!

Full agenda announced:

18:30 - 18:50 - Beers & Networking
18:50 - 19:00 - Opening talk from the host of the event - Sashel Niles Gruber, Competence Center Manager at adesso
19:00 - 19:40 - Talk #1: Leveraging Open Source Tools for Advanced Machine Learning Pipelines - Saumya Goyal, MLOps Engineer extending consultancy to BSH
19:40 - 20:20 - Talk #2: Unleashing Humor with AI: MemeGPT - Fine-Tuning LLMs for Meme Generation using NVIDIA HGX™ H100 and Intel Gaudi2 - Stefan Ojanen, Director of Product Management at Genesis Cloud
20:20 - Onwards - Beer, food & networking

More about the talks:

    Speaker #1:
    Saumya Goyal, MLOps Engineer extending consultancy to BSH (LinkedIn)
    Title:
    Leveraging Open Source Tools for Advanced Machine Learning Pipelines
    Description:
    Immerse yourself in a dynamic presentation centered around optimizing the Machine Learning project pipeline through the strategic utilization of open-source tools. Our discussion will traverse the landscape of seamlessly integrating diverse tools to construct an efficient and streamlined machine learning development pipeline.
    Key Points:
    Open Source Mastery: Explore the pivotal role of open-source tools in revolutionizing the Machine Learning ecosystem, unlocking new dimensions of efficiency and innovation.
    Tool Showcase: Delve into the specifics of LabelStudio, a powerhouse for labeling, and Voxel51, a key player in Explainable AI. Uncover their functionalities and understand how they contribute to elevating your ML projects.
    Enterprise Deployment: Gain insights into the deployment intricacies of these tools at an enterprise level on cloud platforms. Witness firsthand how scalability and performance are optimized in a cloud-centric environment.
    Crafting Cloud-Agnostic Pipelines: Learn the technical art of constructing cloud-agnostic pipelines, offering flexibility and freedom from vendor lock-ins. Explore strategies to ensure your ML pipeline remains adaptable across various cloud platforms.

    Speaker #2:
    Stefan Ojanen, Director of Product Management at Genesis Cloud (LinkedIn)
    Title:
    Unleashing Humor with AI: MemeGPT - Fine-Tuning LLMs for Meme Generation using NVIDIA HGX™ H100 and Intel Gaudi2
    Description:
    Join Stefan in a captivating journey through the realm of AI-driven meme generation. In this talk, we explore the intricacies of developing a custom Large Language Model specifically for creating humoristic memes. Gain firsthand knowledge on fine-tuning an open-source LLM using cutting-edge NVIDIA HGX™ H100 and Intel Gaudi2 accelerators. This exploration includes understanding Parameter-Efficient Fine-Tuning (PEFT) methods like LoRa and QLoRa, integral to enhancing the model's capabilities. We'll delve into the linguistic challenges and the humor elements that make memes so appealing and relatable. The session offers an in-depth look at how advanced technologies, linguistic understanding, and innovative methods converge to create engaging, humorous content.
    Key Points:
    Build and Fine-Tune LLMs: Learn to construct and enhance LLMs using NVIDIA HGX™ H100, Intel Gaudi2, and PEFT methods like LoRa and QLoRa.
    Linguistics and Humor in AI: Explore the challenges of integrating humor in AI-generated content, focusing on memes.
    AI-Generated Meme Showcase: Experience practical examples of small and large-scale Language models in meme generation.
    Recent AI Developments: Understand the latest advancements in AI content generation and the importance of DIY approaches

Looking forward to your RSVPs and to meeting you there!

Keep on hacking!🤩🤩🤩
```

## Isabella Geiß
* adesso the leading provider for IT services in Germany
* Project Management Officer usually and today the host

## Talk #1: Leveraging Open Source Tools for Advanced Machine Learning Pipelines - Saumya Goyal
* Leveraging OSS tools for advanced ML pipelines
* MLOps engineer from some consultancy extends service to BSH Home Appliances Group
* Regular conference speaker; Part-time lecturer at Macromedia Hochschule; MSc Informatics TUM;  AWS Certified Solutions Architect
  * all quite impressive
* Comes from Datamics: helps Audi, BMW, BSH, Daimler, Vodafone - create content on Udemy
* Talks at ML Convered and PyData; she mentioned René Brunner as well

### Why OSS Tools?
* LabelStudio
* FiftyOne
* It costs nothing, until and unless you wish to experience enterprise version, deploying exclusive features, require extensive support
* Excellent capabilities to customize and fix: add plugins, augment features, fix bugs
* No misuse of data
* Fulfills the technical demands
* Allows to become creative with code
* Avoid becoming a code monkey
* Requires a dedicated technical understanding
* Some sophisticated tools: data exploration and ... <-- check: additional tools
TODO: add image from phone with the tools

### Label Studio
* Labeling tool: multiple projects, users, and data types
* Supports images, video, audio, time series, formats
* Supported format: JSON, CSV, TXT ... Cloud support as well for AWS, GCP, Azure
* Integrates well with ML models to supply predictions for label or perform continuous active learning
* Highly customizable interface
* Intuitive design
* Well documented
* She recommends this tool really much
* Look and feel: Cloudflare, NVIDIA, Meta use this ...
* Labeling configuration is done via XML: object, control, visual
* Can be set up with one Compute, one Store, and one PostgreSQL item on AWS for instance
  * Can also be put into Docker, or be replaced with local installations

## Next Tool: (Voxel) FiftyOne
* For CV tasks
* Tool for building high-quality datasets and CV models
* Visualize datasheets and interpret models
* Core features: curating datasets, identifying possible label mistakes in your datasets, evaluating models, embeddings visualizations, working with geolocations: storing, visualizing, querying datasets by location
* Powerful plugin framework for extending and customizing the functionality of the tools
* Ability to orchestrate tasks with Apache Airflow, etc.
* Used by MS, LEGO, ...
* Open-source version allows only local dataset, closed one has remote data storage/usage
* Feature: FiftyOne Brain: finding problems
TODO: add image of the example
* Standard workflow: load dataset into remote machine, launch FiftyOne remote sessions, SSH into this remote server - can be restricted to a particular IP/host
* Allows also usage with notebooks (Jupyter)

### How to Integrate LabelStudio and FiftyOne?
* Proposed workflow: raw data -> visualize and curate dataset -> send it for labeling -> receive the labeled data ->
TODO: add image for the workflow
TODO: image of the architecture for AWS
* Possible to put both configs into one EC2; but better separate, because labelers and data scientists are different

### Plug and Play: Your Call
* Understand the needs of your data scientists and their roadblocks - communicate
* Explore the plethora of tools available in the OSS world
* New tools are released often - find your flavor
* Find the tools which have room for customization
* Example: add custom plugin in FiftyOne (very well documented process for directed creativity)
* Save some money
* Don't stick to one tool forever
* Avoid vendor lock-in by designing your architecture like LEGO
* Contribute to the open-source community, because you can

# Talk #2: Unleashing Humor with AI: MemeGPT - Fine-Tuning LLMs for Meme Generation using NVIDIA HGX™ H100 and Intel Gaudi2 - Stefan Ojanen
* Stefan Ojanen - Director of Product Management at Genesis Cloud
* How to create memes with LLMs
* Unleashing humor with AI
* Largest database for memes: imgflip.com
* Roadmap for MemeGPT
* Training on different sets of powerful hardware: 8x NVIDIA H110 versus 8x Intel Gaudi2 AI
* His third startup he is working at: has already some exit plans
* ChatGPT has problems understanding memes
* Paper: Dank Learning: Generating Memes Using Deep Neural Networks
* Based on LSTMs - already way back the idea, before transformers

### Attention is Not All You Need, Data is What You Need - imgflip.com
* Where to get data? Imgflip, 650k meme templates
* Mailed the founder: 40 million individual user-created memes

### Brief History of LLMs
* Word2Vec (2013) -> LSTM (RNN) 1997--2017 > Transformers 2017
 - -> Hyena & Mamba (2023 -) * Google Translate is for instance Google Translate, or Alexa
* So Mamba is a good competitor

### Why Do Memes Matter?
* Fact: 49% of Americans don't understand irony
* Humor harder than any business case
* Humor: sarcasm/irony
* Contextuality
* Subjectivity
* Linguistic nuances

### Can Robots Crack a Joke? July 2023
* Memes are multimodal
* Meme Drift - Cosimo Iaia - personal friend
* Memes incorporate cultural drift (evolution) much faster than expressions and words in language

### Sampling
* Lots of work dealing with the data, not work with the model
* 256 most common templates; only English memes; one dataset for the metadata for 650k templates, 40 million individual memes
* Data looked pretty nasty into something nicely looking stuff
* Readable structure -> Hugging Face format

### Roadmap
* Model development -> Concept -> POC -> Release candidate -> Final model -> Multimodal model
* Model serving, GC internal K8s + Triton, imgflip.com
* Some small OSS LLMs they tried: Stable-LM, RedPajama, EleutherAI/Pythia-2.8b
## Implementation
* They offer their high-end short-term test platform for $2/hr starting in February
* Llama2-70b: parameter-efficient fine-tuning using LoRa adapters
* Recommended reading: RAM efficient PyTorch
TODO: add image about the Drake meme
* Fine-tuning an LLM: by showing examples of what you expect; to affect the behavior of the model, possible with relatively little data
* 16h for one tuning run

## What is LoRa: Low-Rank Adaptation of Large Language Models
* Take a frozen model with its parameters, change matrix = LoRa updated parameters
* Gaudi2 looks like the real contender against the H100
* Some examples from the Llama2-70b
* What is the threshold for "Large"?

### Recent Developments and Why to Do It Yourself
* While OpenAI is still working on understanding memes, we are already creating them -> just do it yourself!
* Why?
  * Maintain full control
  * No external dependencies
  * Tooling widely available
* All the used code is boilerplate stuff, nothing really fancy - his words
* Special thanks from him to: Dylan Wenzlau, the founder of imgflip.com; Maroune Khouk is the AI evangelist; Stefan Ojanen is the Director of Product Management
* How powerful the machine is needed to make the machine: similar to the fine-tuning machine
* Is this model used in day-to-day? Not yet, plan to integrate and offer API to imgflip
* RAG: not used here, idea is to be totally in model - not retrieved
* Book "Thinking Fast and Slow": the LLM is a fast brain; how to make it more thoughtful: chain of reasoning, RAG, ..
  * RAG is reducing hallucinations; but for memes you don't want to mimic. The model should generalize and generate completely new content!
* Yes, they used a good RA, when everyone is fighting for machines
