# 20230629 Kaggle Munich June 29th 2023

## Details
```
Kaggle is a platform for data science competitions, where you can improve your skills and compete with others to solve real-world problems. Whether you're a beginner or an experienced data scientist, this meetup is for you.

Thanks to Alasco for hosting and sponsoring the meetup!!

Agenda:
18:30 Door opening, pizza arrives, drinks, casual welcoming
19:00 Quick Introduction - 3min + 2 mins welcome words from Alasco
19:05 Talk 1: Can large language models reason by Shabnam Sadegh (Microsoft) - 55mins
20:00 Break 5-10mins
20:10 Talk 2: Time Series Forecasting with FB Prophet by Ena Dzemila (ML Reply) - 30mins
20:40 Food and Drinks + Networking
21:30 - 21:45 End of the event

Descriptions:

    Can large language models reason by Shabnam Sadegh (Microsoft)

Shabnam will talk about the extent to which the large language models can demonstrate reasoning abilities, a key indicator of intelligence. We cover the literature on how to bring reasoning into the LLM-based applications via in-context learning (prompt engineering).

    Time Series Forecasting with FB Prophet by Ena Dzemila (ML Reply)

An exploration of the FB prophet library and its capabilities via a brent oil prices kaggle dataset.
```
## Alasco
* 120 people, 35 engineers

## Can large language models reason?
* data & applied scientist at microsoft
* Agenda:
  * reasoning
  * benchmarks
  * techniques
  * practical tips
* TODO: insert the photo with the qr-code
* code:
* talk will be mostly  review of literature, not a product promotion
* criterias for picking: single-stage over multi-stage; has real world application; in context learning / prompt engineering over fiene tuning

### why do we need reasoning?
* generate code
* self criique
* problem solving
* planning/priorization
* plugin/tool use

![](img03.png)
* arithmetical reasoning
* commonsense reasoning
* logical reasoning
* multi-hop question answering

examples from common benchmarks (titles as foot lines)
img04
* arithmetic calculations quite doable; commonsense reasoning, deductive (based on relationships of people)
* Qiao, Shuofei: "REasoning with Language Model Prompting: a survey" (todo: check this; google "paers with code")
### most common idea: chain of thought
* img05
* standard prompting versus chain of thought-prompting: compared models GPT, LamDa, PaLM
* few shot prompting: giving the model some rational behind the question, then the results improve
* when the LLM starts with rationalizing, then the end result is more often true

### LLMs are zero-shot reasoners
* even if you do not give the reasoning as example,, it improves
* trying different ways of instructing the LLM gives different quality for the result
* misleading ones decrease the results as well
* irrelevant gives the same results like no instructions - so there is a bit of knowledge inside the LLMS

### self-consistency
* img07
* todo: add the algorithm from the image
  * "aggregate by choosing the most consistent answer i the final answer set""
* good way to tweak the responses to improve the obustness

### DIVERSE (diverse verifier on reasoning step)
* step 1: diverse prompts
* step2: step-aware voting verifier
* majority voting could also lead to wrong results, because something is common-sense, but wrong
* therefore use maybe a smaller LLM to verify the answer: so that the results are better than with "self consistency" -> gets to 82% accuracy

### self-verification
* img08
* use the same LLM for verification

### faithful chain-of-thought reasoning
* paper came out at the same time
* when you can verify something statistically why use another llm?
* model writes code, which can give the answer: therefore more powerful (by running the code)
* two aspects: just asking the model to give the results in python language gives more correct results and second their claim is that if you can compute results, why then use a model?
* temperature as influence: if you are aiming for accuracy, then the temperature goes down
* add "answer this in python" to the prompt - this is everything

### least-to-most prompting
* query the LLM to decompose the problem into subproblems, then 2: query the llm to solve sequentially the subproblems
* img09

* all the presented approaches deal with the accuracy of the answer

### self-refine
* img10
*  check the given prompt for acronym generation
* feedback is not just self-critique, but it actually asks for some different criteria:
* "iterative improvement with self-feedback"

### question from the audience: why do those reasoning-optimizations  are working?
* because of transformers; because of code? or is that the training data contains better answers?
* will this stay valid with upcoming models?
  * due to the continued training of models and their fine-tuning they know about those approaches: davinci -2 knew about CoT .. therefore the results became better compared to the initial version
  * why is the code optimization done? (other visitor says that this is a good question): step-by-step approach reveals new data; memorization is not the only cause
  * "bevharioural science on a model": because analytical approach is a bit grey matter
  * "how does in-context learning work?" - check for this paper
    * idea is quite similar to back-propagation
* what happens withs slightly wrong intermediate anaswers? then the LLM can quite good rationalize
  * hypothesis: metaphorically the model is buying more time to think -> more time results in more correct answers (!)

* things which were not covered today: RL, fine tuning; grounding / retrieval argumented

### Take aways (summary)
* img11
* TODO cross check with the image!
* many LLms can benefit form CoT
    * include a thought section in your prompt besides the desired response
    * it gives the model some capacity to think
    * it helps with debugging sometimes as well
* setting the tone seems to be important
  * you are a perfect mathematician ..
* make your result more reproducible and reliable by self-consistency or similar approaches
* cheaper fine-tuned models as a prompter
* comparison needs less cognitive effort
* auto verifiers: deterministic ones or model based ones
* LLM can be LM teacher: data augmentation via LLMs


* struggle to have good quality training data: now lLM can be used to improve the less quality trainng data; to have better augmented training data to use to train smaller LLMs; to our benefit
