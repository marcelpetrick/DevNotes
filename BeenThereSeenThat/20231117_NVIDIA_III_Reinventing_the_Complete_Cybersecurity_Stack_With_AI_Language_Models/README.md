# 20231117 NVIDIA III - Reinventing the Complete Cybersecurity Stack With AI Language Models
* speaker: Bartley Richardson, PhD; Director, Cybersecurity Engineering; NVIDIA

----


* cybersecurity a language problems
* security specific copilots
so what? how we can deeply integrate LMs
three layer sof stack where language models work
what to take away

#representing cyber problems as language problems
* not a new idea
* tracks all the way back to agent based modelling
img00

* chain of markov models
*any sufficeintly represented model would suffer from vocabulary explosion for available memory
* LSTM: lacked enough context for complex assocations

* language models: powered by transformer architecture
* transformer architecture allows sufficient context window (with attention) to learn simple tasks and small corpus
* high utility and success when the target domain is small and limited in scope; small context window is adequate to ive salient results
raltive number of tokens is small or can be restraing
img02
* exampl applications cor CS incluide:
 * log parsing (cyBERT)
 * root ause analysis
 * basic anomaly detection
* architecture fails, when even more additionl context/tokens neededor when domain becomes large

## copilots
* "this talk is not an LLM talk"
* this is about how we can harness their power
* how to solve real world-cyber security problems
* three critical issues are adressed and are the easy button of tLLM integration:
  * address the staffing shortage: staffing is already low, and copilots allow analysts to be more efficient and effective
  * democratize expert service: customers can obtain near real-time answer and guidance to complex deployment scenarios
  * natural interface for customers/users: no need to struggle with complex query languages - natural language is the ultimate interface
* query, filter, pivot: over and over again - while investigating an incident
* a copilot can pull together a lrge amount of information, which allows better incident response
* also: upskilling existing staff
img00
* key challnge for decurity copilots
* maintain topical responses
img00
+ migitate hallucinations
* maintain up-to-date information


# gernatie AI knwoledge BASE chatbot (based on RAG)
todo: image - rag
* integration of language models deeper in the cyber stack
todo: image of integration
* generic cyber + llm stack architecture
todo: image! of the stack

## CVE explitability and vulnerabiltiy analysis
* dramatically improve vulneravbility defense with generative AI
* it matches a human analysit with 85% accuracy:but with faste time, not basd for the first version; 4 times faster
* reduction in CVE-noise
todo: image
* CVE explotability using the LLM engine
* is CVE-2022-42890 explotable in morpheus v23.07.00a?
todo: image
* an initial query goes to the system, then gernerates information, ... which culminates in a human readable conclusion
  * see the evaluation: run 0
  todo: imgage: of the run
* several runs: now checklist item 2: can the vulnerable component be executed? find the requirements to run apache batik. verify the container is
* running htese requirements. action: internet lookup; back to the top - task generator: search java runtime environment using sbom QA system ..
* .. presence does not always mean exploitability!
* traditional RAG architecture:
todo: image
* tweaked version: need an always on service and as many resuable compoents as possible
todo: image
* langchain or lama index can be used directly i that design

### foundation models for cybersecurity
* shared over the coming months (by NVIDIA)
* enable next-generation models and detection via three key modalities:
  * address the data gap
  * perform "what if" scenarios
  * feed downstream anomaly detectors
*example: CyberGPT:
todo image
todo image2
* cyberGTP training times: 2 GPU hours for GPT-2 modell with character level tokenization
* choices for the tokenizer
  * charactler level tokenizer; off the shelf tokenizer; train custom tokenizer
todo: image tokenizer
* demo: cyberGPT-demo ..
* also the possibility to create high quality syntehtic data
  * create content at scale; multiple types of models and architectures, harness for increased data visibility and availability

### how can models be trained for spear fishing campagins
* low volume, high success
* syntehtic data genration for spear phising: default models trained for off-the-shelf intents

------

## Q&A

In what ways do generative AI models contribute to addressing the data gap in cybersecurity, and what are their limitations?

Great question. One way is via synthetic data generation especially for rare events. Think about how in healthcare there may be limited data for some rare conditions, and we can generate much more data based on limited samples. Also similar to how we would do image augmentation to help train image classifiers. So using this synthetic data (e.g., spear phishing) we can train lightweight detectors. And we don't have to wait for that data to become available in real life - moving from reactionary to more left-of-exploit. Of course a limitation is quality. So there has to be a mechanism to ensure quality of the data and that the data is "on topic." This is still an ongoing area of research, but we present one possibility towards the end of this session.

How does the integration of LLMs into cybersecurity tools like Morpheus and NeMo enhance their capabilities for threat detection and response?

