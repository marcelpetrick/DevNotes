# 20231124 kaggle munich at microsoft
## 1st talk: Ayyoob Imani - intern for MS - TODO add his title
* the CIS multilingual team - big group effort
* for 100 languages large corpora available, covered by main LMs
* 1000s of tail langugage little data available
* out of 7k languages
* 1000MT is the only model whichsupports 1k languages
* Serengeti supports 500 african languages
* coverage of existing models: plus a few other large national languages: primary driver is business!
* but there is the need to support other languages: for preerveration of other cultures
* or bread&butter basics: disaster ecovery
* main challenge for tail languages: data scarcity, data qauqlaity
* data quality: leakage: tail lanauge welsh, head language english
* data leak from head lg to tail lg
* acc 99% with false positive rate 1%
* what abut tail language data from the web: after some experiements decision against web rawling
* decsion to rely on academia: ambition: as public as possible, what was published by other researchers
* our approach: stand on the shoulders ... all scattered, no central repo; LREC, ELRA, publications, follow all links
* data cleaning was a big effort: deduplication, metadata analysis to check for incorrect iso-code ..
* Glot2000: 2266 lanuages, 728GB
* Glot500: is a sbuset of Blot2000; criterion: more than 30k sentences; 511 languages, 534 language scripts
* model training: XLM-R base as starting point: vocabulary size: 250k + 150 (new) = 400k
* vocabulary size plays big role in model size
* create evaluation datadsets: we cover N languages - what does that mean?
* extensive evaluation of their models: pseudo perplexity, round trip alingnment, sentence retrieval, sequence labeling, text classification
* todo: what means perplexity?
* the bigger the corpus size, the better the evaluation the model will give
* bible scripts and translations as way to compare languages
* the curse of multi linguality: train multilingual models: loose quality for different lanauges, because the same aprameters are used for different languages
* if you add a single language; then it canbe a problem
* factor tokenization; characters versus bytes
* byte-base representation better
* zipf ceiling: once you get into the lon tail of the Zipf curce, larger vcabularies dont help* you tgt into that long tail very quickly for tail languages
* so voc extension is no easy fix
### lessons learned: licensing issues
* all data published on hugging face; also the trained model
* most tail language work on text is overwhelmingly dominated by religious text: thanks to missionaries (1)
* when there was bad performance on a language, in most cases the reason is poor data quality
* we should have invested more time in the beginning in LanguageID
* the definition and indivdualizatio of tail lanauges is a ard problem
* it needs to be a public comnuity driven process (not done by industry)
* should be based on standards
shatanrds hsould include refernced tet
## new id. method: GLlotLid
* gltlid coves a broad range of tail lanauges
* currenty the state of the srt for language identification
* uses iso-codes
* support for script detection
* completely open source

* question: 8 GPUs with 48 GByte of RAM; two weeks of training
* just picked the languages based on the corpus size - rest was dropped
* basically you could go from one tail lanauge to the next tail lanague, but the best results come from "going from english to tail lanauge"

[end of the talk]

## 2nd talk: ml models monitoring in production - oleksandra sopova
* funny twist: kaggle is about the last percent not about stability in production
* how ml model can fil: data processing issues; data loss & logging issues; broken upsstream or downstream model
* what is data drift? change in data distribution; users coming from a different cohort
* cold start-problem
* what is concept drift: churn prediction; change in underlying relationship (between features and the target)
* example for sudden concept drift: is the pandemic 2020
* also: gradual concept drift: in general the environemnt changes; but when it accumulates it becomes significant
* how to handle data & concept drift?
  * retrain
  * fallback strategy - psotprocessing the output; for instance for spam-filter: a quick hack could help
  * monitoring: where to start?
    * service health
    * data quality
    * model
    * business KPI
* requires job which prepares data for some dashboard
* if you dont have tis, you might have to implement this
* service helath: does the service work? track model calls;
* data quality and integrity: where is it broken?
* rate of missing features: feature correlations
* model performance: how does the model perform? sanity check the ranges of the model output
* data and concept drift: is the model stil relevant?
* business KPIs: how model quality impacts the business metric?
  * but must not be connected to the general machine learning case

  [end of the talk]
