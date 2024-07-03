# 20240703 - AWS UG Munich July 2024 - 10th anniversary of the AWS User Group Munich

## agenda
```
Details

In 2014 the AWS User Group Munich started with the first events in a beer garden (it's Munich!) and a few AWS enthusiasts. And we're very excited to be able to celebrate the 10th anniversary of this AWSome group now! This is why we also do things a little different this time.

Thanks to adesso SE for sponsoring food, drinks and opening their office for us.

For this special occasion we deviate a bit from our regular agenda:
18:30 - Doors open, networking, drinks, food

19:00 - Constantin Gonzalez Schmitz (Principal SA @ AWS): AI/ML at Amazon: What we learned over the years

20:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:30 - Meyyar Palaniappan: A special surprise announcement

20:45 - Michael Wahlers (Head of Technology @ AWS): Let's play AWS BuilderCards!

21:00 - BuilderCards, more drinks, more networking
```

## Intro by Markus
* celebrating the anniversary

## Constantin Gonzalez Schmitz (Principal SA @ AWS): AI/ML at Amazon: What we learned over the years
* Constantin as first AWS solution architect
* "transforming customer experiences through AI-enabled innovations at Amazon.com"
* working for AWS since 2021
* amazon intends to become the worlds most customer cnetric company
* not be afraid of competition or customers, someone offers them a better service
* TODO check the quote from jeff bezos
* there is no hardware or contract attached to that, so if customers find their service someehwre else, they go to the next vendor
* what is the customer promise: very specific customer promise; order in 2 h and 8 min to get it tomorrow
  * behind that is a very expansive sstem: more than 400 mio products; multiple levels of broadcasting
  * forecasting -> capacity -> buying -> placement -> fulfillment
  * accurate delivery promise
  * some are obvious, like seasonal stuff; others are not obvious (children's crazy costumes..)
* start with a simple approach: input -> program -> output
* relies on what humans can observe and program
* machine learning is different: take the available data, feed into algorithm, algorithm does it for your, the model -> get the output: you get a statistial answer
* also: this approach scales well
*  AWS used ML since 2007: decision tree models (if then else on steroids) -> quickly switched to deep learning models
* al fitting items are put into shelves, yellow ones, fulfillment enters
* guided stow/picking activities through bin vision system
* stowed in chaotic order: wherever is any space
* shelf-lighting: to prevent mixing of heavy items and to avoid mixing similar items
* also: optimize packaging: not traditional (box) packaging, but smaller envelopes: 75% lighter and 50% smaller
* big question: which packaging to choose
* ML model changing the game: basic decision making rules + visual inspection of (only) top products
  * feedback loops; gaterhing small amount of data; feed the results and knowledge of workers back into the model
* now this knowledge can be used to adapt to things which never have been seen before
* what about collectibles: for those it means they are delivered in the best possible way
* genAI makes it a bit more interesting:
  * traditional ml models mean a lot of work: ather data, prepare model, tune
  * versus: take a foundation model and use the same model for different tasks
  * working backwards questions: what is the customer? what is the customer problem or opportunity? in most mortant customer benefit clearn? ow do you knwo what customers want?
  * risks vs opportunities: unkown data provenance -> cost implications -> unpredictable behaviours
  * low touch use-cases: well served by existing tehcnologies -  not cost effective
  high touch use cases: risk of negative customer experience (reputation ..)
  * new feature: customer review summaries (Q3/2023): clever idea
  * create customized product photos with background based on the wanted campaign

### what did they learn as organization?
* ml-first mindset and culture
* eanbling teams for the mission
*powerful data platform

* every manager at amazon has t write a business plan eevery year (Op1): chalenges,opportunities, how much to invest, what we see ..
* also: How will we use machine learning? sound slike the ahmmer-naiö-problem: a forcing function
* to think AI as natural way of how we do thigs at amazon - not just make it a "tech people" problem
* tin the problem from the very business side of the task
* ("We wont as not acceptable answer"). conversaton starter.
* break down the silos! domain experts and the technical experts are part of the same team - avoid silo behaviour (known from devops: throw stuff over the wall .. let the tech people sort out the ml-part ..)
* also: they are fast .. they can coordinate within the same day
* apply the right tool for the job: cloud computing gives the team access to all the technology they want
* everyon has access to all tools; automatic compliance rules; remove friction from the rpocess, by adding self service automation ... wow!
* data fuels ML-driven innovations
  * security and performance at scale; innovation happens at the edge; remove heavy lifting
  * amazon.com's ig data marketplace: created a marketplace for data and information ..
* bottleneck people want t do 2x more with AI but struggle to put t into production
* enable speed and scale through automation: make sure it is 100% automated ..
  * what manual process can be replaced with a script to make it faster?
* summary:
  * ai ml not just a toy, but mission critical for amazon
  * ml delivers a differential impact and non-linear scaling for amazon
  * building and scaling ml usage at entreprise level requires clear strategies across a system of enablers
  * .. ask him for questions and give feedback..

## break and AWS important releases by Markus
* the very first time that the employer hosts the AWS meeting (for Markus)
* adesso a full service provider: end to end IT-service provider
  * do a lot of things in the cloud
  * cloud agnostic, not only AWS
  * more than 11k employees, more than 1 biollion€ in group revenue in 2023; 60 locations
  * has 280 AWS certifications
  * internet of things .. in the cloud, on the cloud, for the cloud
* customer obsession
* around 400 updates per month from AWS
* detect new malware uploads in new object uploads to Amazon S3 with Amazon GuardDuty
* container: EKS: open source the Pod identity agent
  * introduces cluster creation flexibility for netowrking add-ons
* elasticache serverless now supports snashot and restore for memcached
* AWS glue: usage profiles is now GA
  * add additional 13 new transforms
  * DAta Quality Definition Language enhancements
* AWS codebuild: create hooks based on the github organization - also build timeout increased to 36h
* amazon codecatalyst:  introducing maven, python, nuget support in codecatalyst package repositories
* now supports gitlab.com source code repos
* AWS codeartifact supports now Cargo, the rust package manager
* "two pizza things"
* AWS cloud trail lake announces AI-powered natural language query generation (in preview us-east-1 only)
* more support for AWS biling and cost management for dashboards: supports FOCUS as data export; as least common nominator
* AWS cloudshell now supports VPC ("we never do cloudshell, only infrastructure as code!")
* AWS Meetup: the well architected startup

## Women's user group - Meyyar Palaniappan
* not enough diversity in the tch space
*
