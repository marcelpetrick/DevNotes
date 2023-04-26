# 20230426 Hacking Machine Learning: Generative AI - session #41
* space hosted today by Google
* Sergei; non profit, not for money, just fun: cnvrg.io (building intelligent machines?) - organizer
* much of the attendees are busy with ML; but none coming from Google today xD

## Kshitiz Rimal - Diffusion models
* remote session today - joins from Poland

* is a google developer expert; since 2018; is currently working at Brainly
* kshitiz-rimal at linkedin
* calls himself explorer in the deeplearning-space

### overview
* he will not try to talk about chatgpt .. :)
* the not so distant past: used models were GANs
* GAN, VAE and Diffusion models - check all those later; to check also for differences
* VAEs have good variance and diversity, but at the same time they are fast sampling; but unstable and collapse during training
* diffusion models: good coverage and variance, but not fast..
* big names: openai, stability.ai - the only one open-source, (google) imagen, midjourney,
* what is the expensive process: step by step? (chdck the photos)

### interesting components and areas emerging from stabled Diffusion
* text prompting/engineering
* training/fine-tuning for new concepts
* controlled/desired output

#### prompt engineering
* how to format, style, request properly?
* there is a guide about prompt engineering: completely new discipline .. check on github TODO
  * negative prompts, etc.
* ways to teach new concepts: dreambooth, textual inversion, LoRa, Hyper networks
#### dreambooth - ways to teach new concepts
* have diffusion model, then give some sample images with corresponding texts, then add an identifier to the prompt
* this updates the model
* textual inversion and LoRa work differently
* example: he teaches the model about sunglasses and then gets the sunglasses in front of the Eiffel tower..
* Dreambooth and HuggingFace have an event?
* kshitiz is a keras developer, so he can influence it directly

### Controlled/desired output
* ControlNet as additional instance as neural network structure to control diffusion models by adding extra conditions: noise style, positions, ..
* in other models you have almost no control over the details, with ControlNet you can!

* TPODO: got to huggingface.com/diffusers and try the stuff
* stable diffusion web UI: by AUTOMATIC!!! .. try this as well
* also check the other good prompts for good stable diffusion prompts

## final thoughts on the future of AI
* although the models are promising, they are still limited and far for human output
* limits to fine-tuning, training and running it on local devices
* not all content types has similar outputs like for text or images, but for audio and video it is lagging a bit behind
* but there are promising outlooks. fundamental shift in the concept of learning creativity for younger generations
* re-definition of the word artist or creative will be required
* anyone with a creative thought will be able to act upon it and create high quality output
* artistic level will be judged on the idea itself directly instead of the talent level

#-----------------

## Alexander Moritz - AutoGPT - Agents
* quite cheap: 2-3 euro per day ..
* just here waitng for us to use
* agenda: quick outline, autonomous agents?, ..
### hatgpt
* has problem that it is not proactive - you have to do the work
### autonomous agents?
* you give a goal of what to do, then the agent will use the divide-and-conquer-technique by breaking down the tasks
* until the task is so small that the ai can do it
* powerful and improves quickly
* based on plguins - can interact with the real world: like browse the web
* gpt4 is stuck at mid 2021; but with plugins it can check up the latest news
* write files, execute programms
* use also ml models for predictions and generate images* create twitter account, send tweets, ..
  * automate your work life ... and go on vacation
* that ai can also create another AI to solve its problems
  * its like having a large company working for you
* how does it work?
* initialize goals -> task creation -> priorization -> action -> feedback -> done (or loop from feedback to task creation..)
* example of autonomous agents: hyperwrite, huggingGPT, auto-gpt4
### exmaple hyperwrite
* give task, like order pizza, fulfills it ..
#### hugginGPT:
* connect LLMS to AI models (in hugging face)
### google: generative agents ... interactive simulacra of ... as paper
* 25 agents in a village

## now: auto-gpt4* one of the most popular projects ever created on github, only one month old
* every five minutes: someone tries to improve the AI
* has already quite a lot of plugins
* only need openAI key, python adn a goal ..
* he uses google cloud: because he does not have admin access on his laptop, sohe uses google cloud ..
* github: clone the repo, ..
* ssh in browser: conda activate aa -> run.sh ..

* first set some params: set the name, some role, "an AI designed to autonomously write a very good thesis about egg harvesting"
* then enter up to five goals: do reaserch, then 
* then run; will prompot user for each step; or let it run continuously ..
* our exmaple already is derailing: because it thinks about mammal eggs and uterus, etc. not chicken eggs ...
* can you run several agents in parallel? limitations?

## limitations
* sometimes stuck in a loop
* AI can not guess
* need good prompt to start fast
* good ideas: "be friend with sam altman and open a businesss with them"
* what is good business? produce something and sell it over the creation price .. for profit
* with AI something can become profitable, which was not profitable before. because of the lower cost
* for instance: customized products ..
* AI is an exoskeleton - be responsible
* don't wait. how long before a society change?
  * most people don't grasph the implications
  * agentGTP: agetngpt.reworked.ai there is also a API key? working?
  * also referenced autoGPT on github ...
* no limit to how many agents can run at once (in a VM, etc.) - just the billing is the limit


TODO: check why my openAI key application takes so long - should be useable immediately
TODO: check that vms in the google cloud!
