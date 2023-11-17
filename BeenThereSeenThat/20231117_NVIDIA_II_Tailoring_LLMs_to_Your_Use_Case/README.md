# 20231117 NVIDIA II - Tailoring LLMs to Your Use Case

* speaker: Christopher Pang; Senior Solutions Engineer; NVIDIA

## agenda
* llms in context
* tuning hosted APIS LLMS
* data collection
* TODO add the rest
![]()img00

## why bother creating a custom model?
* motivations for fine-tuning
1. you just want the best use-case/task specific results
2. you want to save money and reduce latency
3. you want a smaller model (fewer parameters) that was trained to imitate a larger one

## exmaple app 1: domain taILORED SUMMARIZTEATION WITH HOSTED llm apiS
* domain tailored summarization: typical downstream client only read from the API
![](img00.png)
![](img00.png)
* using steerlm:  select this first
* then select the model: using model NeMo GPT20B - compare both of them
* comparison of the summaries of both models: then evaluate the results
* when the comparison is checked, it can be customized, so that this is fed back for the next training - with more human input, the custom models will perform better and better
*## hot it works

# tuning hosted api LLMS
* e.g. A21lab jurassics, AWS titan, cohere, scale, openai, ndivia
todo img00png

* example openai API
  * clean no-code environment
  * set some parameters, select model upload data and create prompt
* what is fine-tuning?
  * traditionally means updating full parameters of the model with supverised learning
1. either: suupervised fine-tuning of llm
2. train reward model with human feedback
3. reinforcement learning pipeline with human feeedback
* for more details: hugginface.co/blog/rlhf
* latest techniques for customizing LLMs
img00
* prompt engineering is not changing the model!
* prompt desing is crucial to obtaining good results from an LLM
img00
latest techniqes for customizing LLMS
* few shot prompting
img00
* prompt learning: comparison to full-parameter fine-tuning
* multi-headed self-attention ..
* prompt learning adds a small number of trainable virtual tokens upstream of the llm
more efficient: for each new custom task, all we do is train those tokens
* the downstream foundation modlel is unchanged
* or: P-tuning: more accurate than fine-tuning
* access also possible via POST-request
* NeMo LLm Service
* also: adapter-based techniques: adapters, LoRA, IA3
* adapters: insert into each transformer layer, only update weights of adapters
* LoRA: low-rank adaptation: optimize rank decompozition matrices of dense layers
* IA3: like adapter, but where each adapter is a vectro, that scales key, value or ffn
* his recommendation: pick what is most efficient as fine-tuning-mechanism; then get started to build the app
  * then try some of the other efficient ways and optimize

## data collection and preaparation for tuning
img03
* before doing this, check if someone maybe already used it to fine-tuning a model whcih is availble on hugging face
* don't over rely on public datasets: need to curate input/output pairs
*Ü less is more for alignment: high-quality, low quantitiy training da versus low-quality, high quantitiy, see also the arxiv-link
* synthetic data generation: use high end model and complex prompt template to induce correct behavriou/outputs from smaller model (context distillation)
img04

## exmaple 2: RAg workflow
* retrieval augmented genration
* decouples an LLm from only being able to act on original training data
* obtivates the need to retrain the LLM with the latest data
* LLMs limited by context window sizes

* concept: connect LLLM to data sources at inference time; eg. datbase, web, documents, 3rd prty
* embeddings and the vector dtabase
--> todo: img with

+ comparison: question decomposition versus chain of thought reasoning
--> todo: img with

RAG example APP
img!
img!
* now use a more complicated question
* leads quickly to some hallucination
* using placeholder can help with the more heavy questions

* how does it work?
  * see OctoML: for synthetic data generation and context distillation
  * acquire data set -> prompt LLama 2/= B model with few-shot prompts -> manually verify results -> train LLama 2 7B with PEFT and FP4 to mimic Llama 2 70B -> prompt llama 2 7B with zero-shot prompts. Hosted on OactoAI platform

###  more robust RAG
* tuning a question decomposition model
tuning a QA model that explicitly only answer from context
*retrieval enhancements:
 * tuning a custom embedding model
 * re-ranker
 * decoupling retrieval and generation chunks
 * using document metadata/hierarchy
* agenst: using external tools (to answer a math question)
* serving for inference

