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

# isabella GEiß
* adessor on f the leading  I service providers in germany
** project management  officer

## saumya - leveraging opensource tools (todo check the agenda for correct name)
*leveraging OSS tools for advanced ML pipelines
* MLops engineer from some consultancy extends service to BSH home appliances group
* regular conference speaker
* part time lectuer at macromedia hochschule
* msc informatics TUM
* AWS certified solutins architect
  * all quite impresive
* comes from DAtamics: helps audio, bmw, bsh, dailmer, vodafone - create content on udemy
* talks at ML convered and pydata; she mentioned rene brunner as well
### why oss tools?
* labelstudio
* fifty one
* it costs nothing, until and unless you wish to experinece entreprise version, deplyoing exlcusivfeatures, require extensive support
* excellent capabilities to customiue ad fixx: ad plugins, augment feautres, fix bugs
* no misue of data
* fulfillsthe technical demands
* allows to become creative with code
avoid becoming a code monkey
requires a dedicated techinal understanding
* some sophsiticated tools: data exploration and ..
TODO add img from phone with the tools
### label studio
* labelling tool: mutliple projects, users and data types
* supports images, video, audio, time series, formats
* supported format: JSOn CSV, TXT ... cloud support as well for AWS, gPC, azure
* integrates wellmitMl models tosupply predictions for label or perform continuous active learnin
* highly cutomisable interface
* intuitive desing
* well documented
* she recommends this tool really much
* look and fell: cloudflare, nvidia, meta use this ..
* labelling configuration is done via XML: object, control, visual
* can be set up wit one Compute, one Store and one ostgreSQL item n AWS forisntance
  * can also be put into docker, or be replaced with local installations
## next tool: (Voxel) FiftyOne
* for CV tasks
* tool for building high quality datassts and CV models
visualize datasheets and interpret models
core features: curating datasets, identify possible label mistakes in your datasets, evaluatiog models, embeddings visualzations, working wiht geolocations: storng, visualizing, querying datasets by location+
* powerful plugin framewok for extending and customizing the functionality of the tols#ailityto orchestrate tasks wiith apache airflow, etc.
* used by MS, lego, ..
* opensource version allows only local dataset, closed one has remote data storage/usage
* feature: FiftyOne Brain: finding problems
TODO add img of the example
* standard workflow: load dataset intoremote machine, launc fiftyone remote sessions, ssh into this remote server - cn be restricted to a particualr ip/host
* allows also usage with notebooks (juypter)

## how to integrate labelstudio and fityone?
* proposed workflow: raw daa -> visualize and curate dataset -> send it for labelling -> receive the labelled data ->
TODO add image for the workflow
TODO image of the archivetcure for AWS
* possible to put both configs into one EC2; but better searate, because labellers and data scientists are different

## plug and play: your call
* understand the needs of your data scientists and their roadblocks - communicate
* explore teh plethora of tools available in the OSS world
* new tools are released often - find your flavor
* find the tools which have room for customization
* example: add custom plugin in fiftyone (very well documentesd process for directed creativitiy)
* save some money* dont stick to one tool forever
* avoid vendor lockin by desgning your architecture like lego
* contribute to the open source communicaty, beceause you can

# second talk - MemeGPT (TODO add proper title from agenda)
* Stefan Ojanen - Director of product management at Genesis Cloud
* how to create memes with LLMs
* unleashing huor with ai
* largest database for memes: imgflip.com
* roadmap for memGPT
* training on different sets of powerful hardware: 8x nvidia H110 versus 8x Intel Gaudi2 AI
* his third startup he is working at: has already some exit plans
* chatgpt has problems to understand memes,
* paper: Dank Learning: generating memes using deep neural networks
* based on LSTMs - already way back the idea, before transformers

### attention is not all you need, daa is what you need - imgflip.com
* where to get data? imgflig, 650k mem templates
* mailed the founder: 40 million individula user created memes
### brief hsitory of LLMs
* word2vec (2013) -> LSTM (RNN) 1997--2017> transformers 2017
 - -> Hyena &Mmba (2023 -)* google translate is for instance google translate, or alexa
* so mamba is a good competitor

## why do mems mater?
* fac:t: 49% of americans dont understand irony
* humor harder than any business case
* humor: sarcasm/irony
* contextuality
* subjectivity
* linguistic nuances

### can robots crack ajjoke? july 2023
* memes are multimodal
* Meme drift - Cosimo Iaia - personal friedn
* memes incorporate cultural drift (evolution) much fast than expressions and word in language

### sampling
* lots of work dealing iwht teh data, not work with the model
* 256 most common templates; only english memes; on dataset for the metadata for 650k templates, 40 mio invidiual mems
* data looked prety nasty into something nicely looking stuff
* readable sturcutre -> huging face format

### roadmap
* model development -> concept -> POC -> release candidate -> final model -> multimodal model
* model servin, GC internal K8s + Triton, imgflip.com
* some small OSS LLMS they tried: stable-lm, redpajama, eleutherAI/pythia-2.8b
## implementation
* they offer theigr high end short term test platform for 2$/hr starting with february
* llama2-70b: parameter-effficient fine-tuning using LoRa adapters
* recommended reading ram efficient pytorch
TODO add img about the drake meme
* fine-tuning an LLM: by showing examples ofwhat you expect; to affect the beahviour of the model, ossible wiht releaitvely little data
* 16h for one tuning run

## what is Lora: low rank adapatio pf large langue models
* take a fozen model with its parameters, change matrix= lora updated paameters
* Gaudi2 looks like the real contender against the H100
* some explanes form the llama2-70b
* what is the treshold for "Large"?

### recent developments and why to do it yourself
* while openai is still working on understanding memes, we are already creating them -> just do it yourself!
* why?
  * mantain full control
  * no external dependencies
  * tooling widely available
* al the used code is boilerplate stuff, nothing really fancy - his words
* special thanks from him to: dylan wenzlau, the founder of imglfip.com; maroune khouk is the AI evangelist; stefan ojanen is the director of product managemnt
* how powerful the machine is neded to make the machine: similar to the finetuning machine
* is this model used in day to day? not yet, lan to ntegrate and offer API to imgflip
* RAG: not used here, idea is to be totally in model - not retrieved
* book "thinking fast and slow": the llm is a fast brain; how to make it more thoughful: chain of reasining, RAG, ..
  * RAG is deucing hallucinations; but for memes you don't want to mimic. the mdel should generalize and geenrate completyl new content!
* yes, they used a good ra, when everyone is fighting for machines
