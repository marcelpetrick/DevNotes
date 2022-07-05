# 20220705 EdgeMLSeries EdgeImpulse Munich Day 1
* maybe 40 to 45 participants based on the confirmed invitations
* handled in 6 cities; aim: vivid discussion what is happening in the edge-world

## Edge Impulse - an introduction
* advanced ML for every solution
* director for sales: Mihail Ruhalic
  * hit 2019 at the embedded world the ML technology; but was not sure if this will take off; did not believe this, but joined them two months later
* Amir: 20 years of development experience with Arrow(?); .. and others
* Edge: Impulse founded in 2019, two guys from ARM
* help:
  * build real world datasets at scale (autolabelling, versioning, structuring)
  * develop custom ml solutions fast (signal processing, data extraction)
  * deploy intelligent edge products
* everything produced should be open source; right now 40k develops on platform, 85k projects, 1k enterprises

ml solutions:
* wearables (Oura): voice commands, health prediction, activity detection, gesture recognition, acoustic event detection
* spaces: voice commands, fire detection, acoustic event detection
* industry: pdm - motors

* product is a Saas-platform in the cloud, but output is a c++ model
* not loyalty driven: 1 or 1k does not matter; your IP stays your IP, no impact on BOM
* entreprise license: 12 month; monthly fee; 3ke for platform, 5ke for solution help; if there is the urge and need to do things fast
* any sensor, any data, any use case
[img00 from phone]
* FOMO as new architecture; faster objects, more objects
* lots of automation for data collection
* output optimization (not just model, but the dsp as well)
* also link device for live inferencing: because ML is always some iteration-process (professional standpoint), because not all data sets in one point covered
* eg. a tesla six years ago is from software much different to one from today; loop is very important
* EI is not alone: they are aware of the competitors, EI can be run in a docker container
* hedge against silicon shortage: their EI environment allows to convert models from specific hardware to some different one without much trouble (not hw bound!)
* main flow: input data (resize images, slice timeseries into windows); preprocess data (signal processing, ..); learn from data (neural networks, classic ml, transfer learning); -> get some model which does 60 to 80% what it should do -> still some homework, but it does what it should
* auto labeling tool:  first label minimum set, then sorting into buckets, then just retrain the model and use it to label the next data -> until everything is clustered into buckets; 
* CHECK THIS: currently in progress: active learning capability of models
* optimal ML solutions with EON Tuner: how do you know which model is the best model? you don't know; so an engineer tries to tune the hyperparameters (chance to burn lots of time..); they do a slightly different approach by also checking the DSP side
  * 20 to 40 models as result; optimized for different specs: accuracy, latency, RAM footprint, flash footprint
* FOMO: ARC DSP @ 400 MHz at 11 fps; or RPi class with 60 fps
* total explainability of the model: parameters, layers, .. in contrast to Cartesium (STMicro): needed for cause and effect relations
* active learning: like calibration as in field model optimization

## ML 10 years ago and ML today
* 1763 bayes theorem: statistics
* 1805 least squares method
* 1913 Markov chains
* 1943 artifical neutron
* 1951 first neural network machine
* 1957 perceptron
* 1969 nearest neightour algirthm
* 1970 backpropagation
* 1979 neocortignitron
* 1982 recurrent neural network
* 1986 backpropagation applied to neural network
* 1989 reinformencet learning
* 1990-2005: support vector machines, random forest algorithm
* 2005-2021: attempts to resssurce neural networks with unsupervised pretraining,probalilistic neural nets, aleternative learning rules
* 2012: imagenet chhallenge: classify unsee saples of the same image; alexnet CNN possible due to the advancement in GPU processing
* 2021-present: more layers, more parameters, lots more computing cycles, a few important tricks that imrive training and generalization,
## hot topics in 2022
* transformer networks; attention based neural networks
  * focus on specific areas in our percetion
* quite good for computer vision and natural language processing (NLP)
* GANS: generative adversarial networks
* diffusion models (markov chains with random noise): cat with a hat ..
* self-supervision great techniqe for labelling unlabelled data
* zero-shot learning (no trainign data) versus one-shot learning
* knowledge-distillation
## ml tasks
* supervised learning: regression
* image classification: binary image classification: dog and cat ..
* object detedtion: with bounding boxes
* image segmentation
* natural language processing: keyword spotting, (google home and alexa)
* clustering: crime prediction using k-means clustering
* imensional reduction: squash the 30x30 features into two dimension by reduction, then easy to label
* reinforcement learning: good for learning to play Go or other computer games

* reasons for failure: asking the wrong question
* having too less, much data, using the wrong tools,not the right model or metrics, wrong people, trying to solve the wrong question











.. wip ..




