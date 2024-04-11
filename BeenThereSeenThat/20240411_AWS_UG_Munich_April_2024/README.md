# 20240411 - AWS UG Munich April 2024

## agenda
```
AWS UG Munich April 2024

Details

Right after the Easter holidays we continue with our meetups and focus on production use cases in the Big Data area this time.
Please note, that we open the doors at 18:00 already and will start at 18:30 with the talks!

This time we meet at the synvert Data Insights office and thankfully get food and drinks provided.

AGENDA:
18:00 - Doors open, networking, drinks, food

18:30 - Markus Ostertag (AWS Hero): Recent AWS announcements

19:30 - Christian Burger (BSH Home Appliances), Mario Montes Aguilar, Hsiao-Ching Pierre (synvert Data Insights): Building Modern AWS IoT Lakehouse: Where Smart Devices Meet Big Data

20:30 - Saif Addin Ellafi (BSH Home Appliances), Eduardo Gonzalez (synvert Data Insights): Streaming in a Data Lake: Enabling real-time Model Monitoring from appliances

21:15 - More drinks, more networking
```

## Intro by Marksu
* intro after the food truck closed its curtains
* recap of his relevant changes:
* compute: EC2 G6 instances are now GA (nvidia L4 Tensor Core GPUs)
* improve contaner scanning
* extended support adds 12 months of security patches: for "out of support" versions, but with a price-tag (for pnned versions): either breaking change or compliance rules
* who is Gregor Hope (AWS Entreprise architects)? Vendor lockin; but people who complain abut that are the ones paying the price for continued support# 20240405

needs refinement: CodeOxygenator
* serverless: support for Ruby 3.3
* DynamoDB supports now AWS PrivateLink
* TimeStream (time series db) for InfluxGA ins now GA
* ElastiCache Serverless adds more controls for scaling
* what is a blue/green (for databases - replication?)
* DevTools: AWS cloudFormation: new validatio checks for stack operations; sTackSets launches ListStackAutoDeploymentTargets API
  * CF console now support visualisation of stacks in Application composer
  * CodeBuild now spport scustom images (Docker) for Lambda compute - prepopulate for specific tools
  * now suort itlab and GitLab SelfManaged
* BedRock GenAi chatbox blueprint in CodeCatalyst
* Introducing AWS CodeConnections, formerly known as AWS CodeStar Connections: CodeStar Connections API will be disabled in April 2025
* AI/ML:
  * Bedrock now available in PAris
  * Claude3 Haiku now new
  * Mistral Large now only available in PAris
  * knowledge db now supports metadata filtering (knowledge bases are the RAG feature)
  * now let's you cutomize prompts and number of retrieval results
  * offers support for CF and Service Quotas
  * AWS announces a 7-day window to return Savings Plans
  * AWS cost allocation tags now support retroactive application
* Announcing AWS Deadline Cloud: rendering service, for 2D/3D rendering
* Amazon Location Service for iOs and Android
* AWS Munich Office Event: The well architected startup - resilient rhapsody - 24h April (https://AWS-startup-lofts.com/emea/events ?)
* May 7th: not the lego-building at neuperlach (??), but near Odeansplatz
