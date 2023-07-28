# 20230713 Kaggle Munich

```
Details

Kaggle is a platform for data science competitions, where you can improve your skills and compete with others to solve real-world problems. Whether you're a beginner or an experienced data scientist, this meetup is for you.

Thanks to Acronis and Constructor Learning for hosting and sponsoring the meetup!!

Agenda:

18:00 Door opening, drinks, casual welcoming
18:30 Quick Introduction by Alexandre Moritz - 3 min + 2 mins welcome words from Constructor Learning
18:35 Talk 1: "Artificial Intelligence - Hype & Reality: Will the Terminator Ransomware arrive soon?" by Lukas Nester (Acronis) - 25 mins
19:00 Break - 5-10 mins
19:10 Talk 2: "NLP in Radio NASCAR Communications" by Adriano Persegani Daguzan (Constructor Learning) - 30 mins
19:40 Talk 3: "Credit risk analytics with machine learning" by Fares Djerourou (UniCredit) - 30 mins
20:10 Pizza arrives and Drinks + Networking
21:30 - 21:45 End of the event

Artificial Intelligence - Hype & Reality: Will the Terminator Ransomware arrive soon? by Lukas Nester (Acronis)
In this thought-provoking session, we explore the intriguing intersection of artificial intelligence, its surrounding hype, and the realistic implications for the future.
Delving into the question of whether the dreaded Terminator Ransomware is on the horizon, we provide valuable insights on the actual risks and challenges we face in the AI landscape.

NLP in Radio NASCAR Communications by Adriano Persegani (Constructor Learning)
In the adrenaline-fueled realm of NASCAR, AI and Deep Learning are transforming strategic decision-making. This project delves into how teams utilize real-time radio communication data, processed through advanced Deep Learning models, to gain a competitive edge. We'll explore the intricacies of data preparation, and the implementation of NLP techniques, showcasing a practical application of these technologies in the high-stakes world of NASCAR racing.

Credit risk analytics with machine learning by Fares Djerourou (UniCredit)
At a time when some significant banks are going bankrupt the question of a looming financial crisis is always being raised. What have banks done since the 2007 crisis to prevent such events from happening again? In this talk we will go through the modeling procedure adopted by banks when it comes to assessing their credit portfolio risk, we will be taking a practical example with real loan data and go through the data preparation as well as the machine learning models being used by financial institutions to meet capital requirements.

See you soon!

Don't miss out on this opportunity to learn, network, and have fun with other Data Science- / ML- / Kaggle fans!

We are always looking for speaker. If you have any ideas or suggestions, please don't hesitate to let us know.

We look forward to seeing you at the next Kaggle meetup!
```

## Introduction
* Constructor and Acronis have the same owner
* 'knowledge is the solution against all evil'; educational institution
*  constructor start-garden -already starting to learn in kindergarden - check this out
* earlier: Schaffhausen institut for technology
* for their courses they do 2-stage-interviews and work also with capstone projects from real companies - less dropouts
* why? university degrees take too long to complete
* become a data-scientist in 12 weeks?

* upcoming events: 28.07. Jetbrains office for presentations of capstone projects
* harnessing aI for product management; online?
![](img00.png)
* 10k€ course fee; but also voucher and loans, etc.

## "Artificial Intelligence - Hype & Reality: Will the Terminator Ransomware arrive soon?" by Lukas Nester (Acronis) - 25 mins
* helping the world get #cyberfit for 20 years
* starting with a small backup solution - right now one of the leading vendors for data protection ...
* growing quite fast: 2k employees in over 30 locations

* hackers don't look for companies, but vulnerabilities
* most of the time 7million $ are the average cost for a successful cyber-attack
* AI is no match for human stupidity
* (Germans: risks instead of opportunities)
* Acronis is using gpt for event invitations, presentations, website content, for lots of use cases
*  incivta.ai - share own model?

* what might be next for AI in malware?

### poly/metamorphic malware
* ask te AI to write new malware version for each new infection, e.g. BlackMamba
* the behaviour changes little

### self adapting malware
* behaves differently depending on the env and compromised system
* e.g. DeepLocker IBM 2018

### autonomous AI malware
* completely new never-before-seen attack methods, like Rowhammer

#### asymetric attack
* attacker uses very low resources, the defender as to use high resources to defend
* little effort, expertise, fast and scaled - great effort expertise necessary, time-consuming

##  "NLP in Radio NASCAR Communications" by Adriano Persegani Daguzan (Constructor Learning) - 30 mins
* from Data Science to NASCAR
* Adriano is one of those career shifters; from restaurant manager to data science

* why become a DS?
  *  high demand
  * versatile skills
  * impactful insights
  * problem-solving opportunities
  * constant learning and growth
  * future-proof career

### The fast and the verbose: NLP takes on NASCAR radio
*team and drivers communicate with each other
* you can check the radio of everyone
* someone previously implemented already some speech recognition (nvidia) -> ginormous data set
* filter: importance and intent labeling
* this time some unsupervised ML
* automatic topic identification
* topic comparison
* identified different clusters after dimension reduction
* topic classification: frequent words worked quite well
* Few shot learning has a really high score, therefore preferable
* used Google Colab for training
* right now they could classify 23k talks in less than 6 seconds
* check on radionascar.com - has also chat for testing out the models

## "Credit risk analytics with machine learning" by Fares Djerourou (UniCredit) - 30 mins
* modeling expected and unexpected loss
* before: logistic regression or decision trees were used; but there was a correlation between the values
*  cure: person defaulted, but they paid it back
![](img01.png)
* splitting it into more components allows to model it more directly - but this does not work
* banking sector not really happy about ML models because of the lack of trust
* data preparation as first task; proper encoding of some columns
* fixing missing columns - because no use for them
![](img02.png)
* models tested: logistic regression, gradient boosting, random forest, feed forward neural networks

### next topic: options
![](img03.png)
* call and out options as vanilla options, most basic ones
* good for speculation
* monte carlo sampling with python (todo?)
* strike price (?)
* Heston volatility smile
* trained a feed-forward model on 100k samples: confidence 99%
* reference: Investopedia - check this
* his approach: never go above four layers
* holding does not want to have models, which lack interpreteability
* he supersampled the imbalanced classes
