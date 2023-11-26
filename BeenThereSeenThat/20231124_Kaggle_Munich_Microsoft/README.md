# 20231124 Kaggle Munich at Microsoft HQ

* Hosted By Alexandre Moritz und Shabnam S.

```
Kaggle is a platform for data science competitions, where you can improve your skills and compete with others to solve real-world problems. Whether you're a beginner or an experienced data scientist, this meetup is for you.

Thanks to Microsoft for hosting and sponsoring the meetup!!

Agenda:
18:00 Welcome and registration

18:30 Talk 1: Ayoob Imani - His NLP research at Microsoft

19:15 Break

19:30 Talk 2: Oleksandra Sopova - Monitoring ML Models in Production

20:00 Snacks and networking

21:00 End of the event

See you soon!
We look forward to seeing you at the next Kaggle meetup!
```

## 1st talk: Ayyoob Imani - intern for MS - TODO add his title
* the CIS multilingual team - big group effort
* for 100 languages large corpora available, covered by main LMs
* 1000s of tail language little data available <-- check: "tail language" or "tail languages"
* out of 7k languages
* 1000MT is the only model which supports 1k languages
* Serengeti supports 500 African languages
* coverage of existing models: plus a few other large national languages: primary driver is business!
* but there is the need to support other languages: for preservation of other cultures
* or bread & butter basics: disaster recovery
* main challenge for tail languages: data scarcity, data quality
* data quality: leakage: tail language Welsh, head language English
* data leak from head lg to tail lg
* acc 99% with false positive rate 1%
* what about tail language data from the web: after some experiments decision against web crawling
* decision to rely on academia: ambition: as public as possible, what was published by other researchers
* our approach: stand on the shoulders ... all scattered, no central repo; LREC, ELRA, publications, follow all links
* data cleaning was a big effort: deduplication, metadata analysis to check for incorrect iso-code ..
* Glot2000: 2266 languages, 728GB
* Glot500: is a subset of Glot2000; criterion: more than 30k sentences; 511 languages, 534 language scripts
* model training: XLM-R base as starting point: vocabulary size: 250k + 150 (new) = 400k
* vocabulary size plays a big role in model size
* create evaluation datasets: we cover N languages - what does that mean?
* extensive evaluation of their models: pseudo perplexity, round trip alignment, sentence retrieval, sequence labeling, text classification
* todo: what means perplexity?
* the bigger the corpus size, the better the evaluation the model will give
* Bible scripts and translations as a way to compare languages
* the curse of multilinguality: train multilingual models: lose quality for different languages, because the same parameters are used for different languages
* if you add a single language; then it can be a problem
* factor tokenization; characters versus bytes
* byte-based representation better
* Zipf ceiling: once you get into the long tail of the Zipf curve, larger vocabularies don't help* you get into that long tail very quickly for tail languages
* so vocab extension is no easy fix
### lessons learned: licensing issues
* all data published on Hugging Face; also the trained model
* most tail language work on text is overwhelmingly dominated by religious text: thanks to missionaries (1)
* when there was bad performance on a language, in most cases the reason is poor data quality
* we should have invested more time in the beginning in LanguageID
* the definition and individualization of tail languages is a hard problem
* it needs to be a public community driven process (not done by industry)
* should be based on standards
* standards should include referenced text
## new id. method: GLotLid
* gltlid covers a broad range of tail languages
* currently the state of the art for language identification
* uses iso-codes
* support for script detection
* completely open source

* question: 8 GPUs with 48 GByte of RAM; two weeks of training
* just picked the languages based on the corpus size - rest was dropped
* basically, you could go from one tail language to the next tail language, but the best results come from "going from English to tail language"

[end of the talk]

## 2nd talk: ml models monitoring in production - Oleksandra Sopova
* funny twist: Kaggle is about the last percent not about stability in production
* how ml model can fail: data processing issues; data loss & logging issues; broken upstream or downstream model
* what is data drift? change in data distribution; users coming from a different cohort
* cold start-problem
* what is concept drift: churn prediction; change in underlying relationship (between features and the target)
* example for sudden concept drift: is the pandemic 2020
* also: gradual concept drift: in general the environment changes; but when it accumulates it becomes significant
* how to handle data & concept drift?
  * retrain
  * fallback strategy - postprocessing the output; for instance for spam-filter: a quick hack could help
  * monitoring: where to start?
    * service health
    * data quality
    * model
    * business KPI
* requires job which prepares data for some dashboard
* if you don't have this, you might have to implement this
* service health: does the service work? track model calls;
* data quality and integrity: where is it broken?
* rate of missing features: feature correlations
* model performance: how does the model perform? sanity check the ranges of the model output
* data and concept drift: is the model still relevant?
* business KPIs: how model quality impacts the business metric?
  * but must not be connected to the general machine learning case

  [end of the talk]
