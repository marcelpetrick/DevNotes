# 20231117 NVIDIA - The Fast Path to Developing with LLMs

* speaker: David Traubenheim; Senior Solutions Architect NVIDIA

* todo add images from mobile
* todo: add the part about guard rails
* todo add images from desktop



* examples of frameworks: not only LangChain
* competitors to langchain are hayxstack and griptape
img_TODO.png
  * unitary call versus chain/pipeline call
* langchain: open source, large user community
* haystack: open source by deepset
* next use case: similarity search
img_TODO.png
 * simple local vector DB: document input -> docuemnt processing-> conversion to vectors -> retrieval
 img_TODO.png
 * based on LangChain components

## RAG_: retrieval ugmented gerneration (RAG)
!img todo
* decouples an LLM from only being able to act on orginal training data
* obtivates the needto retrain the LLm with the latest data
* LLMs limite by contxt window sizes
concept:
  * connect llm to dat sources at inference time: eg. databases, documents, 3rd party APIs
  * find relevant data
  inject relevant data into the promopt
* components ..
### canonical RAG workflow
img_TODO.png

## embeddings and a vector database
* embeddings are data represented as numerical vector
* part of semantic search
useful for: classification, clustering, topic discovery
many pretrained and trinabled embedding model sources ..
img_TODO.png
### stage 1 data preapration: loading and chunking data
img_TODO.png
* workflow: storage -> doc loaders -> doc chunking
* document loading, splitting, chunking, storing -> lod from file formats: pdf, json
### stage2: chunking
* check: splitting methods: need to pick right splitting method to ensure no-loss of information, ex. Split on separators
* chunk size: smaller chunk size (fine grained) vs. large chunk size (holistic). Needs experimentation to fin right-size chunk based on doc types
### stage 3. retrieval options
* subquery chaining: decompose prompt to multiple retrieval stages
* re-ranking: rewtrieve more results, and rank on multiple atrtributes to improve query relevance
img_TODO.png
* building the app
* the whole app is surprisingly brief: because he framework does the heavy lifting
* optimizing retrieval to accellerate performance
img_TODO.png
* TODO: invitation to explore the nvidia ai foundation models
*Ü nemotron-3, code llama, Neva, Stable Diffusion XL, LLam 2, CLIP
img_TODO.png
* TODO add the two URLS
## What did you learn?
img_TODO.png

core concepts of LLm architecture and fondation models
factors for selecting between and evaluationg LLM APIs
prompt enbinerring mbasis..

todo more lines from this slide.


------
copied from the Q&A

----
Do you see in potential in NLP wit GNNs?

GNN archtectures have been used for text classification and language translation. These are smaller models than the ChatGPT architectures we're discussing at the moment. So, perhaps an oppo for GNN models running on edge processing for narrow tasks.

What do you recommend would be a good framework to conenct multiple LLMS over HTML 5 Web App

LangChain, Griptape, Haystack, and LlamaIndex are a few of the frameworks you can consider for building LLM applications.

assuming we could also ask for similar emails to b grouped e.g. same issue ?

Very true! Once you have structured data thanks to the LLM's JSON output, you can design the UI however you wish.

Will this session be focused on closed-source LLMs?

We will be covering several LLMs, both open-source and closed-source throughout the day. :)

How to understand the temperature variable?

Temperature hyperparameter controls the creativity of the model. The higher the temperature value, the higher the creativity, suitable for tasks such as creative writing.

Will we be covering finetuning in this session?

We cover that in the next session, "Tailoring LLMs to Your Use Case"--hope you can join for that too!

What is temperature parameter again?

A measure of randomness permitted in the search for the top response. Higher numbers add a sense of creativity, for better or worse, depending on your app!

How are these benchmark scores calculated?

Normally, a paper is published along with results, to show how the scores were calculated.

Want to train LLM with my own data only. How can I do this? How to start?

We'll be discussing options for customizing LLMs in Session 2: Tailoring LLMs to Your Use Case, which will follow this session.

Other the temperature, how can we determine which hyperparameters to add apart from temperature?

I've found this Guide can be useful for learning more about prompting, including some of the common settings. https://www.promptingguide.ai/introduction/settings

Is Prompt-engineering suitable for other task like code-representation using pre-trained model?

