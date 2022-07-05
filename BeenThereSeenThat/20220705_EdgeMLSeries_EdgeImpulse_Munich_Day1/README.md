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

### hot topics in 2022
* transformer networks; attention based neural networks
  * focus on specific areas in our percetion
* quite good for computer vision and natural language processing (NLP)
* GANS: generative adversarial networks
* diffusion models (markov chains with random noise): cat with a hat ..
* self-supervision great techniqe for labelling unlabelled data
* zero-shot learning (no trainign data) versus one-shot learning
* knowledge-distillation

### ml tasks
* supervised learning: regression
* image classification: binary image classification: dog and cat ..
* object detedtion: with bounding boxes
* image segmentation
* natural language processing: keyword spotting, (google home and alexa)
* clustering: crime prediction using k-means clustering
* dimensional reduction: squash the 30x30 features into two dimension by reduction, then easy to label
* reinforcement learning: good for learning to play Go or other computer games

* reasons for failure: asking the wrong question
* having too less, much data, using the wrong tools,not the right model or metrics, wrong people, trying to solve the wrong question
[todo: add some of the photos - at least those which can be read]

## Making things smarter
* coming from Arrow, Amir Sherman
* adding more semiconductor functionality to grow the platform
* he will also replace renesas and alif, because they could not come due to sickness
* "AlifSemiconductors and EdgeImpulse is a great combination"
* 2022 1.2 billion devices with ML functionality
* wide, broad support
[img: platforms]
* lots of ARM-based solutions
* cloud AI, edge AI (existing), endpoint AI (new): how to do face and voice recognition without connection to the cloud?
  * cortex m55: up to 15x uplift
  * ethos u55; 32x ml uplift
* combination is possible, can be combined with other platforms: speed to inference increases, also increase the energy efficiency
* ethos m55: first microNPU for cortx.M
* 4.7 ms to detect a face; 10 ms for yaw and landmarks (face angle and feature): worked quite fast with a group of people
* alif ensemble development kit: is available
* currently the kits do not work for automotive, because just down up to 25°C (? or down to minus?)
* work with global foundries, not TSMC
* "great question" ..
* price range to 5-12 euro for 10k item prices

## syntiant - making edge AI a reality - robert van der waal
* delivering deep learning solutions for always-on battery powered devices
* actually a semiconductor company, but also provide tools to train models
* first idea was to create an edge-device, which is alexa-ready; passed this also in 2019
* huge journey for the company itself
* syntiant neural decision processors: at-memory compute; store data close to MAC-part (multiply and accumulate)
* optimized edge devices, which recud battery consumption: A53 at 1 GHz versus 32 MHz syntiant core v2 -> 3,5days versus 1 year
* syntiant data hub:
* glass breaking detection: data from kitchen usage is similar to glass breaking; so this is an additional problem
[img to add]
* NDP100, 120 and 200
* example: runs two networks: one for keyword detection, one for glass breaking; both can run concurrently
* battery-operatred person detection
* now the problem is the microphone: some have now no-sound-sensing
* cameras a re a bit less power hungry than microphones (?)
* Syntiant and Edge Impulse collaboration
* tinyml-board is available on digikey [checkthis]: contains ndp101-chip; 2hours of work to get a working model

## MCSA - an old technique in a new dress
* motor diagnosis: how to improve with ML?
* two types: AC and DC motors
* BLDC motors: brushless mtoros; most common in devices and robotics
* bearing faults and stator faults: short cicruits, shaft faults, brushes fault
* faults require time to develop
* condition monitoring for motors
* objective: reduce maintenance cost, improve components, reliability, optimized motor performance, predict motors failure
* MCSA: motor current signature analysis is sensorless based
* sensor based: thermal monitoring, noise monitoring, vibration monitoring, torque m.; disadvantages: possible sesor failures, accurate sensors are expensive, require access to the motors, invasive installation
* effective dsp approaches: emd (empirical mode decomposition)
* classical ml worked better than deep learning
* but there was just the 10year old paper: no opensource, no code existing
* then they used edgeimpulse to recreate the model
* ingest the data-set; the tuning the model and layers
* 60k datasets as input used; 11 classes and combinations can be recognized
[img for the deployment of the model]
* continuous deployment with automated pipeline

## Edge ML in the world: datasense by sc robotics
* using tinyML
* IoT for agriculture
* two main products: data logger and wine-smart-bung
* battery operated devices, so power consumption really important
* "we don't like being said how to solve a problem, we want to understand it first": we show solutions, because we have the experience
* edge ml: why and when?
  * bandwidth saving
  * energy saving
  * local operations
  * network independence
  * long-time-to-market (due to waiting for data-input from customer)
* edge gesture detection: no touch
* systems architecture for Ntouch
[add image]
  * uses time of flight sensor 
  * thanks to edge impulse the reuse of a model for another target is straightforward
  * once a gesture is detected, any output event can be triggered
  * TOF-sensor: light ultra-sonic device; 8x8 pixels picture
  * so with EI they train simply on images
  * two operation modes: fingers detection (fingers for one, two, three..) and gesture detection (swipe): color for the extra dimension
  * very useful stacking technique  
* difficulties: data quality
  * problem with skin-tone and left-/right handed affected the data quality: no more good clustering of the data-set
  * the "data explorer" feature helped quite well: with one click data-samples can be reclassified with just a few clicks
* quick protoyping: they used the RPi and Jetson Nano, support for these platforms was quite useful
  * any change via ssh quite simple: anything which runs linux; after validation they use smaller microcontrolers
* model deployment: constraints for OTA and memory sizes; proper strategy should be chosen
* st vlx5 for the TOF sensor (should be freely available) [check this]




.. wip ..