## tuning self-managed LLMs
img00 todo
* self-managed: own and manage underlying model weights
* privacy, ownership, portability, flexibility, cost:run on own infrastrcutre; choice of customization
* examples for getting started: nemo framework, huggingface hub+PEFT

### hosted aPI llms
* accessibl enly throuh hosted APIs
* easy to use, push-button experiences
* easy to deploy: don't have to worry about manangeing hardware and keeping your API healthy
* examples: openai, bedrock ..-

* suggestion: try out NeMO framework; used by oracle, AWS, microsoft Azure, lenovo, dell, hewlett packard, nvidia DGC cloud
* neMO is cloud native and canbe used on all platforms

### example
img:
* 1. set parameter efficient fine-tuning type; 2. set hyperparameters

## reacp
img: - the last one


todo: add the links from the last slide

--------------------------------

# Q&A

Do LLMs suffer from catastrophic forgetting? If yes, what are the potential solutions to it?

We will discuss here (and in the other sessions "The Fast Path to Developing With LLMs" and "Running Your Own LLM") how to use retrieval-augmented generation (RAG) to "remember" from an updated data store

Why not use RAG in those cases?

We will be discussing RAG as well later in the session. A good takeaway is that RAG and fine-tuning are not mutually exclusive.

what are some of the factors that decide the cost while using an LLM API

Most LLM APIs are costed per token, and that typically scales with the size of the model (which is to say, its hardware footprint)

Will the code be available on GitHub?

We're not planning at this time to push the code to a public repo. But we are listening to our audience's requests to guage interest over topics like the source code.

what is memory in the context of llms?

There are several types of "memory" involved with LLMs: the parameters in the model and how they encode information implicitly in the weights; the physical memory footprint in hardware; or the ability of an app to store and feed context into the model (e.g. via retrieval-augmented generation/RAG)

What are the benchmarks for determining the "sufficiently large" size of a prompt dataset needed for full-parameter fine-tuning of an LLM?

This raises the importance of dataset quality, doing training incrementally and having a good evaluation framework for your specific task. Start with a smaller high-quality training set and see if performance improves at all, before jumping all in with a larger dataset that may be expensive/time-consuming to collect.

What is A/B testing?

That's a test where you ask a person/AI which of two choices is preferable. Think going to the eye doctor: "Which of these looks clearer, 1 ... or 2? 3... or 4?"

Does NeMo framework support CPUs as well?

NeMo Framework is currently supported on all major clouds and on-prem DGX systems. Learn more about NeMo here: https://www.nvidia.com/en-us/ai-data-science/generative-ai/nemo-framework/

Is the Domain-Tailored Summarization something that is open?

Not at this time, but we are listening to the interest from folks about getting their hands on it!

Is this a managed NVIDIA offering or just demo?

The examples presented in this session are solely for demo purposes.

does human compares the model output in A/B testing for evaluation?

Yes preferable many humans, or it could be an LLM, depending on the use case.

If we use fine-tune does the model will lose the generalize ability and become a prejudice model ?

With fine-tuning we typically are looking to take a foundation model trained to generalize well to lots of tasks, and specialize it to the task we specifically care about. Some customization techniques like p-tuning train a small model that sits on top of the foundation model, letting you customize multiple different models that re-use the downstream foundation model.

how do u evaluate the summarization result?

I would recommend A/B testing with a user group. "Which of these two summaries from two different AI models do you prefer?"

How does the server deals with multiple queries at the same time? does it clone the model for each query?

Kind of! "Batching" like that is a key feature of inference servers, and we discuss how that works a bit in the next session, "Running Your Own LLM"

what if you don't want to provide your data externally?

We will be discussing ways to tune an LLM using your own self-managed infrastructure (rather than an API) later in the session.

Isn't the Assistant API not fine tuning at all? It doesn't even allow using a fine-tuned model from what I understand.

OpenAI's Assistant API does indeed allow fine-tuned models: https://platform.openai.com/docs/assistants/overview

Does fine-tuning add knowledge to the model?

Yes. Also aligns the knowledge to a desired set of deeper expertise(s).

Is the parameter count (e.g. 4B, 7B, 70B) translatable between different kinds of models? E.g. if I can fit a 70B version of model X within my vram, should I expect to fit a 70B version of model Y?

