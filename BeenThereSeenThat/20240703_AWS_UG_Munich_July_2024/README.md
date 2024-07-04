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
* Celebrating the anniversary

## Constantin Gonzalez Schmitz (Principal SA @ AWS): AI/ML at Amazon: What We Learned Over the Years
* Constantin was the first AWS Solutions Architect
* "Transforming customer experiences through AI-enabled innovations at Amazon.com"
* Working for AWS since 2021
* Amazon intends to become the world's most customer-centric company
* Not afraid of competition or customers; if someone offers them a better service, Amazon accepts that <-- check: is there a quote from Jeff Bezos?
* No hardware or contract is attached, so if customers find a better service elsewhere, they go to the next vendor
* Customer promise: very specific; order in 2 hours and 8 minutes to get it tomorrow
  * Behind that is a very expansive system: more than 400 million products; multiple levels of broadcasting
  * Forecasting -> capacity -> buying -> placement -> fulfillment
  * Accurate delivery promise
  * Some are obvious, like seasonal items; others are not obvious (children's crazy costumes..)
* Start with a simple approach: input -> program -> output
  * Relies on what humans can observe and program
* Machine learning is different: take the available data, feed it into an algorithm, the algorithm does it for you, the model -> get the output: you get a statistical answer
  * This approach scales well
* AWS has used ML since 2007: decision tree models (if-then-else on steroids) -> quickly switched to deep learning models
* All fitting items are put into shelves, yellow ones, fulfillment enters
  * Guided stow/picking activities through bin vision system
  * Stowed in chaotic order: wherever there is space
  * Shelf-lighting: to prevent mixing of heavy items and to avoid mixing similar items
  * Also: optimize packaging: not traditional (box) packaging, but smaller envelopes: 75% lighter and 50% smaller
  * Big question: which packaging to choose
  * ML model changing the game: basic decision-making rules + visual inspection of (only) top products
  * Feedback loops; gathering small amounts of data; feed the results and knowledge of workers back into the model
* Now this knowledge can be used to adapt to things that have never been seen before
* What about collectibles: for those, it means they are delivered in the best possible way
* GenAI makes it a bit more interesting:
  * Traditional ML models mean a lot of work: gather data, prepare the model, tune
  * Versus: take a foundation model and use the same model for different tasks
  * Working backwards questions: what is the customer? What is the customer problem or opportunity? Is the most important customer benefit clear? How do you know what customers want?
  * Risks vs opportunities: unknown data provenance -> cost implications -> unpredictable behaviors
  * Low-touch use cases: well-served by existing technologies - not cost-effective
  * High-touch use cases: risk of negative customer experience (reputation ..)
  * New feature: customer review summaries (Q3/2023): clever idea
  * Create customized product photos with background based on the wanted campaign

### What Did They Learn as an Organization?
* ML-first mindset and culture
* Enabling teams for the mission
* Powerful data platform

* Every manager at Amazon has to write a business plan every year (Op1): challenges, opportunities, how much to invest, what we see ..
* Also: How will we use machine learning? Sounds like the hammer-nail problem: a forcing function
* To think of AI as a natural way of how we do things at Amazon - not just make it a "tech people" problem
* Tying the problem from the very business side of the task
* ("We want as not acceptable answer"). Conversation starter
* Break down the silos! Domain experts and the technical experts are part of the same team - avoid silo behavior (known from DevOps: throw stuff over the wall .. let the tech people sort out the ML part ..)
* Also: they are fast .. they can coordinate within the same day
* Apply the right tool for the job: cloud computing gives the team access to all the technology they want
* Everyone has access to all tools; automatic compliance rules; remove friction from the process by adding self-service automation ... wow!
* Data fuels ML-driven innovations
  * Security and performance at scale; innovation happens at the edge; remove heavy lifting
  * Amazon.com's big data marketplace: created a marketplace for data and information ..
* Bottleneck: people want to do 2x more with AI but struggle to put it into production
* Enable speed and scale through automation: make sure it is 100% automated ..
  * What manual process can be replaced with a script to make it faster?
* Summary:
  * AI/ML not just a toy, but mission critical for Amazon
  * ML delivers a differential impact and non-linear scaling for Amazon
  * Building and scaling ML usage at an enterprise level requires clear strategies across a system of enablers
  * Ask him for questions and give feedback..

## Break and AWS Important Releases by Markus
* The very first time that the employer hosts the AWS meeting (for Markus)
* Adesso is a full-service provider: end-to-end IT service provider
  * Do a lot of things in the cloud
  * Cloud agnostic, not only AWS
  * More than 11k employees, more than 1 billion€ in group revenue in 2023; 60 locations
  * Has 280 AWS certifications
  * Internet of things .. in the cloud, on the cloud, for the cloud
* Customer obsession
* Around 400 updates per month from AWS
* Detect new malware uploads in new object uploads to Amazon S3 with Amazon GuardDuty
* Container: EKS: open source the Pod identity agent
  * Introduces cluster creation flexibility for networking add-ons
* ElastiCache serverless now supports snapshot and restore for Memcached
* AWS Glue: usage profiles is now GA
  * Add additional 13 new transforms
  * Data Quality Definition Language enhancements
* AWS CodeBuild: create hooks based on the GitHub organization - also build timeout increased to 36h
* Amazon CodeCatalyst: introducing Maven, Python, NuGet support in CodeCatalyst package repositories
* Now supports GitLab.com source code repos
* AWS CodeArtifact now supports Cargo, the Rust package manager
* "Two pizza teams"
* AWS CloudTrail Lake announces AI-powered natural language query generation (in preview us-east-1 only)
* More support for AWS billing and cost management for dashboards: supports FOCUS as data export; at least common denominator
* AWS CloudShell now supports VPC ("we never do CloudShell, only infrastructure as code!")
* AWS Meetup: the well-architected startup

## Women's User Group - Meyyar Palaniappan
* Not enough diversity in the tech space
* Why now (ten years after the other group exists)
* Global statistics: for every three men, there is 1 woman
* EU: for every 5 men, there is 1 woman in IT
* Spread the word, be the multiplier, empower women
* Amazon culture of writing
* Women who want to switch into the cloud career
* Make cloud technologies accessible to all
* "If she can see it, she can do it"
* Role models and visibility
* Förderverein AWS Community DACH
* First official meetup in October 2024, AWS Office Munich
* Follow AWS Women's User Group Munich: and spread the word
* TODO: share the QR code
* "Pulse of the audience": check what the audience thinks .. reach out to her and tell what they expect to see

## AWS BuilderCards: Michael Wahlers - Head of Technology
* Usually convinces governments to get rid of digitalization .. (not sure if I understood this correctly)
* What is BuilderCards: card game, not a service
* Architecture building game, educational, game concept unique to AWS, sustainable, a pretty decent board game
* House rules are possible for adaptation; team building
* TODO: add the photo
* Is it like Magic? (MTG)
* The challenge and the solution: what service can be combined with what?
* Cards, legacy cards, costs, categories .. TCO (total cost of ownership) credits
* 2nd edition coming: at re:Invent
* Mission cards: winner has the most well-architected points
* Make it available to buy online in Q4
* Right now not buyable, currently just swag
