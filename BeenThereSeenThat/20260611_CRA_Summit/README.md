# 20260611 CRA Summit - NXP & Toradex in Munich
* 09:00 to 18:00
* TODO add the agenda from OCR-ed image

* ~100 participants in the Bürgerbräukeller

## 1st talk: CRA overview - David Osterberger - from TÜV Süd
* Reporting obligations begin September 2026 for vendors
* December 2027: all requirements must be applied
* Products in scope: hardware products, laptops, clients, software clients (e.g., operating systems), and remote software data processing capabilities (cloud)
* Exclude: hobby software; software only sold to friends
* Products under other standards (military, marine, medical) do not fall under this regulation
* Categorization into four different groups:
* Reporting obligations: if a vulnerability is discovered in a library you use, you must find a way to fix it
* Provide software updates during the support period for at least 5 years
* Needs conformity assessment: falls under CE marking
* Technical requirements: available without exploitable vulnerabilities, secure by default configuration, software updates, access control, data confidentiality and integrity, security logging, availability of essential functions, control data outflow, data deletion, limit attack surfaces, limit impact of attacks, minimization of data processing
* product lifecycle management design, develop and production -> deliver< -> maintenance
* minimum of five years support period
  * Five years individually from product launch for each device sales date
* CE marking for manufacturers: identify applicable directives -> create EU declaration of conformity and affix the CE marking... SEE PHOTO
* Requirements are governed by EU new legislative directives
* Manufacturers must conduct regular audits, tests, and evaluations
* Take care that third parties and open source components do not compromise product security
* Vulnerability management requirements: single reporting platform by ENISA by September 2026
* Reporting timelines: 24h for the first report on the vulnerability; max 72 hours for comprehensive description of the vulnerability and incident
* todo photo of the decision tree: for the CRA compliance check


-------------

## John Oster: Resilience - navigating the CRA for resilience and competitive advantage
* Lead for the cybersecurity department there, chair for some UPTANE standards (update for automotive, 5 years with Toradex)
* "It's the Cyber Resilience Act, not the Cyber Security Act or Cyber Defense Act" - he liked that sentence
* Risk management: four tools: prevent the risk (ideal); mitigate the damage from the threat, transfer (the risk - CRA does not allow this; full responsibility as manufacturer); accept (residual risk - just accept this)
* CRA standards process (i brief)
  * horizontal standards: general standars, that apply across all pridouct categories
  * vertical standards: more detailed standards, specific to a particular product category
* vertical standars will be harmonized: more efficient to apply them; presumption by applying them - means you apply all the standards  
* ETSI standards (verticals): like WP38 tamper resistant microcontrollers


* quesiton: do securitsy products have to have automatic updates? not gonna make sense; due to closed networks, etc. cra is risk management framework -> so docment in the risk assessment what the intendendd reasonable uses are; then done
  * asutomatic updates text: ".. if applicable .."
  * so when you plug in a usb-stick, that the updates start: when reaosnable without more user interaction? in person via usb-stick could be fitting; but have to see how the regulators will view this
  
-------------

## 3rd talk: BE solutions - icing on the cake - Philippe Dmitiry
* different from ten years ago to now
* 10y ago: hardware features differnetiated; software had to run along with it
* Today the situation has changed: developing products has to be developed, maintained and secured
* Major difference: cyber threats. 10 years ago nobody cared because it wasn't important
* buainess requirements versus techncial requirements:
  * Business requirements: faster time to market (major); reduced engineering effort; predictable lifecycle costs, reduced operational risk; compliance readiness
  * Technical requirements: secure OTA updates; containerized applications; fleet monitoring; reproducible deployments, secure software supply chain; vulnerability management; long-term maintenance
* Maintaining the product is now a major requirement; over OTA; and when secure - even better
* Vulnerabilities have to be found, managed, tracked and fixes deployed
* so to fulfill the market needs you need to cover everything
* more important: to have a platform for all those topics is more important than just a build system (like yocto)
* 10 people in the company, so limited team and resources: so how to handle this? SBOM, OTA, vulnerability management, monitoring, containers, fleet management... all already included
* within one year to put the first version onto the market

-------------

## 4th talk: amelia alder  - cybersecurity grc manager at knorr-bremse
* talking about the product liability
* running unsupported systems many be interpreted as operating below expeced safet levels (risk mangement, NIS2)
* CRA suüport period ends IS NOT safe harbour
* incident after support period finishes: then there could be also claims afterwards; five yers after the support period ends -> claimto econimic operator
* product includes software (and digital manufacturing files)
* pld - product liability directive says and aplies to products to products which are substantially modified when being put to service
* defective it it lacks the saety eole are entitled to expect/required by law