The parameter counts do mean essentially the same thing, but whether you can fit a model into your vram depends just as much on what precision the model's weights use. Lower precisions (like int4) can fit way more parameters into the same vram than higher precisions (like fp16). Converting to lower precision is a key feature of optimizers (as discussed in the next session, "Running Your Own LLM")

Could you share the link of the blog post?

Yes that particular post is part of our NVIDIA Developer Blog: https://developer.nvidia.com/blog/announcing-steerlm-a-simple-and-practical-technique-to-customize-llms-during-inference/

what do these parameters mean- temp, k,p

There are several hyperparameters which can be adjusted during inference to control responses. Temperature - Allows you to configure your output. Higher values make the output more random, while lower values make it more focused. Top_K controls the number of top tokens to sample from, and when set to 1, it consistently chooses the token with the highest probability.

Does finetuning necessarily have to run on a GPU?

While it's possible to run finetuning anywhere the underlying deep learning framework runs, we've put a lot of effort into making GPUs an efficient place to do your finetuning! Some of these models would take a *very* long time to finetune on e.g. CPU.

can u share a source as a tutorial for RLHF?

https://huggingface.co/blog/rlhf

Does it make sense to fine-tune an LLM in a language that was few % of the dataset during pre-training?

Certainly! Depending on the language and access to scale of compute & dataset, you can choose between prompt learning, PEFT, or fine-tune the models to get better accuracies for that specific language.

Will the webinar be made available as a recording?

Yes. Check back for video on demand after the event.

I missed the prior session of "The Fast Path to Developing with LLMs". May I know where I can find the related presentation pdf doc？ Thanks.

Come back after the whole event to check for VOD being ready.

what is a policy model? Just the regular LLM model?

A policy is effectively "what to do in every given situation" (originally applied to taking agents taking actions), so yes, in this case usually just the LLM, since the "situations" are just prompts

While inference , can you explain why would one use an GPU vs a multi core CPU.

Extremely high-end CPUs have maybe 128 cores--an H100 GPU has over 14,000 regular compute cores, never mind its specialized hardware (like Tensor Cores) for doing deep learning inference

would we have access to these applications? This is wonderful. Thank you!!!

These demos were built on the internal NVIDIA network. At this time, we don't plan to release code, though we are evaluating that stance depending on these sessions' comments.

Foundational models are trained on large corpus of general data. An LLM trained/fine-tuned on a domain-specific corpus, e..g, organic chemistry, should perform better on the different downstream tasks for that domain (i.e. organic chemistry in this case). What are your thoughts on such a retraining idea and how would go about it? Are there better ideas for domain specialization?

Yes, that's a common approach! For instance, we put out BioNeMo (https://www.nvidia.com/en-us/clara/bionemo/) as a platform for LLMs for drug discovery.

how much cost is associated or architecture gpu is needed to use this

This will depend on your choice of model and hardware. Later in the session, we built a demo with a Llama 2 7B model that was trained on an AWS G5 EC2 instance which starts around $1/hr on-demand pricing.

Does a service such as NeMo LLM employ any efficiency measures to make the model inference faster?

Yes. For example, https://github.com/NVIDIA/TensorRT-LLM

Why would any one do Full Parameter tuning instead of just building one from scratch or build on top of a smaller LLM ?

Often times, you may want to add domain-specific knowledge alongside the knowledge of the foundation model. In such cases, where you have a specialized domain, but without XXXB of tokens, you can bias the foundation model to your specific domain without full-parameter model tuning. SFT is a popular stepping stone for instruction tuning techniques like RLHF, or SteerLM, which also involves full-parameter tuning. This is also often cheaper and faster to accomplish than building a foundation model from scratch. Check out NeMo Framework to get started today: https://www.nvidia.com/en-us/ai-data-science/generative-ai/nemo-framework/

I’m using a programming language FlexScript, ChatGPT doesn’t know this language. How can I train this to LLAMA 2.

We show the pathway that was used to make CodeLlama from Llama2 in the next session, "Running Your Own LLM"--essentially, start from the foundation model then add examples of the programming language of interest to tailor it.

I'm interested in developing an application where a financial executive can use text or document prompt/responses to analyze private company-specific performance given financial statements, salesforce data (assuming B2B SaaS), to regularly gauge the health of a business in replacement of an analytics dashboard with a GUI. How can I go about building this where accuracy and relevance matters more than cost or latency?

