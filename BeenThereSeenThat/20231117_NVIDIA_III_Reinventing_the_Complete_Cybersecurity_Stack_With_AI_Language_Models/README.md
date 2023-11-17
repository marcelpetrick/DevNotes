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
*
