# AWS UG Munich May 2024

```
It definitely is one of the most known companies in Munich, but nevertheless the AWS User Group Munich didn't had the chance to visit their offices... until now! We're very happy to be able to meet at the Siemens AG office at Wittelsbacherplatz this time and thankfully get food and drinks provided.

Please note that due to office security regulations you need to enter your real name in the registration form and provide an ID while entering the building.

AGENDA:
18:30 - Doors open, networking, drinks, food

19:00 - Markus Ostertag (AWS Hero): Recent AWS announcements

20:00 - Leo Hanisch (Siemens AG): From a Lambda-Lith to an Event-Driven Architecture: Lessons Learned

20:45 - Raphael Manke (codecentric AG): Supercharge Lambda functions with AWS Powertools

21:30 - More drinks, more networking
```

## intro from markus ostertag
* ec2 now protects your AMIs from accidental dergeistration
* ec2 simplfies visibitlit inyt your actve AMIs
* AMI: amazon machine images: additional flag; unlock first before deleting the ami
* drill from ami to ec2; instead of just ec2 to ami like before; data not gathered historiacally, just after launch
* EFS increases maximum per cleint throuhpu to 1.5 Gbit/s
* Amazon EKS: split cost allocation is possible
* cloud front now supports Origin Access Control (OAC) for Lambda function URL originas
+ denial of wallet: bute forcing (is/was possible)
* AWS Glue studio notebooks is now available in 6 additional regions
* DynamoDB: now supports and FIS action to pause global table replication
  * introduces configurale maximum throughput for on-demand tables: prevents denial of wallet
* onitoring/observability: internet wather map
* AWS cloudformation changesets now offer enhanded change visibility for deployments
* codecatalyst introducing:
  * file comit history
  * workflow approval gates (aka: someone should press a button)
* KMS announces more flexible atomatic key rotation
  * price is now capped a 3$/month max
* amaon personalize mow makes it easier to delete users from datasaets
* AI/ML:
  * bedrock: new models available; claue 3 opus, amazon titan image enerator and titant text embeddings v2, cohere command R and R+ are now available
  agents for amazon bedrock now with claue3 haiku and sonnect
  guardrails for bedrock now generall availabl
  custom model import for amazon bedrock in preview
  * knowledge bases now support multiple data source
  * model evaluation on amazon bedrock is now GA
  * knowlege bases now supprots mongodb atlas for vector storage
  * Amazon Q (as answer to MS copilot)
    * Q Devloper is now GA (includes CodeWhisperer), Q Apps now in Preview, Q subscritipion management now available
    * meta's llam 3 now available via sagemaker jumpstart and bedrock
    * Q in Quicksight now GA: like building presentations
    * Q Apps is the professional thing - based on partyrock: give it a prompt,
* backdoor through Q? no, looks like it does heck f you should have access to that ressource
* introducting workflow monitro for AWS media services
* AWS well archiectured tool connector for Jia

* next meetup: june 12th Scalable Capital