In addition to synthetic data generation, we can allow system to perform complex sets of operations (think something similar to AutoGPT if you're familiar), where the system is answering questions itself, pulling context from additional sources, and writing prompts automatically. This helps accelerate the jobs of human analysts.

With the prevalent use of LLMs by threat actors for phishing, how do you assess the potential escalation of AI models being applied to more technical tasks, such as patch differential analysis to bypass security fixes, or training on large malware datasets to develop novel variants of existing malware families? What are NVIDIA's insights on mitigating these advanced AI-driven cybersecurity challenges?

This is a really good (and legit) question. As you allude to, any offensive capability can be used for defense (and vice versa). Adversaries are already using these technologies for offense, but we have yet to fully embrace them on the defensive side. That's step one - we need to at least match current offensive capabilities. One advantage that the industry has is its workforce though. We have cybersecurity experts, and these same technologies can be used to up-skill that workforce (give them superpowers).

Can these models be used to combat bots prevalent on social media?

If there is an appropriate data set, then it would generalize to that. There's another workflow we have that we don't talk about today called Digital Fingerprinting. We're working right now to combine telemetry from foundation models (synthetic data) into a Digital Fingerprinting workflow. (https://www.nvidia.com/en-us/ai-data-science/ai-workflows/digital-fingerprinting/)

What specific challenges in cybersecurity are addressed by using LLMs, and how do they compare to traditional cybersecurity approaches?

LLMs in cyber security provide the option for a natural language interface to vast datasets for a group of users who are not necessarily data scientists. For example, there are large repositories of cyber threat intel. Democratizing rapid access to that knowledge base offers economies of scale for Security Operations Center teams.

does using differential privacy(DP) and SMCP( Secure Multi-party Computation) in Federated Learning are enough to maintain the security and privacy in AI models?

Perhaps for privacy, although privacy still is (IMO) better in layers. For security, we also want to make sure that models are encrypted (both at rest and during transmission), and that we can provide clear attestation that the model does represent the data it was trained on.

LLMs are large and not (to the best of my knowledge) suitable for in-line inference. Does this approach solve that?

In these instances, we're not advocating for placing a LLM directly in-line with your data (at line rate / at bandwidth). Instead, they would be used to quickly and accurately train downstream detectors - large models training smaller, highly targeted models.

Are there still uses for the earlier language based approaches, or does everything now become a LLM application?

100% there is still room for other approaches. LLMs are extremely powerful and have great applications, but they don't undo the benefits from traditional ML/DL and even statistical-based approaches. As always, defense in layers - and right tool for the right job.

Considering the comprehensive integration of AI language models in cybersecurity, as outlined in this presentation, I'm curious about your anticipatory strategies against adversarial attacks targeting these AI systems. How are you preparing for scenarios where threat actors might exploit the AI's inherent vulnerabilities or biases to undermine cybersecurity defenses?

Very appropriate question. The answer is complicated, but it does come down to layers. For example, we would rely on attestation and encryption (at the model level, even when in use) to provide a guarantee the model hasn't been tampered with. On the data side, the immediate approach is to hash datasets and compare against a known hash (also useful for models). Hashing, encryption, and signing do go a long way, but there will be edge and corner cases. Part of this will rely on the human to evaluate the system, and that requires accurate telemetry and explainability. We're putting efforts into those areas as well.

does all this mean that security teams needs a prompt engineer and a RAG engineer in house ?

Not necessarily. There's an example coming up where we show how prompt engineering can be placed "in the box".

Do you think there is an issue with anthropomorphizing LLMS in that it promotes a false sense of intelligence and perhaps a false sense of trust in LLM responses?

I do, and I'll admit I'm guilty of this from time to time - e.g., they "hallucinate". As security professionals, part of our job should be to reinforce applications where LLMs have utility and those where perhaps we have other modalities that work well. A first step is realizing that they're not magic and don't solve all problems (the phrase I like to use is "it's math, not magic"). Knowing and conveying the limitations of LLMs is key. One way we can help here is discuss them in terms of very specific use cases.

Would you please share resources on prompting models for cyber uses? Human Language Interface is a great concept. In practice, each LLM has a unique prompting approach. Anyone who has compared LLAMA2 and GPT4 knows that skillful prompting means the difference between a meaningful answer and gibberish.

This is a great question. It goes even deeper than cyber use cases, and when we switch LLMs (and prompts) it can lead to sub-optimal results. Specifically for cyber, we'll have more to share in the next few months (especially around our foundation model work).

Could you discuss the specific use cases where LLMs have successfully improved cybersecurity operations, especially in terms of risk assessment and mitigation?

We have one coming up, but we have a CVE exploit analysis and vulnerability POC where we see a 4x improvement in speed to mitigate (vs. a human alone).

I assume by "noise" you are including false positives, correct?

Correct

so what you are saying is we can make our own in foundry?

You can, yes.

what part calculates the cve score with out human input into the scoring criteria ?

We're not necessarily calculating a score with this workflow. We're seeking to help the human collect and verify that a CVE isn't exploitable in a given container. That said, if you have a scoring mechanism internally for CVEs that you use (or integrate from a feed), that is another data source that can be integrated. We do that internally with our bug/ticketing system we use for this purpose.

Where do I get this LLM Agent

Please stay tuned for the 23.11 release of Morpheus that will include this functionality.

Is prompt injection something you have to sanitize, or does the LLM Engine have safeguards in place for it?

Those can be integrated directly into the LLM Engine, but our recommended way would be to place this safeguard closer to the LLM itself. For example, we used NeMo Guardrails in our testing for this purpose: https://github.com/NVIDIA/NeMo-Guardrails

Does task generator has access to sandbox env to excute commands

It can. In our example here, we haven't done that. But if there exists a sandbox that you have a defined API for, that is simple to hook up with a source/sink node.

Greetings, who trains the task generator? thanks

It's customized per the application. There's a combination of logic there as well, that is expressed as simple data science workflows. We have another application of this (similar to CVE) that has different tasks, and we rely on SMEs to help us train the tasks that are possible.

Just out of curiosity, on average, how many iterations of this loop are run for a typical CVE query

It varies quite a bit, depending on how many transitive dependencies are there and how many items on the checklist have to be finalized. Typically though it's <= 10.

Why not skip the first 3 steps and get the answer by simply scan the docker itself ?

Good question. In this case, the underlying requirement (the JRE) wasn't mentioned in the original CVE text. The only thing we knew from the advisory was that it was present in Apache Batik. Creating the checklist and then executing on it mimics what a human container dev would do in this case. There are also some much more complex scenarios (multi-level transitive dependencies) that are more difficult to answer.

Will this topic be released in the form of a blog or repo?

The LLM engine we're releasing a EA version in Morpheus as part of the 23.11 release (end of this month). For spear phishing, we have a inference workflow available as part of NVIDIA AI Enterprise. We have a tech blog going live on 11/27 that covers these topics as well.

Question: How often would a foundation model need to be updated? How would I know that the foundation model needs updating? How can we automate the process?

That is a *fantastic* question. There's not one answer here, but I can tell you what we've seen. When you train a foundation model for a specific (narrow) set of tasks, we don't see it needing to be updated often. In fact, you can get by with SFT or RLHF most of the time (after it's trained). How you know this though depends a bit on the scenario. I answered a question earlier about Digital Fingerprinting. In these instances (where we're using synthetic data to train downstream detectors), we monitor model drift (specifically concept drift). The nice thing here is it maps 1:1 to how we would know any ML/DL model needs to be updated. There is no solution (in my opinion) yet for taking humans completely out of the loop. SMEs will still look at the concept drift and make that determination. We do provide mechanisms to then retrain those models (or fine-tune them).

Is CyberGPT model publicly accessible or a proprietary?

We haven't made it available yet since it's still a work in progress. We'll have more to share on it early next year though!

The trend in foundation models is multimodal transformers capable of producing both text and image output. Will morpheus 2.0 be able to generate graphs and related images that will help in reporting?

Hey David! That's an interesting point. I don't think that would be built into Morpheus proper, but that would be an integration we could provide and yet another use of the LLM integration (which I think is great). I'm writing this down though as this is an interesting idea.

Is there training available so developers can more easily get familiar with these use cases?

Check out the NVIDIA Deep Learning Institute where we have a free 1-hour course https://courses.nvidia.com/courses/course-v1:DLI+T-DS-02+V2/

Given the reliance on vast datasets for training AI models, what protocols (legislative or applicative) should be put in place at to ensure data privacy and compliance with global data protection regulations?

This a great question which requires a larger form to highlight all the many efforts happening to address data protection. However one way NVIDIA is working towards trustworthy AI is with model cards ++. You can learn more about it here: https://developer.nvidia.com/blog/enhancing-ai-transparency-and-ethical-considerations-with-model-card/

How do you manage to preserve privacy in generated data? Utility seems to be good, but we also should think about privacy when using LLMs to generate synthetic data.

Absolutely, completely agree. One way is by making these models highly targeted. We wouldn't want to release our CyberGPT model (as is) since it contains all of that PII. However, for a cybersecurity ISV, having these models that do have some notion of individuality in them can be beneficial. There are all sorts of ways we can protect those models (e.g., encryption + hash + verify, attestation), which go a long way. And I often make the point we all know - all of the existing best practices for access control don't go away when you have a LLM in your system.

Be good to see the speaker address OWASP's 10 most critical large language model vulnerabilities.

This is a good point. We'll work some of these into a future version. We do allude to some of them (e.g., LLM08 - excessive agency and LLM09 - over reliance). This is why we advocate for this being a tool for humans (and letting the expert make decisions). Some of the rest of them (e.g., LLM02, LLM01, LLM07) can also be addressed with tools like NeMo Guardrails. But I like your suggestion.

Will the model identify bad data to avoid being poisoned? How can data poisoning attacks be avoided or mitigated?

This is an ongoing area we're working on, and a valid point. We have some ideas on how we can identify what this bad data (e.g., intention poisoning), such as comparing key aspects to a known good dataset. In addition, we believe that retraining may not be necessary all the time - and a lot can be done with p-tuning (which doesn't adjust the model weights).

