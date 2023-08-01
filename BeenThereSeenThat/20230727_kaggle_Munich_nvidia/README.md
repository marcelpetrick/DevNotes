# 20230727 kaggle Munich nvidia

todo: add photos

## 1st talk: Winning a Kaggle competition: Large-scale image Retrieval of Google Landmarks by Christof Henkel, PhD, Senior Deep Learning Scientist (KGMON), NVIDIA
* currently grandmaster number three worldwide
* started at LMU, works at nvidia
* Christof Henkel; https://twitter.com/kagglingdieter

## image retrieval
* given a query image find the most similar image in a db of indexed images
* normally create embedding or correlation, feature vector fort he image (all different names)
* main challenge to train a model to have a good image embedding vector
* if this is possible do embedding for query image and match this against the content of the database
* can be used as well for classification
* simply by using the class of the most similar image
![](img00.png)
* competition has some images which were never seen before
* usually 512 as width of images; for embedded things vectors of 32 are common (drones)
* importance for embedding vectors and similarity
* images with the same coloring, weather conditions, ... can be found

* cosigned similarity: describes the angle between the embedding vectors
  * simplest way: hashing: naive way ..
* state of the art way: arc face loss
* cluster the embedding vector across some center, which represent sthe class; also represent tha margin of the calss
  * can be used for NLP as well, not just image vision
* how to combine models and approaches:
img01

* RANSAC for homographic verification
## LLMs:
* information retrieval document or chunk embeddings
find relevant documents for question  answering
de-duplication
classification
## ecommerce
* embeddings are central for product/user representation which can be used for recommendation

# GLD2
* google landmark dataset 2 (quite important, has papers about it)
*a good benchmark for large scale image retrieval: shares a lot of properties for other large scale sets
* diverse in terms of 200k classes
  * nature, buildings, globally with some bias on Europe
* but similar:
  * churches: 500k churches, castles and museums
  * parks, mountains, ..
* long tail: not homogenous
* half of the classes have less than ten images; which makes it quite tricky
* high intra class variability (see churches)
* crowd-sourced: wikimedia commons; right now with climate change for July; needs GPS and some metadata and have the proper license
* but google also has "operators", who are hired and take specific photos for wanted new classes
* there was a "cleaned" version after the 1st place solution of the 20129 google landmark competition
* 3 step approach: 100 nearest neighbours ... GLDB-clean; also resulted in the reduction of classes to 81k; is a subset
* competition has two tracks: recognition and the retrieval track
* inference is done on a hidden query set
* added spice by adding non-landmark distractors
* resnet; and generalized mean-pooling as approach of the winners of the competitions
* comparisons of annual solutions: img03
* local feature recognition is really important for proper classification; for instances for churches
* kaggle kernels using deep learning approaches

### competition of 2021
* requirements: 1 P100 GPU, 2 cores CPU, needs to run in 9 hours; everything needs to be offline
* tight timeline: only 6 weeks; last weeks winners were published as well - so everyone starts at the 1st place of the last year
*strategy: no spatial verification, focus on local features, retrieval approach also for recognition

* elevate retrieval and recognition quality
* he used the 2019 results and test-images to identify pure landmark items

### his ML workflow
![](img04.png)
* workflow which helps him to iterate quite fast
* most competitions as team, but this one alone
* quite modular: training/experimentation; storing; incremental deployment
* training: not a fan of docker 2 years ago; but now he likes  it: same environment wherever he goes; just installs some more pip-packages
* consistency between different team members and machines ..; version mismatches bugs!

#### details
* he loves jupyter lab as IDE
* better support for multi-gpu training
* uses github to store code and share with team members
*feature: github actions: push code to kaggle dataset and kernels
* ASWS for storage
* neptune: for visualization; displaying metrics, storing hyperparameters; comparing training runs; compare with team members
* the pushing to kaggle and its automation was quite helpful for him ... also the requirements.txt
### tips for large scale data
* really helps with experimentation: just use a subset of the data
* 1 percent of the data: just check stuff
* then larger subset for experimentation (half), but still not the full data - to save time
* same is true for the image sizes; also re-use the weights on larger images, the retrain again for even bigger images -> gives you a much more efficient approach fr experimentation
* in theory everything should run on GPU, but his experience is that this way CPUs are starving
* multi-GPU training: distributed data parallel over DP (distributed parallel); because it reduces the communication between GPUs and is therefore faster

### modeling and architecture
* use backbones where weights of the images are already pre-training on imagenet
* two main  models: hybrid swin transformer and DOLG
TODO: image of his architecture
* STEM -> Body -> neck -> Arface classification head

## first model: DOLG
* efficeint net encoding
* de-orthogonal fusion of local and global descriptors
* image TODO
* subcenter arcface with dynamic margins handles the intra-class variability well; 2nd and 3rd place the year before
* transformers can be used as well for computer vision: but need specific input resolution; pathing up the image into parts; also using the global virtual token into the neck and into the loss function

## second approach for the recognition
* he used his cleansed non-landmark dataset to flag images
* idea is discriminated class reranking
todo image of class consistency reranking
* at the end of the day he had 9 models in his kernel: accumulated training time 7-10 days on 8xV100

## curent SOTA
* transformer/CNN hybrids like convnext, maxfit
* large scale pretraining on image-text pairs:
  * CLIP learns visual concepts just by matching image with description of the image; gives much better image representation than training on image net
* using Matchformer, using cross-attention for spatial verification
* sources: youtube series also github open-sourced code and papers

# 2nd talk: Training is Silver, Inference is Gold by Adolf Hohl, Solution Architect Manager, NVIDIA
* Adolf Hohl -  Solution architect - from nvidia
* loves to build large scale number crunchers in his free time
* start: given an ONNX by Crhistof - pytorch versus tensorflow people; pytorch was the absolute majority of the users in the room
* he combined two models into one
* CLIP as feature extractor
* Triton is their inference server: ensemble model
* input tensor is a unfolded image; makes model more convenient to use; jpeg-decoder (current GPUs have jpeg encoders in hardware); does not need CUDA
* he usually wants to convert all ONNX models; his fingers start to twitch to do onnx export ..
* TODO: check TRITON model navigator
* followed by a demonstration: he does everything containerized (DOCKER!)