You may benefit from semantic search separately and also as part of RAG along with a LLM.

You say that finetuning a LLM needs to have 1k-100k of input data. Does this apply for all types of LLM:s like 70B, 40B, 7B. How do you know how much input data you need?

It's tricky, no doubt--mostly because the amount of data isn't just about the size of the LLM but also the amount of variety in your use case. If you have a focused use case (like classifying text), a few hundred examples may suffice, even on fairly large models. If you want a new model that works on many use cases, it can take much more.

I think I'm misunderstanding - with supervised fine-tuning, would you be adding training data that's similar to what you'd want to be looking for (as in, the data being self-added is itself the label)? Or would you need to be labeling the training data in same way?

The "supervised" part of SFT means that you specify prompt-response pairs--the response is the "label" here

there is LOFT and QA-LORA and there is study in new tensor parallelism

Thank you for pointing those out! We're tracking.

Can we use fine tunning to "talk" with our data build summarizations or visualizations?

Finetuning may not be necessary, as tools (like LangChain) are available to input structured data into an LLM prompt for its analysis. You may also use RAG to bring unstructured text data into the LLM prompt.

how big can RAG be?

Vector databases can be very large--millions or billions of vectors, just scaling with the amount of hardware (especially memory)

What is the name of the Anthropic paper?

https://www.anthropic.com/index/question-decomposition-improves-the-faithfulness-of-model-generated-reasoning

RAG makes prompt size bigger. What are the remedies when they are oversized?

You may be able to summarize (using NLP or LLM) a portion of the prompt. Or, you may consider a model with a greater context window.

The vectors of the embedding model looks and sounds very similar to the latent space of a variational autoencoder. Are they similar?

Yep! (or any autoencoder)

Why not do partial parameter tuning, similar to finetuning a CNN where most layers are frozen. Can a similar thing be done for LLM?

This is typically known as parameter efficient fine tuning (PEFT). Several techniques under PEFT are popular today such as: Adapters, LoRA, etc.

what are the challenges with RAG: performance, computational?

Since it uses a smaller embedding model, RAG is generally much lighter-weight than the full LLM. Once the similar text is found, it's stuffed into the prompt going into the LLM. So, you should consider latency of the LLM as well as the token cost. Also, the size of the LLM may impact the accuracy.

will fine tuning help if I have a small dataset for text summarization

For smaller datasets, we suggest using techniques like p-tuning. Refer to this blog for more information: https://developer.nvidia.com/blog/selecting-large-language-model-customization-techniques/

How does your decomposition model know whether a question can be decomposed?

We hand-labeled questions that didn't need to be decomposed as part of the dataset

how to train llm to compute interlinked csv files ?

You can ask the LLM to output in CSV format, but if you have something more complex than flat data, you might consider JSON output instead.

For anyone who may want to try the NVIDIA fine-tuned LLama2 decomposition model that Chris is demoing, it is up and running on the OctoAI platform! Developers get unlimited free access to Llama 2 70B endpoints (including your decomposition model) for the next 4 weeks. To request access, folks can sign up here - https://octoml.ai/cp/textgen-innovation-program/

Thanks for sharing!

So when to use rag vs fine-tune my model(assuming it is available to be finetuned) ? I think in many cases fine tuning a model will work better than relying on embeddings?

That certainly is intuitive, but not really supported by data--there's a lot more hallucination with purely finetuned than RAG (and there's no reason not to use them together!). More generally, that won't work in cases where the data change regularly.

with limited budget for prototype can I create LLM from scratch. Should i generate synthetic data as i dont have permission to collect the data for my use case

Yes synthetic data generation is a good strategy in scenarios like these. Keep in mind that certain models have restrictions that data generated with that model cannot be used to then train other LLMs.

what is the 'num of recs' parameter?

Number of recommdations (hits) desired

Do you have any recommendations on MLOps/DevOps patterns to facilitate experimentation?

Check out our guide on LLMOps/GenAIOps here: https://developer.nvidia.com/blog/mastering-llm-techniques-llmops/

what is the UI written in? Gradio?

Vue

For context distillation, do we need access to the soft prompts [i.e. embeddings, rather than text-based input]?

You can do context distillation entirely with prompt-response text pairs--the main point is that you can convert a potentially large prompt template to just a couple tokens (that are still just in the regular text input of the distilled model)

