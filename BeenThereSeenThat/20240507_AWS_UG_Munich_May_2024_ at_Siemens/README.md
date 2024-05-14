# 20240507 AWS UG Munich May 2024 - at Siemens

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


## Intro from Markus Ostertag
* EC2 now protects your AMIs from accidental deregistration
* EC2 simplifies visibility into your active AMIs
* AMI: Amazon Machine Images: additional flag; unlock first before deleting the AMI
* Drill from AMI to EC2; instead of just EC2 to AMI like before; data not gathered historically, just after launch
* EFS increases maximum per client throughput to 1.5 Gbit/s
* Amazon EKS: split cost allocation is possible
* CloudFront now supports Origin Access Control (OAC) for Lambda function URLs as origins
* Denial of wallet: brute forcing (is/was possible)
* AWS Glue Studio notebooks are now available in 6 additional regions
* DynamoDB: now supports an FIS action to pause global table replication
  * Introduces configurable maximum throughput for on-demand tables: prevents denial of wallet
* Monitoring/observability: Internet weather map
* AWS CloudFormation change sets now offer enhanced change visibility for deployments
* CodeCatalyst introducing:
  * File commit history
  * Workflow approval gates (aka: someone should press a button)
* KMS announces more flexible automatic key rotation
  * Price is now capped at $3/month max
* Amazon Personalize now makes it easier to delete users from datasets
* AI/ML:
  * Bedrock: new models available; Claude 3 Opus, Amazon Titan Image Generator, and Titan Text Embeddings v2, Cohere Command R and R+ are now available
  * Agents for Amazon Bedrock now with Claude3 Haiku and Sonnet
  * Guardrails for Bedrock now generally available
  * Custom model import for Amazon Bedrock in preview
  * Knowledge bases now support multiple data sources
  * Model evaluation on Amazon Bedrock is now GA
  * Knowledge bases now support MongoDB Atlas for vector storage
  * Amazon Q (as an answer to MS Copilot)
    * Q Developer is now GA (includes CodeWhisperer), Q Apps now in Preview, Q subscription management now available
    * Meta's LLaMA 3 now available via SageMaker JumpStart and Bedrock
    * Q in QuickSight now GA: like building presentations
    * Q Apps is the professional thing - based on PartyRock: give it a prompt
* Backdoor through Q? No, looks like it does check if you should have access to that resource
* Introducing workflow monitor for AWS Media Services
* AWS Well-Architected Tool connector for JIRA

* Next meetup: June 12th, Scalable Capital

# Leo Hanisch - Lambda-lith
* Business solutions and platforms is his department
* Get rid of Excel and emails: customers are actually different Siemens departments
* 30 experts: from project management to business analysts, front and backend developers, solution architects, ...
* Scalable, hybrid team setups (more than 80 projects p. a.)
* People come with a problem statement to them
* Not only implement them but also operate them throughout the whole lifecycle
* Munich is an HQ for Germany
* AWS certified solutions architect, cloud chapter lead for their department
* Enthusiastic about anything serverless
* Use case: product master data
  * Hardware components evolve over time
  * Architecture: Amazon API Gateway <-> AWS Lambda <-> (CRUD) Amazon DynamoDB
  * But is this suitable for complex processes?
  * Lambda-lith:
    * Advantages: less cold starts, easier migration from existing system (re-platforming)
    * Drawbacks: longer cold starts; synchronous execution only, difficult error handling/retries, bundle size limits
  * But is listed as anti-pattern for lambda-based applications: increases cognitive burden on developers
  * Single key and very nested object, then you have to scan every table for filtering
  * Maybe do a flat setup: only top-level keys?
  * Why would you use it: re-platforming, easy to get started with AWS, because you do not know better

### Second use case: Siemens COIN - get Siemens shares
* Now same pattern, but with Amazon Aurora instead of DynamoDB:
* Created several smaller lambda-liths
* An endpoint and a lambda function create a microservice
* Drawback: once a year HR will run their annual email campaign: share matching program -> within few hours thousands of users: scaling (no problem?):
  * Therefore they configured a proxy before the writers: enable enhanced connection handling
  * Configure automatic scaling for readers on the Aurora cluster
  * Challenge your assumptions!

### Digital visit management - use case
* Do a tour for potential customers: to convince them to build with Siemens
* Really huge flowchart for the state machine: primary thought: AWS Step Functions?
* Enables async communication
* Event-driven mindset is closer aligned to the business use case
* Decouple your system into smaller domains
* Smaller blast radius in case a microservice fails
* Learned: plan for observability; one big Step Function can become overwhelming; do not create its own orchestration service
* Be aware of duplicate events: due to event-driven architecture, but also some services emit certain events twice

### Last use case: my digital lab assistant
* In collaboration with Siemens Healthineers
* Idempotency: identify repeated events and prevent duplicated, inconsistent, or lost data
  * How to:
    * Extract a unique attribute of input event
    * Control database for identification? If it does not exist, just continue with the original action; if it exists, just do nothing (stop processing gracefully)
* Learned: use X-Ray to trace requests; use common log format; prefer smaller Step Functions over a big one; use versioning to ensure backward compatibility, use idempotent event handler to increase resiliency

* Plan your architecture to adapt!
