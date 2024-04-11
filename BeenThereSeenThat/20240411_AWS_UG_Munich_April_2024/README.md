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
## Intro by Markus
* Intro after the food truck closed its curtains
* Recap of his relevant changes:
  * Compute: EC2 G6 instances are now GA (Nvidia L4 Tensor Core GPUs)
  * Improved container scanning
  * Extended support adds 12 months of security patches for "out of support" versions, but with a price-tag (for pinned versions): either breaking change or compliance rules
* Who is Gregor Hoppe (AWS Enterprise Architect)? Vendor lock-in; but people who complain about that are the ones paying the price for continued support
* Serverless: support for Ruby 3.3
* DynamoDB now supports AWS PrivateLink
* TimeStream (time series DB) for Influx is now GA
* ElastiCache Serverless adds more controls for scaling
* What is a blue/green (for databases - replication?)
* DevTools: AWS CloudFormation: new validation checks for stack operations; StackSets launches ListStackAutoDeploymentTargets API
  * CF console now supports visualization of stacks in Application Composer
  * CodeBuild now supports custom images (Docker) for Lambda compute - prepopulate for specific tools
  * Now supports GitLab and GitLab Self-Managed
* BedRock GenAI chatbox blueprint in CodeCatalyst
* Introducing AWS CodeConnections, formerly known as AWS CodeStar Connections: CodeStar Connections API will be disabled in April 2025
* AI/ML:
  * Bedrock now available in Paris
  * Claude3 Haiku now new
  * Mistral Large now only available in Paris
  * Knowledge DB now supports metadata filtering (knowledge bases are the RAG feature)
  * Now lets you customize prompts and the number of retrieval results
  * Offers support for CF and Service Quotas
  * AWS announces a 7-day window to return Savings Plans
  * AWS cost allocation tags now support retroactive application
* Announcing AWS Deadline Cloud: rendering service, for 2D/3D rendering
* Amazon Location Service for iOS and Android
* AWS Munich Office Event: The well-architected startup - resilient rhapsody - 24th April (https://AWS-startup-lofts.com/emea/events)
* May 7th: not the Lego-building at Neuperlach, but near Odeonsplatz
