# 20231107 AWS UG Munich November Event

```
AWS UG Munich November Event

Christmas is just a few weeks away and so is AWS re:Invent 2023 in Las Vegas. So let's prepare for the most important event of the year (I'm talking about re:Invent) in style:
This time we meet at the IBM Watson Tower and get food and drinks sponsored by Nordcloud.

For office security please provide your real first and last name during the registration!

AGENDA:
18:30 - Doors open, networking, drinks, food

19:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:00 - Arvid Ottenberg, Lars Dittert, Christian Ungnadner (IBM) - Innovating Vehicle Connectivity: A Serverless IoT Approach on AWS

21:00 - Henrik Andersson (BMW) & Marco Hutzsch (Nordcloud): Management of a massive AWS Environment is (Server)less work!

21:45 - More drinks, more networking

If you have an office or co-working space where we can meet (100-150 people), want to sponsor drinks/food or have a (lightning) talk you want to present - please let us know!

Everyone who participates in an AWS UG Munich event must adhere to the Code of Conduct!
```
## Short intro - Ostertag
* Clemens from IBM spoke some words, Nordcloud and IBM sponsored it
* Biggest event ever, Clemens' words
* First thought "mainframes" when you hear IBM
* IBM consulting for AWS
* Pretty open in technology and solutions
* Nordcloud known for `hyperscaler` and AWS

## AWS important releases - Ostertag
* What happened since the last meetup? (last October)
* WIP: AWS European Sovereign Cloud: full EU-based; run by EU residents
* Region will be in Germany
* Every hyperscaler is US-based
* Markus said that Amazon never handed data to the US government (FBI, CIA..) from an EU customer; but there is a business need in Germany for that
  * Prefix like "aws-gov-eu" are totally decoupled from anything from AWS before; needs also a new AWS account! Just like "aws-gov-us" or "aws-cn"
  * Everything should be siloed, so that you don't try to connect to outside services
* EC2 allows to set AMIs now also to a disabled state
* Instance suffix is saying if Intel or AMD: M6i means Intel, C6a - AMD <-- check: SUGGESTION: Confirm correct instance suffix for Intel
* Spain is most of the time a new region where they add new instances
* Reserving GPU instances for certain days and lengths now possible in US East
* Network: first scales out, then terminates the unhealthy target (before this could lead to a death spiral)
* SQS throughput now up to 18k messages/second
* R7g is ARM-based, because it's Graviton3-based
* Databases: transaction logs always get appended on
* ETL - Extract, Transform, Load
* AWS Glue now supports GitLab, BitBucket in its Git integration feature
* AWS X-Ray now supports W3C format trace IDs - sent via OpenTelemetry Collector
* CodePipeline can now be triggered by tags as well: can also retry from the first action in a failed stage
* CodeWhisperer can now be customized
* AI/ML: Rekognition moderation model can be customized
* Bedrock now available in Frankfurt
* Next AWS UG meeting: 14th December at AWS office - talking about re:Invent highlights

## Innovating vehicle connectivity - a serverless IoT architecture on AWS
* Talk by the three guys: Markus introduced them as boy band
* "Advisory solution architect"
* IoT 101: enable to connect people anywhere and anytime
* Use-cases: smart home; smart grid (power grid), smart city, smart industry
* Growth of 130% over four years
  * 83 bn connections in 2024
  * 70% of the IoT connections are in the industrial sector
* Edge on the one hand - cloud on the other hand
* Remotely triggered functions
* Add IoT architecture - photo ![](img00.png) TODO
* The whole stack does not generate much value unless you create some IoT applications
  On the sides are the management and security dimensions: no faking of events or devices allowed
* Challenges in the development of IoT solutions
  * Device management
  * Distributed systems
  * Scalability
  * Intelligence
* What if you have different machines from different vendors, also different models, different formats, capabilities of these devices, ..
 
### Project: Showcase for connected vehicles
* 63k sensor-equipped vehicles; 2 mio datasets daily; 20k geofences for positioning in Europe
* Data is put into data lakes
* Why does the data have to be processed at all? Could it not be put into the data lakes directly?
* Needs: consuming applications need homogenized data; vehicles are equipped with sensors from various manufacturers, different sensors provide different data
* AWS S3, EventBridge, Lambda, and SQS are the used technologies
* All of them are pay as you go - as you use them
* ETL pipeline is split into five different components
* Patterns: queue-based architecture; event-driven architecture (EDA), serverless architecture
* SQS added as load balancer: collects all messages; just possible due to the queuing - no immediate response needed
* Serverless: scalability will be done by AWS; reduces operational fee
* DevOps with IaC on different stages
* img02 TODO
* AWS Lambda is responsible for enriching the homogenized events
* Much spikes during the day, but also datapoints with almost zero traffic
* Nonfunctional requirements of the external services not known - was a challenge; not sure how to handle a massive amount of data
* Simple retry mechanism was not enough
* Three potential solutions:
  * Reserved concurrency for AWS Lambdas
  * Introduction of the circuit breaker pattern: to support the recovery of the external system and improve failure management
  * Ambassador pattern: introduction of the ambassador pattern
* IoT Core Broker is expensive; also can only handle messages with max. 128 kilobytes

## BMW framework public cloud
* Henrik Anderson <-- check: SUGGESTION: Confirm correct spelling of the name
* Marco Hutzsch
* 60 nationalities in 29 countries, 20 mio connected cars; centered in Munich
* More than 11k applications
* Agile transformation of the BMW Group
* BMW Cloud Foundation team: is more than 500 people

[rest missing due to empty battery]
