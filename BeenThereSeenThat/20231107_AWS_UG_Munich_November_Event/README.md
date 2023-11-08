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
* clemens from IBM, nordcloud and ibm sponsored it
* biggetst event ever, Clemens words
* first thought "mainframes" when you hear IBM
* IBM consulting for AWS ..
* prett open in technology and solutions
* nordcloud knwon for `hyperscaler` and AWS

## AWS important releases
* what happened since the last meetup? (last octobre)
* wip: AWS European Sovereign Cloud: full eu-based; run by eu.residents
* region will be in Germany
* every hyperscaler is us-based
* Markus said that Amazon never handed data to us-government (fbi, cia..) from a EU-customer; but there is a business need in germany for that
  * prefix like "aws-gov-eu" are totally decoupled from anything from AWS before; needs also new AWS account! just like "aws-gov-us" or "aws-cn"
  * everything should be siloed, so that you don't try to connect to outside services
* EC2 allows to set AMIs now also to a disabled state
* instances-suffix is saying if intel or amd: M6in means Intel, C6a - AMD
* Spain is most of the times a new region where they add new instances
* reserving GPU-instances for certain days and lenghts now possible in US-east
* network: first scales out, then terminates the unhealthy target (before this could lead to a death spiral)
* SQS thoghtput now up to 18k messages/second
* R7g is arm-based, because graviton3-based
*databases: transaction logs: always gets appended on
* ETL - extract transform load
* AWS Glue now supports GitLab, BitBucket in its Git integration feature
* AWS X-Ray now supports W3C format rrace IDs - sent via OpenTelemetry Collector
* coepipeline can now be triggered by tags as well: can also retry from the first action in a failed stage
* codewhisperer can now be customized
* AI/ML: Rekognition moderation model can be customized
* Bedrock now available in Frankfurt
* next AWS UG meeting: 14th Decembre at AWS office - talking about re:iInvent hgithlights

## innovating vehicle connectivity - a serverless IoT architecture on AWS
* talk by the three guys: markus introduced them as boyband
* "advisory solution architect"
* IoT 101: enable to connect people anywhere and everytime
* use-cases: smart home; smart grid (power grid), smart city, smart industry
* growth of 130% over four years
  * 83 bn connections in 2024
  * 70% of the IoT connections are in the industrial sector
* Edge on the one hand - cloud on the other hand
* remotely triggered functions
* add IoT architecture - photo ![](img00.png) todo
* the whole stack does not generate much value unless ou create some IoT applications
on the sides are the management and security dimeniosn: no faking of events or devices allowed
* challenges in the development of IoT solutions
  * device management
  * distributed systems
  * scalability
  * intelligence
* what if you have different machines from different vendors, also different models.. diffrent formats, capabilities of these devices, ..
### project: showcase for connected vehicles
* 63k sensor-equipped vehicles; 2 mio datasets daily; 20k geofences for psoitioning in Europe
* data is put into data lakes
* why does the data to be processed at all? could it not be put into the datalakes directly?
* needs: consuming applications need homogenized data; vehicles are equipped with sensors from various manufacturers, different sensor privde different data
* AWS S3, eventbridge and lambda and SQS are the used technologies
* all of them are pay as you go -as you use them
* ETL pipeline is split into five different components
* patterns: queued based architecture; event driven architecture (EDA), serverless architecture
* SQS added as load blanacer: collects all messages; just possible due to the queing - no immediate response needed
* serveless: scalability will be done by AWS; reduces operational fee
* DevOps with IaC on different stages
* img02 todo
* AWS lambda is responsible for enrichting the homogenized events
* much spikes during the day, but also datepoints with almost zero traffic
* nonfunctionla requirements of the external services not known - was a challenge; not sure how to handle a massive amount of data
* simple retry-mechanism was not enough
* three potential solutions:
  * reserved concurrency of AWS lambdas
  * introduction of the circuit breaker pattern: to support the recovery of the external system and improve failure management
  * ambassador pattern: introduction of the ambassador pattern
* Iot core broker is expensive; also can just handle messages with max. 128 kbytes


## BMW framework public cloud
* henrik anderson
* marco hutzsch
* 60 nationalites in 29 countries, 20 mio connected cars; centered in munich
* more than 11k applications
* agile transofrmations of the bmw group
* bmw cloud foundaton team: is more than 500 people

[rest missing due to empty battery]