Typically, for coding use-cases on foundation models (meant for natural human language) prompt engineering won't yield the best results. I would recommend more advanced techniques like p-tuning. You can learn more about the different customization techniques, in the next webinar: "Tailoring LLMs to Your Use Case". Please register here: https://www.nvidia.com/en-us/events/llm-developer-day/

What is the best approach to precisely fine-tune an LLM to get rid of hallucinations if it's possible?

We will be discussing strategies for mitigating hallucinations in Session 2: Tailoring LLMs to Your Use Case, following this session. In short, training models further on your specific domain, as well as packing the context of the prompt with relevant information (RAG).

What is a minimal hardware setup for working with LLMs? Which types of GPUs (how many) are needed for fine-tuning (in an on-premise setup)?

For self-managed LLMs, you'll want to check our the session later today: "Running Your Own LLM"!

Can you explain more about benchmark for a beginner?

There are several ways to evaluate models, however each one of the techniques has its own set of shortcomings. Ways include: Academic benchmarks, human-in-the-loop evaluation, or using LLMs as a Judge. Academic benchmarks are very uni-dimensional, evaluating models on a single task with a single dataset and not representative of real-world interactions. Human-in-the-loop evaluations are tedious and laborious. LLMs as a Judge relies on the confidence one has on the capability of the LLM that is being used as a judge.

There are some efficient way to quantize LLMs or make them more efficient including qlora, lora and deepspeed (accelerate wrapper), is there a certain argument that would call these libraries. Or does NVIDIA use it's own kit?

We touch on LoRA in the session "Tailoring LLMs to Your Use Case" and NVIDIA's stack for self-managing LLMs both in that session and in "Running Your Own LLM"!

Can Guardrails be customized to what we want? For example if I want to build a chatbot that doesn't give private information of my clients, can I adapt Guardrails to do that?

NeMo Guardrails is fully programmable toolkit that can be customized with any types of rails. Learn more here: https://github.com/NVIDIA/NeMo-Guardrails and https://developer.nvidia.com/blog/nvidia-enables-trustworthy-safe-and-secure-large-language-model-conversational-systems/?ncid=prsy-552511#cid=dl28_prsy_en-us.

Why do we need multiple chain prompt any specific reason?

It is often helpful to reduce complex tasks that an LLM (especially a smaller model) needs to complete into smaller sub-tasks. Chaining multiple prompts rather than asking the LLM to do everything at once may result in better performance on the task.

How is memory and the number of shots that you can do associated?

The more shots, the more text in the prompt. The more text, the more context memory used.

Can anyone begin with high end consumer gpu and beginner knowledge develop their own LLM and application or do you need to be PH.D level?

Building a full foundation model from scratch would be a monumental task for an individual--but making an app with a customized LLM is totally possible! The apps we show throughout the sessions today all can be done at that scale, and we hope the sessions are helpful in figuring out where to start.

Is it also possible to have pdf as document input?

Absolutely, e.g. LangChain has a PDF reader function. Others to do too.

What are some good ways to clean up HTML documents prior to feeding them to LLMs? e.g. cleaning up emails that contain HTML

Some frameworks will have built-in document parsers. For example, LangChain has an HTML parser that uses Beautiful Soup to clean up HTML.

can we get the free sandbox to try LLM for our use cases

Suggest you get started on NVIDIA AI Foundations to try state-of-the-art models from the community and NVIDIA today. https://catalog.ngc.nvidia.com/ai-foundation-models

How carefully do you need to "curate" documents going in? For example, if I'd stripped the HTML from a web page, but there were things like headers and nav bar text, would that hurt?

Curation is a big part of data prep (and we discuss further in "Tailoring LLMs to Your Use Case" later today). Many modern LLMs can "work around" HTML syntax, but you could also tune a model explicitly to extract the useful information from a page using the techniques we discuss in that session.

Is it possible to save the state of a chain to return to it and continue chat later?

Yes, as the history (or a summary thereof) can be stuffed into the prompt.

What underlying hardware do we need to have to start using NEMO today at our organization?

NeMo Framework today is supported and tested on all major clouds, and on-prem DGX systems.

For generating the embeddings of the search, what language model are you using?

