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
* request to share this event to people we like (or don't like)

## Single-cell Perturbations - Dmitrii Rudenko
* team of five people: U900
* easy task: in terms of machine learning but not bio informatics
* several paelttes of in vitro human cells, lots of compunds
* cell type, compound (aracetamodl or L-alanine)
* Limma: special model for bio informatiks, to avoid batch effect and same donor effect
* their solution:
  * 1. special validation schema based on predictability
  * 2. catboost + pyoost: target encoding and quantiles, train bootstrappong, SVD decomposition of targets + inverse-trandform for test
  * 3. MLP: data augmentations with random noise, Lions as optimizer, BatchNorms + blottlenecks
* 6th place: used some Limma backransformation
* 3rd place: Optuna for optimizations; training on pseudo-labels; test-labels; use this as part of your own training cycle; predicted tests
  * questionable if this approach with raw power can be applied to other challenges and if it would perform there as well this good
* 2nd place: transformer, huber loss + lion optimizer
  * clustered all the data with k-means & stratified validation by k-means labels; mean target encoding as additional features
  * neural networks train neural networks
* 1s place:
  * parsed wikipedia  for gene/compond description
  * used biowordvec to create embeddings of it
  * used chembert embeddings of all inouts
  * logCosh + MSE + MAE + BCE loss

* bottleneck approach: from dense features sparse ones are deducted
* usually you ave to do good for  multi-regressional

* throwing away the T-cells was the most powerful trick; data-driven not model driven!
* do you want to read an artile about how people have not solved their problem?
