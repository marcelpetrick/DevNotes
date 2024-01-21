# Kaggle Munich January 19th

```
Thanks to Concept Reply GmbH for hosting and sponsoring the meetup!!

Agenda:
18:00 Door opening
18:25 Introduction
18:30 Kaggle Open Problems – Single-Cell Perturbations: Write up of 13th place and lessons learned by Dimitrii Rudenko (45 min)
19:15 Review current Kaggle Competitions, how to start and team building (30 min)
19:45 Networking + Pizza (30 min)
```
## Intro by Alexandre Moritz
* Request to share this event with people we like (or don't like)

## Single-cell Perturbations - Dmitrii Rudenko
* Team of five people: U900
* Easy task: in terms of machine learning but not bioinformatics
* Several palettes of in vitro human cells, lots of compounds
* Cell type, compound (paracetamol or L-alanine)
* Limma: special model for bioinformatics, to avoid batch effect and same donor effect
* Their solution:
  * 1. Special validation schema based on predictability
  * 2. Catboost + pyboost: target encoding and quantiles, train bootstrapping, SVD decomposition of targets + inverse-transform for test
  * 3. MLP: data augmentations with random noise, Lions as optimizer, BatchNorms + bottlenecks
* 6th place: used some Limma back-transformation
* 3rd place: Optuna for optimizations; training on pseudo-labels; test-labels; use this as part of your own training cycle; predicted tests
  * Questionable if this approach with raw power can be applied to other challenges and if it would perform there as well this good
* 2nd place: transformer, Huber loss + lion optimizer
  * Clustered all the data with k-means & stratified validation by k-means labels; mean target encoding as additional features
  * Neural networks train neural networks
* 1st place:
  * Parsed Wikipedia for gene/compound description
  * Used biowordvec to create embeddings of it
  * Used chembert embeddings of all inputs
  * LogCosh + MSE + MAE + BCE loss

* Bottleneck approach: from dense features, sparse ones are deduced
* Usually, you have to do good for multi-regressional

* Throwing away the T-cells was the most powerful trick; data-driven not model-driven!
* Do you want to read an article about how people have not solved their problem?