We use a BERT-family embedding model called E5 (found in Hugging Face) for the demo. There are many for embeddings. For example, if you wanted an API-based embedding model you could try OpenAI's API.

does LLM store all the data in vector database ?

The LLM doesn't do the storage itself (backend processes, including the embedding model, do), but all that strictly has to be stored in the vector database is the vectors--you could look up the original text at inference time, from the original data storage.

what is the use of vectors being discussed?

The closer two vectors are, the more similar the meaning of the text.

How does combining different embedding models affect retrieval? For e.g., llama embeddings w/ open ai embeddings?

In general, embeddings from different sources can't be combined--they live in different worlds, so to speak. For retrieval, you need a measure of "distance" that is consistent, and since the same text would be put in different places with different embedding models, distance is inconsistent.

Any link for a whitepaper on Nemo working with LLMs?

We have several resources to get started with NeMo. Please refer to the user guide to get started today: https://docs.nvidia.com/nemo-framework/user-guide/latest/index.html#

is LangChain the recommended framework for GPT3.5 - GPT-4 ?

We don't specifically recommend one framework over another--LangChain is just a popular one, starting with the rise of ChatGPT models like those.

How can we chunk by semantic meaning so the same topic or paragraph isnt split into different chunks?

Reduce chunk size is one way. Others have proposed using semanic similarity metrics (like shown here) to know when a "new" chunk should begin.

I am equally interested in the 2 webinars starting at 9:30, will the webinar be available on demand later? I can't choose which to attend.

Glad to hear it! Yes, the sessions will be available on demand.

Can we also combine RAG methods with a fine-tuned model on our data? Or would that just be redudant

Yes! We talk about doing exactly that--and why you might want to--in the session "Tailoring LLMs to Your Use Case"

where can we prepare our own LLM?

NeMo offers an end-to-end framework from building, customizing and deploying generative AI models anywhere, learn more here: https://www.nvidia.com/en-us/ai-data-science/generative-ai/nemo-framework/. You can also use one of the many frameworks available in the community to build custom LLMs such as DeepSpeed, HuggingFace, etc.

to run a 40B paramater model would a A100 GPU be sufficient ?

With quantization, you could potentially run a Llama 2 70B model on a single A100 80GB GPU.

Is there a good tutorial on toolkits like LangChain that you would reccomend?

A good one is at DeepLearning.ai

When working with RAG, all the embedding data is then converted into plain text to be sent to LLM for Augmented Response Generation?

Kind of! It's not possible to convert embeddings directly back to text, but instead you look up the text based on which embeddings were selected

Though your Guardrail can be programmed/controlled, is there any inbuilt restriction on terms? I mean excluded words/phrases?

Nope - fully customizable and programmable toolkit, offering developers full flexibility, with a quick path to build custom rails and logic for specific applications :) Get started here: https://github.com/NVIDIA/NeMo-Guardrails

Can you clarify more the difference between pre-training and fine-tuning?

Pre-training involves training foundation models from scratch, while fine-tuning is the process of customizing a foundation model for your use-case(s).

Can you elaborate more on the creation of datasets for finetuning for specific domain, or share your experience?

We will discuss strategies for gathering datasets in Session 2.

I arrive a bit late. Will this be recorded and posted somewhere?

The recordings will be available later on demand.

How do I take into consideration the distinction between similarity between embed(query) and embed(document) vs. similarity between embed(answer(query)) and embed(document)? In other words, be aware of the difference between a query and a document?

Some embedding models do indeed make a distinction between the two--for instance, e5-large has "query" vs "passage"

Which model will be great to convert natural language prompt to sql query related to my database

Many foundation models (like a GPT3.5) already have the ability the write SQL out-of-the-box. However, keep in mind they were likely trained in many different versions of SQL, so fine-tuning a model to only use your specific variant of SQL, and also providing it with your database schema, would likely lead to better performance.

Excuse my noob question... how do i compare and contrast LoRa vs RAG pls?

They are complementary techniques--see the later session "Tailoring LLMs to Your Use Case". LoRA updates the LLM, RAG brings it relevant data.

I've heard that vector databases are sometimes overkill for simple search tasks, and some experts just recommends regular DB's.

Vector-based Semantic Search can be combined or substituted with more traditional search techniques like an Elasticsearch.