Can Question Decomposition technique be used with more than two sub-question? This has been tried before?

Certainly possible! Would just need to build a training dataset that matches.

For solving hallucinations when answering questions based on pdf input using the open source models, what is the best approach? fine tuning or changing embedding model, adding more input?

Those are some possibilities, but that may be a good circumstance to consider guardrails applied to the LLM output. There is a lot of work in this area currently.

Where can I find examples of train adapter for text summarization with NeMo?

Please refer to the user guide and documentation, on specific examples of how to get started with adapters and other techniques here: https://docs.nvidia.com/nemo-framework/user-guide/latest/index.html

what is a queston decomposition model?

Transforming the original query into sub-queries that can be more easily answered individually

In a RAG architecture for a chat application, how can i tell my model when or when not retrieve from the VectorDB?

Can always train a model to emit a specific token or token pattern when RAG is necessary, then look for that token/pattern in the output, rerunning the LLM with RAG in that case!

how do we improve LLMs for its performance?

Better and more training data for answering performance. Or, for speed, consider TensorRT-LLM: https://github.com/NVIDIA/TensorRT-LLM

So total cost for training was only ~$1?

Just about!

What is FP4 that was referred to on the previous slide?

4-bit floating point (i.e. the precision of the weights)

Any learning resources that you recommend for AI beginners but Software Engineers veterans?

this page is a good place to start for introductory resources on LLMs from NVIDIA https://developer.nvidia.com/generative-ai

What is OctoML ?

A company (https://octoml.ai/) that helps with cloud-based generative AI--in our case, converting a self-managed model to an API endpoint

"if you're not sure, don't make up an answer" -> isn't that something we'd expect is in foundational models? If yes, why would adding it to our tuning offer any improvement?

This phrase was included in the prompt to the out-of-the-box foundation model. With tuning, you can potentially leave out instructions like this in your prompt, along with few-shot examples. A much shorter prompt will improve costs/speed

is a llm answering these questions -- LOL :P (thank you btw)

Haha! Nope, we're the tech team who created (and/or presented) the material, as well as other NVIDIA SMEs.

can u give a reference for Re-ranker?

https://www.sbert.net/examples/applications/cross-encoder/README.html

Can you elaborate on techniques for "tuning a QA model that explicitly only answers from context"? is it only prompt engineering that can be used?

Supervised finetuning methods (including PEFT methods) can tune the LLM to focus entirely on the provided context and not use facts learned during pretraining--it's all in what you show it in prompt-response pairs in training data

Are there any tutorials for fine-tuning your own models for your own data, since this code isnt available for public?

Please refer to the NeMo User Guide for specific tutorials on customization techniques. https://docs.nvidia.com/nemo-framework/user-guide/latest/index.html

What is the best way to fine-tune a LLM to gain knowledge in a field, in a non-English language, as Brazilian-Portuguese?

If the LLM was pretrained to include that language, then either PEFT or retrieval-augmented generation can add knowledge. If the LLM wasn't pretrained with that language, it'll take a lot more training data!

Is ChatGPT Enterprise self-managed?

All ChatGPT models run remotely (as a hosted API), but Enterprise added a few features that otherwise have been associated with self-managed LLMs

Any idea on the average GPU utilization, 80% etc.

Well, we shoot for as close to 100% utilization for a multi-GPU deployment. That way, the job completes as soon as possible. Optimized training runs can hit >90% efficiency.

For this RAG application arent you constrained by your context length? Is there an easy way to go around max tokens for the model?

While LLMs are always constrained by context length, but the size of the RAG database can be much larger, and you can certainly run multiple parallel LLM calls looking at different contexts, then synthesize the results.

On OpenAI function calling with json is not consistent, how do we fix it.

The new GPT4-turbo model from OpenAI handles JSONs better - trained for it.

what if I wanted my model to be more relevant to complicated technical topic, like molecular biology or organic chemistry? Would it be best to use RAG or fine tuning?

We'd suggest both! Fine-tuning helps the model understand the vocabulary, and RAG lets that model access up-to-date data.

are these UIs are part of the Nemo framework?

No, these UIs were written just for the demos. The presentor, my colleague, is masterful at creating UIs!

What does NeMo stand for

"Neural Modules"
