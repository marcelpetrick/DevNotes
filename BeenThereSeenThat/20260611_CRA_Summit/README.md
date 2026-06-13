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
* product lifecycle management design, develop and production -> deliver -> maintenance
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
* CRA standards process (in brief)
  * horizontal standards: general standards, that apply across all product categories
  * vertical standards: more detailed standards, specific to a particular product category
* vertical standards will be harmonized: more efficient to apply them; presumption by applying them - means you apply all the standards  
* ETSI standards (verticals): like WP38 tamper resistant microcontrollers


* question: do security products have to have automatic updates? not gonna make sense; due to closed networks, etc. cra is risk management framework -> so document in the risk assessment what the intended reasonable uses are; then done
  * automatic updates text: ".. if applicable .."
  * so when you plug in a usb-stick, that the updates start: when reasonable without more user interaction? in person via usb-stick could be fitting; but have to see how the regulators will view this
  
-------------

## 3rd talk: BE solutions - icing on the cake - Philippe Dmitiry
* different from ten years ago to now
* 10y ago: hardware features differentiated; software had to run along with it
* Today the situation has changed: developing products has to be developed, maintained and secured
* Major difference: cyber threats. 10 years ago nobody cared because it wasn't important
* business requirements versus technical requirements:
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
* running unsupported systems may be interpreted as operating below expected safety levels (risk management, NIS2)
* CRA support period ends IS NOT safe harbour
* incident after support period finishes: then there could be also claims afterwards; five years after the support period ends -> claim to economic operator
* product includes software (and digital manufacturing files)
* pld - product liability directive says and applies to products which are substantially modified when being put to service
* defective if it lacks the safety people are entitled to expect/required by law

-------------
# The CRA - a paradigm shift - Jeni Nadar
* Jeni Nadar - System Sales Lead Security
* the inofficial CRA guy from NXP
* NXP is not doing anything regarding CRA - as fair feedback
* as reference: http://nxp.com/cra - check then the documentation section
* application notes for multiple different appliances: home apps, ..
* just a legal recommendation, not an advice
* essential cybersecurity checklist: only for own tracking, not legal advice
* recommend to give the design to another team which is not involved into the design process; or third party for risk assessment
* technology-agnostic approach: CRA sets device security principles without specifying how
* CRA ECRs cover: product configuration, product authentication, access to product, data protection, product monitoring and cyber state awareness, vulnerability fix and product update, reduction of incidents impact and product availability
* cra does not specify: level of security; level of protections must reflect the level of risks, depending on product type, use case and application; functional requirements cryptographic algorithms protocols, pki, x.509 certificate format, etc.; technological implementations; security hardware, software, etc
* no reference that says it has to be in hardware: but NXP would say yes
* Secure Enclave as new feature sometimes in sync with TrustZone

-------------
# dr. peiet TODO - product security guy
* encourage people to do their own risk assessment
* he is one company, specializes in CRA and RED
* linux foundation: survey 68% of organisations are unaware of the CRA - last year 66% - so in europe also as bad as rest of the world
* many organizations will have a lot of work to be CRA compliant
* mATURITY NEEDED: LEARN TO BUILD SECURE DEVICES
* myth: the CRA legal text should give us clear requirements - it does not; because fluffy; NLF essential requirements are made more specific by standards: out of a one sentence essential requirement follow a standard with like 100 pages
  * software may not harm kittens -> where lasers are used to create a product, the optical power should not be higher than 1 mW.
* CRA assessment procedures: TODO add photo
* establish the product context: for home or for factory?; risk acceptance criteria, asset identification, threat identification, risk assessment, your own security requirements, secure design, secure implementation, testing and validation, risk monitoring & review
* you as manufacturer are responsible for the whole product: your part of software and ALL components and libraries and dependencies! - check if that is secure

-------------

# burkhard stubert - from threat modeling to risk assessment
* threat is a violation of essential product property
* example 2d: access control -> threat (from unauthorized access) to security measure (by appropriate control mechanism, including authentication, identity or access management system and report on possible unauthorized access)
* adam shostack: four question framework for threat modelling:
  * what are we working on? user stories related to system interactions
  * what can go wrong? violated product properties (threats)
  * what are we going to do about it? eliminate, reduce, accept, transfer, risk; security measures to mitigate violations
  * did we do a good job? review of all violations found; write tests for violations
* mitigate risk from supplier by asking them about their assessment
* use security decision records - as markdown, in git repo
* add user story to sdr context
* slides from website
* brainstorm for the violations mitigation efforts
* security critical functionality on demand: good recipe to mitigate security problems; limit time when a device can be attacked; someone needs physical access; intentional activation
* with mitigations it should not get worse; should only get better
* validate the risk assessment, when you do an important update : CRA stands for continuous risk assessment.. from his opinion

-------------

# build versus buy under the CRA: jon Oster
* the toaster project .. do everything from scratch
* overbuilding has a failure mode; buying has one as well
* rules of thumb for doing evaluation: for security products:
  * open is better than closed
  * standards-based is better than custom
  * a system you fully understand is better than a black box
  * for open source: paid maintainers are better than hobby projects
  * but OSS projects dominated by a single company can be risky
* it cost us a meaningful amount of development time
* don't roll your own crypto; bruce schneier
* what do we mean when we say: software update update system?
  * 4 elements:
    * a repository where update and metadata are stored, new updates are uploaded, may include fleet management functionality
    * an update agent responsible for interacting with the repository (downloading updates, verifying integrity, reporting on currently installed software)
    * one or more backends for installing the software once downloaded and validated
    * a protocol for how these elements interact
* new ENISA technical advisory on secure update mechanism: 
* use standard VEX for vulnerability exposure: cyclone DX vex, openVEX
* don't want to have so many false positives
* but also don't wanna miss real issues
a funnel: all CVE are like 500k -> 2k are applying to your SBOM -> VEX files then shrink it to 50 -> your threat model cuts it down to 10 -> remediate those (mitigate, adapted, mitigate)
* vulnerability manager with torizon
* ariana from security pattern; or vulnscout.io from yocto; dependency track; onekey; guac
* 


-------------


* challenge: sbom generation for c++ products; cdxgen - works, but reports too many, example stm32 project; then do some curation ... but is this not a source for failure because not fully automatable?


* using fable 5 to rename a variable ..
  * talk about how breaking the flow, like for creating a document is interrupting your work. so even when overkill I sometimes dictate directly to the agent, then tell him to create the document himself. less overhead.

  * ran qwen3.5:3b locally to fix the grammar errors. 270k tokens (8 min with battery saving) later we had a fixed version. good. But one api call for GPT3 three years ago could fix it in seconds .. way less energy consumption