-------------
# The CRA - a paradigm shift - jenirathese nadar
* Jeni Nadar - System Sales LEad Security
* the inofficial CRA guy from NXP
* NXP is not doing anything regarding CRA - as fair feedback
* as reference: http://nxp.com/cra - check then the documentation section
* application notes for multiple different appliances: home apps, ..
* just a legal recommendation, not an advice
* essential cybersecurity checklist: only for own tracking, not legal advice
* recommend to give the design to another tesam which is not inviolved into the design process; or thrid party for risk assessment
* atechnokogy agnostic approach: CRA sets device security principles without specyfying how
* CRA ECRs cover: product configuration, rpoduct authentication, acces to product, data protextion, product monitoring and cyber state awareness, vulneraviblit fi xand product update, reduction of incidents impac and product availabilit
* cra does not specify: level of security; level of protections must reflect the lefel f risks, depending on product type, use case and application; functional requirements cryptogaphic algorithms proctols, pki, x.509 certificate format, etc.; technoloogical impelemtnatios; security hardware, software, etc
* no refernce that sas it has to be in hardware: but NXP would say yes
* Secure Enclave as new feature sometimes in sync with TrustZone

-------------
# dr. peiet TODO - product security guy
* encourage people to do their own risk assessment
* he is one company, speciliazes in CRA and RED
* linux foundation: survey 68 % or organisations are unwaware with the CRA - last sear 66% - so in europe also as bad as rest of the world
* many irganizations will have a lot of work to be CRA comliant
* mATURITY NEEDED: LEARN TO BUILD SECURE DEVICES
* myth: the CRA legal text should give us clear requreiemtns - it does not; because fluffy; NLF essential requirements are made more specific by stanrads: out of oa one sentence essential requirement fllow a standard with ike 100 pages
  * software may not harm kittens -> where lasers are used to create a product, the optical power should not be higher thna 1 mW.
* CRA asessment procedures: TODO add photo
* establish the product context: for home or for factory?; risk acceptance criteria, asset identification, threat identification, risk assessment, your own securit requirements, secure design, secure implementatio, testing and validation, risk monitoring & review
* you as manufacturer are responsible fo the whole product: your part of software and  ALL components and libraries and dependencies! - check if that is secure

-------------

# burkhard stubert - from threat modeling to risk assessment
* threat is a violation of essential product property
* example 2d: access control -> threat (from unauthoried access) to securtiy measure (by appropriate control mechanism, including ahtentication, identiy or access mangement system and report on possible unahtorised access)
* amdm shostack: four question framework for threat modelling:
  * what are we working on? user stories related to system nteractions
  * what can go wrong? violeated product properties (threats)
  * what are we going to do about it? elimint, reduce, accept, transfer,rssk; security measures to mitigate violations
  * did we do a good job? review of all violations fund; write tests for violations
* mititate risk from supplier by asking them about their assessment
* use security decision records - as markdown, in git repo
* add user story to sdr context
* slides from website
* brainstorm for the violations mitigtation efforts
* security critical functionalty on demand: good recipe to mitigate security problems; limit time when a device can be attacked; someone needs ophysical access; intentional tactivation
* with mitgations it should nt get worse; should only get better
* validate the risk assessment, when you do an important update : CRA stands for continuous risk assessment.. from his opinion

-------------

# build versus buy under the CRA: jon Oster
* the toaster project .. do everything from scratch
* overbuilding has a failure mode; buying has one as well
* rules of thumb for doning evaluation: for security products:
  * open is better than closed
  * standards-based is better than custom
  * a system ou full y understand is better than a black box
  * for open source: paid maintainers are better than hobby projects
  * but OSS projects comindated by a single company can be risky
* it costed us a meaningful amount of development time
* dont roll your own crytpo; bruce schneier
* what do we mean when we say: software update update system?
  * 4 elements:
    * a repository where update and metadata are stored, new updates are uloaded, may include feleet management functionality
    * an update agents responsible for interacting with th respotiroy (downloading updates, verifying integrity, reporting oin currently installed software)
    * one or more backends for installing the software once downloaded and validated
    * a protocol for how these elements interact
* new ENISA echnical advisory on secure update mechanism: 
* use standrd VEX for vulnerability exposure: cyclone DX vex, openVEX
* dont want to have so many false positives
* but alsdo dont wanna miss real issues
a funnel: all CVE are like 500k -> 2k are applying to your SBOM -Y VEX files then shrink it to 50 -> your threat model cuts it down to 10 -> remediate those (mitigteu, dapted, mitigate)
* vuknerability manager with torizon
* ariana from security pattern; or vulnscout.io from yocto; dependenc track; onekey; guac
* 


-------------


* challenge: sbom generation for c++ products; cdxgen - works, but reports too many, example stm32 project; then do some curation ... but is this not a source for failure because not fully automateable?


* using fable 5 to rename a vairable ..
  * talk about how breaking the flow, like for creating a document is interrupting your work. so even when overkill i saometimes dictate directl to the agent, then tell him to create the document himself. less overhead.

  * ran qwen3.5:3b locally ro fix the grammar errors. 270k tokens (8 min with battery saving) later we had a fixed version. good. But one api call for GPT3 three years ago could fix it in seconds .. way less energy consumption
