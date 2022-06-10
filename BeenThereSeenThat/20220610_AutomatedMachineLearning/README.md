# 20220610: Automated Machine Learning
* powered by machine learning for production

* presenter Diana Artiom
* 19:00-21:00
* Sebastian Pineda Arango is the teacher

![](img00.png)
![](img01.png)

## motivation
* 80 % of DS/ML projects dont make it to production
* different kinds of specialists are necessary for various steps of the ML pipeline
![](img02.png)

## mission
* wanting to grow and host a lot of events ..
![](img03.png)
![](img04.png)
![](img05.png)
![](img06.png)

## ice breaker
* How are you feeling today?
* go to: ahaslides.com/8GORB
![](img07.png)
![](img08.png)
![](img09.png)

## now the "real" speaker takes over
* presenter Sebastian Pineda Arango
![](img10.png)
* humans do classification, but also uses previous knowledge
![](img11.png)

### how do machines learn?
![](img12.png)
![](img13.png)
* one shot learning as another technology
* or signature-learning (like a cat is like a small tiger, cute, ..)
* or transfer-learning: use pre-trained models

* simple example: ![](img14.png)
  * only one line of code will already achieve good performance
  
* automatic hyperparamter-optimization:
![](img15.png)
![](img16.png)
![](img17.png)
* autoscaler: best combination of models, scalers and [?]
* pipeline-optimization works very nice; better than just choosing a random model
![](img18.png)

## meta-learning: analogy with the evolution
![](img19.png)
* brain is changing and previous knowledge forms it: better adapted
* level over the machine-learning
* umbrella of AutoML
![](img20.png)
* Meta-training
* example application: self-driving cars under different conditions
* cars usually trained in a boring, empty road, good lighting: problems with changes (snow, many cars, weird background, ..)
![](img21.png)
![](img22.png)
### learn2learn
![](img23.png)
### neural architecture search <-- check this
* best combo of model, scaler, reducer is wanted
![](img24.png)
* transformers perform good; for NLP
* still not clear what is the best performing one; which is a stable one?
* that is wanted to b avoided

+ autogluon (is from Amazon) is a bit more * auto.gluon.ai/stable
![](img25.png)

### further topics:
* automated data cleaning
  * detect outliers
  detect mislabels
* multifidelity HPO
* when searching for HP:

* don't train on the whole dataset
* don't train all epochs: dependin on problem size and input-size it can take to 2 hours to two months; don't want to use the whole budget; just use a small part of the bduget to get an idea what to do and get
 ![](img26.png)

* batch processing: train models
* afterwards: transform input, model, output transformation

* currently ML is converting to one line of code
* currently model-deployment is really wanted and needed

* automatizing ml-creation is actually reducing the amount of jobs
* selfdestructive for our jobs
![](img27.png)

![](img28.png)
[end]
