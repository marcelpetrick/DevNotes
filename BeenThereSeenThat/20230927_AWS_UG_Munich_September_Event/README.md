20230927_AWS_UG_Munich_September_Event

# 20230927 AWS UG Munich September Event

```
With the AWS Community Day DACH on Sept 14th (register here: https://www.aws-community-day.de/) we have the most exciting AWS Community event of the year in our home town, but nevertheless we keep up the pace with another meetup of the AWS UG Munich just 2 weeks after!

And this meetup will be a special one as Viktoria Semaan from AWS San Diego will join us!

This time we meet at ARES Consulting and as always get food and drinks sponsored. Let's pray for good weather as we then can enjoy their fabulous roof top terraces!

AGENDA:

18:30 - Doors open, networking, drinks, food

19:15 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:00 - Viktoria Semaan (AWS) & Maarten Smeets (Mendix) & Ravi Singh (Mendix): Architecting highly available, multi-Region applications

21:00 - Jonatan Steuernagel (ARES Consulting) - IPv6: Why and How to Embrace it Today, using Transitional Mechanisms

21:45 - More drinks, more networking

If you have an office or co-working space where we can meet (100-150 people), want to sponsor drinks/food or have a (lightning) talk you want to present - please let us know!

Everyone who participates in an AWS UG Munich event must adhere to the Code of Conduct!
```

-----

* host: Markus Ostertag
* hosted by Ares Consulting
* cloud practitioner maybe later, first the solution architect

## AWS Important Releases
* in 14d next meetup
* AWS global accelerator now supports client IP preservation - what means NLB? good for geolocation
* announcing AWS dedicated local zones: inside your own building - you are the only ones, who work with it then(!?)

### Compute
* get lots of instances in Oregon, Ireland, ..
* EC2 R7iz instances are memory-optimized
* D3en - dense HDD-storage
* EC2 M7g and R7g instances are now available in Frankfurt
* with 7th family price increase; which is very unusual
* EC2 M6i and R6i instances now in Zurich
### Network
* announces Public IP insights, a new feature of VPC IP address manager - because starting with 2024 IPv4 will cost money
* NLB got all the traffic, now you can put security groups on top of it - for instance, block all traffic except certain ports already at the entry of the AWS-network
### Storage
* S3 inventory can include ACLs, but you should use IAM bucket policies
* mountpoint for S3 generally available
### Serverless
* Lambda now detects and stops recursive loops in Lambda functions (SQS and SNS)
* because this was costing a load of money - now the detection breaks those loops
* eventbridge scheduler can now be auto-deleted
### Databases
* Aurora PostgreSQL now supports pgvector to store embeddings (for ML models)
* Aurora supports now local write forwarding for MySQL
* Aurora global database introduces global database failover
* DocumentDB now supports document compression (lz4)
* Aurora and RDS get beyond the community end-of-life support (with a price tag): AWS will put the critical security fixes; tradeoff money against migration..
### Analytics
* CloudWatch supports regex filter syntax format
* automatically creates views, with filtering; gives also ratio and sample sizes <-- looks quite promising
### DevTools
* CodeCatalyst now supports workflows triggered by GitHub pull request
* CodePipeline now supports GitLab
### ML
* Amazon Transcribe now supports Toxicity Detection for spoken conversations
  * can tell now on a meta-level if harmful content inside the transcribed text/sentiment analysis
### Else
* WorkSpaces announces new Linux client with versions supporting Ubuntu 20.04 and 22.04
* next meetup will be at the 10th of October "Gaszählerwerkstatt" at Stadtwerke Munich - quick start until tomorrow, when it is announced officially
# Architecting Highly Available, Multi-Region Applications
* Viktoria Seeman, previously Mendix, now DevRel, came from California
* Marten Smeets and Ravi Singh from Mendix as well, subsidiary of Siemens
* "Everything fails, all the time" CTO Werner Vogels
* mitigation with failover in case something fails - quite clever; softens the impact
* 99.99% availability

### Resilience
* three-part framework: high availability, disaster recovery, and continuous improvement
* 32 AWS regions and 102 availability zones right now
* each AZ is one or more discrete data centers
* natural disaster, technical failure or human actions can be the causes
* backup/restore -> pilot light -> warm standby -> multi-site active/active
  * but becomes more and more expensive with each step right
* Google: AWS cloud product for information about the 240 current services

## Now: Marten Smeets from Mendix
* outages can't happen, service disruptions
* multi-region failover has problem for regulatory reasons: constrained by governments
* Mendix is a low-code application platform
* promise is by doing that you can add more people to your maker force; anybody who is conceptually able to develop the use case
* idea is to make more people productive: from small businesses to very large ones
* Mendix also helps with a managed service to create pipelines and deployments: this helps to run the application and still comply with security, ..
* 300k+ developers using their platform; over 16k production applications; 2k customers; 16k RDS instances (most instances in a single account); 600 EC2 instances - moving from Cloud Foundry towards Kubernetes - this is quite a lot; 14 regions
  * highly automated for the rollout
* fail: December 7, 2021: network traffic error; customers could not deploy apps anymore, also apps were running but were not available
* active/active would be best from the view of an architecture, but is super expensive; warm-standby is good enough for most customers with the fitting price point

## Now: Ravi: also Mendix
* options: auto-healing (container dies - restart); multi-AZ failover, horizontal scaling
* PaaS - platform as a service?
* RPO of 15 min as requirement from a big automotive customer - they realized they can't provide this
* database and file storage are replicated to a different availability zone within the same region; the replicas are kept in sync
* if the app is horizontally scaled, then there will be also app containers in the second AZ
* then: commitment to SLA of 99.95% and RPO of 15 min; RTO of 90 mins
* multi-region failover does not happen for minor issues
* initially PostgreSQL, now Aurora, which is prepared for that global replication
* AWS does the heavy lifting, Mendix does it not
* S3 buckets are with a bidirectional sync replicated
* invested heavily into monitoring: active and passive part; data is collated and processed with SQS to create a health alarm
* additionally: synthetic monitoring: canary application which collects data from all other regions -> then triggers an alarm
* demos with failover and failback
