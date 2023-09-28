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

* host: Markus Ostertag
* hosted by Ares consulting
* cloud practitioner maybe later, first the solution architect

## AWS Important Releases
* in 14d next meetup
* AWS global accelerator now supports client i preservation - what means NLB? good for geolocation
* announcing aws dedicated local zones: inside your own building - you are the only ones, who work with it then(!?)
### Compute
* get lots of instances in oregon, ireland, ..
* EC R7iz instances are memory optimized
* D3en - dense HDD-storage
* EC M7g and R7g insances are now available in Frankfurt
* with 7th family price increase; which is very unusual
* EC2 M6i and R6i instances now in Zurich
### network
* announces Public ip insights, a new feature of VPC IP adress manager - because starting with 2024 ipv4 will cost money
* NLB got all the traffic, now you can put scurity groups on top of it - for instance block all traffic except certain ports already ath the entry of the AWS-network
### storage
* s3 invetory can inclue ACLs, but you should use IAM bucket policies
* mountpoint for S3 generally available
### serverless
* lambda now detects and stops recursive loops in lambda functions (SQS and SNS)
* because this was osting a shitload of money - now the detection breaks those loops
* evenbridge scheduler can now auto-deleted
### databases
* aurora PostgreSQL now supports  pgvector to store embeddings (for ML models)
* aurora supports now local write forwarding for MYSQL
* aurora global datase introduces global database failover
* documentdb now supports document comression (lz4)
* aurora and rds get beyond the community end of life-support (with a price tag): AWS will put the critical security fixes; tradeoff money against migration..
### analytics
* cloudwatch supports regex filter syntax format
* automatically creates views, with filtering; gives also ratio and sample sizes <-- looks quite promising
### DevTools
* codecatalyst now supports workflows triggered by github pull request
* codepipeline now supports gitlab
### ML
* Amazon Transcribe now supports Toxicity Detection for spoken conversations
  * can tell now on a meta-level if harmful content inside the transcribed text/sentiment analysis
### Else
* workspaces announces new linux client with versions supporting ubuntu 20.04 and 22.04
* next meetup will be at the 10th of octobre "gaszählerwerkstatt" at Stadtwerke Munich - quickstart until tomorrow, when it is announced officially
# Architecting highly availalbe, multi-region applications
* viktoria seeman, previously mendix, now DevRel, came from california
* marten smeets and ravi singh from Mendix as well, daughter of Siemens
* "verything fails, all the time" CTO Wener Vogels
* mitigation with failover in case something fails - quite clever; softens the impact
* 99,99% availability

### resilience
* three part framework: hgih availability, disaster recovery, and continuous improvement
* 32 AWS regions and 102 availabilty zones right now
* each AZ is one or more discrete data centers
* natural disaster, technical failure or human actions ca be the causes
* backup/restore -> pilot light -> warm standby -> multi-site active/active
  * but becomes more and more epensive with each step right
* google: AWS cloud product for informations about the 240 current services

## now: Marten Smeets from Mendix
* outages can't happen, service disruptions
* multi region failover has problem for regulatory reasons: constraint by governments
* mendix is a lowcode application platform
* promise is by doing that you can add more people to your makerforce; anybody who is conceptually able to develop the use case
* idea is to make more people productive: from small businesses to very large ones
* mendix also helps with a managed service to create pieplines and deployments: this helps to run the application and still comply with security, ..
* 300k+ developers using their platform; over 16k production applications; 2k customers; 16k RDS instances (most instances n a single account); 600 EC2 instances - moving from cloud foundery towards kubernetes - this is quite a lots; 14 regions
  * highly automated for the rollout
* fail: december 7, 2021: network traffic error; customers could not deploy apps anymore, also apps were running but were not available
* active/active would be best from the view of an architecture, but is super expensive; warm-standby is good enough for most customers with the fitting pricepoint

## now: Ravii: also Mendix
* options: auto-headling (container dies - restart); multi-AZ failover, horizontal scaling
* PaaS - platform as a service?
* RPO  of 15 min as requirement from a big automotive customer - they realized they can't provde this
* database and file storage are replicated to a different availability zone within the same region; the replicas are kept in sync
* if the app is horizontally scaled, then there will be also app contianers in teh second AZ
* then: commitment to SLA of 99.95% and RPO of 15 min; RTO of 90 mins
* mult region failover does not happen for minor issues
* initially postgresql, now aurora, which is prepared for that global replication
* AWS does the heavy lfting, mendix does it not
* S3 buckets are with a bidirectional sync replicated
* invested heavily into monitoring: active nd passive part; data is collated and processed with SQS to create a health alarm
* additionally: synthetic monitoring: canary application which collets data from all other regions -> then triggers an alarm
* demos with failover and failback

