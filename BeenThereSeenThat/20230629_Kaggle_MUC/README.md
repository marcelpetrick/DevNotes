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
*
