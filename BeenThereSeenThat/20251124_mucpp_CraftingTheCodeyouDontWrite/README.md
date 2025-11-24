# 20251124: mucpp - Crafting the Code You Don't Write: Sculpting Software in an AI World

```
Crafting the Code You Don't Write: Sculpting Software in an AI World

Veranstaltet von Andreas W. und 2 weitere
Photo of MUC++ group
MUC++
4.6
3.197 Bewertungen
Details

Sponsor: Brainlab (http://brainlab.com)

Streaming Link: https://www.twitch.tv/mucplusplus
Stream starts around 19:00 CET.

******
This month we have the big pleasure to welcome Daisy Hollman to our user group. Daisy is a distinguished software engineer and programming language expert, known for her impactful contributions to the C++ standards committee since 2016. She has worked on C++ language and library design at Google, and more recently joined Anthropic, where she explores the intersection of programming languages and AI systems.

******
Abstract
It’s shockingly uncontroversial to say that the fields of developer experience and developer productivity have changed more in the past six months than in the 25 years before that.

As part of the Claude Code team at Anthropic, I’ve had the privilege of witnessing the evolution of agentic coding from proof-of-concept experiments to nearly autonomous software engineers in just six months. In this keynote, I’ll share some of my experiences and learnings from that journey, talk about how LLMs work more generally, attempt some live demonstrations of the latest functionality, explore the future of agentic programming, and tie all of this back to what it means for your workflow as a software engineer.
​
When I agreed to give this talk earlier this year, there was some portion of the narrative that involved “why you should be using agents to accelerate your development process.” Since then, the world of software engineering has evolved such that the interesting question is no longer “why” but “how.” Like sculptors facing the invention of power tools, or painters around the invention of photography, we now live in a world where vast quantities of rough-draft code can be generated with a very low barrier to entry. How does the role of a software engineer evolve when AI can autonomously implement features from requirements? How do we build safety features into the power tools we’re chiseling away at our codebases with? What aspects of software craftsmanship become more important, not less, in an age of abundant code generation? And critically for the C++ community: how do we leverage these tools where correctness and performance are non-negotiable? The future isn’t about AI replacing programmers, but about a fundamental shift in how we think about software creation. And surprisingly, you might not miss the old way of doing things.

******
Schedule
18:00 -- Dinner @ Brainlab
19:00 -- Welcome by Brainlab/MUC++
19:05 -- "Crafting the Code You Don't Write" (Daisy Hollman)
21:30 -- Official End
C & C++
Programming Languages
Computer Programming
Software Development

Brainlab AG

Olof-Palme-Straße 9 · München, BY
```

## talk
* dr. daisy hollmann - daisyh.dev/talks/muc-meetup - from Anthropic 
* maybe 80 people in the audience
* long time c++mcommittee member
* also former cppcon program chiar: one of the cpp people
* joined in 2025 anthropic, working on claude code; has now an office here in munich as well


## goals:
* understand llsm aand coding agents at a high level: espeircially that parts which are relveant and how to use them to wirte code
* learn to thin about coding agents as a tool
* improve your emntal model forow and why llms make mistakes
  * and learn how to anticipate and avoid mistakes
* learn how to lear: to use coding agnets more fficiently
* geek about the future of c++ and where coding agents fit n that picture

## how to llms wrok?
* 2017 transformers -> 2018 early pre-trained models -> 2019 scale -> 2022 alignment -> 2023 tool use -> 2024 reasoing -> 2025 agents
* archteitecture: embedding lsyers tuns tolen into vectors, context window (fixed at training time); embedding dimension
* teh context window is the make context the model can thin about at a given time
* transformers build connections between related tokens that mayb be far from each oter in th input
  * abrraction as connection of tokens in different layers
* output of te model is a probalbilit distribution of ossible next tokens
* the model coses the next toen based on ths distribution: the temperature contols how random the samling is
* llm pretraining: start with random weights; then look at some toens; look at the probsalibily distribution o of the ext tokns, then compare them
* 2019: push towards larger scales; gpt-2 1.9 billion parameters
* pretraining is a compression of the trainng parameters, lossy compression
* emergent behaviours and unreasonable effectiveness of scale: completions for return values ... randomness or understanding?
  * C++ is about living with our bad decisions
  * 4.5 haiku had a 100% prdiction rate
  * why are more sophistic models get this worse?
  * compression through conceptual generazation is a useful metaphofor understanding how pre-trained models store (context?)
* peovlwm qith pretrained models. gloified auto-complete?
* traINING LLMS: REINFORCEMENT LEARNING
* comparison of pull rquets run experiments of ull requests, then rate them
* use older model to rate results; nothumansd anymore; use a "preference model"
* competing agents: games; winning agent can set up the reward; no reward hacking
* acquire a defucnt startup - get hands on their data and source code; open source repsitories
* also sometimes handwritten casess and rating them helped for claude code
* tool use: we are in the èd`era of agentic tooling: we haven't eveninvented `vi` yet
* most llms use xml-based sysntsx for tool invocation for now
* if the old_string is wrong, then the tool call fails: ifthere are multiple old_strings, then it fails as well
* xml a bit beter to train on than json
* TODO add the url fot the aNTML
* anthropic does everything on slack: problem with tool calls inside the answer
* context window sizes overt time: gpt1 512 tokens; gpt-4 32 k tokens; claue 3 2024: 200k tokens; gemini 1.5 mio tokens ..
  * sweet spot for 200k and 1 mio tokens
  * there is something fundamental for the transformer architecture: a way is needded to ut more relevant information into the cotnext window in order to make the output better
  * automatic injection of 2let me think this step by step" - improves output wuality by just injecting those strings into the sequence
* metr: agent task length grows over time: u to 30 hours
* agents: ode sarach tool: how to agents udnerstand 1m+ line codebase with only a few hundred thousand tokens of context?
* how do humans do this?
* search code through key enty points: check what is called by those types and data strcutures
* claude code explores clang .. and how and where to impelment something where at the code ...
* doom debugger? ud? wrap claude code? "when was the second zombie killed inthis playthrough"? - has source code and the traces?
  * so claude code steps throigh the traces and then tells when the second thing s was killed
* her agi pill moment: do an improvement of a tool before even get introduced to the code base
* "a coding agent is like ajunior engineer who has read the whole internet"
  * struggle often with large scale tasks; struggle with lots of stakeholders
  * LLMS overperform on highly arcance tasks; pretty good with build ystems, know cpmpiler intrinsics; 

* mods of operation:
  * rapid prototyping
  * side quests ..
* planning and brainstorming; helping with writer's block
* modernization, cross translation work wel; refacroring not
* you write the core logic; the ai writes everything else
  * your focus: core algorith;, architecture and code strcuture; design and strategy; securit llgic
  * ai's work: build system configuration, benchmarking harnesses, error handling boilerplate

## best practives: don't be surprising
* if the llm is guessingthe effets of your function incorrectly, maybe it needs a beter names
* avoid clever operator overloading
* dont mix owning and non-owning semantics of the same typs
* avoid macros
* avoid argument dpendent lookup
* use regular types whereever possible
* create, document, and maintain rigorous invariatns at encapsulation boundaries
* comment your code: comments are more important for agents thanthey are for humans!
* frequent verbose comtns can act like extended thinking
* redundancy is useful!
* agents are very good at generating and maintaingin comments
* add a CI step tat asks an agnt to verifiy all of the coments related to changes in your oull request

## beyond interactive use
* inreractive use of agents quickly becomes bottlnednecked by the human in the loop
* this mode of use wil always produce the most productivity per token
* huamns dont scale well
* parallel subagents: PR review toolkit as plugin all of this is free; except the used tokens)
* claude code plugins: allows to istall collecions fo slash commands, skils, subagents, hooks, etc.
* detach yourself fro being in the loop:m look ahead, not just do

