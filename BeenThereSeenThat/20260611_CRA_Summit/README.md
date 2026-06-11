# 20260611 CRA Summit from Toradex and NXP in Munich
* 0900 to 1800
* TODO add the agenda from OCR-ed image

* maybe 100 participants in the bürgerbräukeller

## 1st talk: CRA overview - David Osterberger - from TÜV Süd
* September2026 reporting duties for vendors
* december 2027 all requirements have to b applied
* which products are in scope: harware product, laptops, clients, software clients like operating systems; and remote software data processing capabilities (cloud stuff)
* exclude: hobby software; only sold to friends
* also things under other standards: military, marine, medical .. does not fall under that regulation
* categorization into four different groups: 
* reporting obligations! due to some bug or some lib you use has a vuln, then have to find way to fix this
* provide software updates, during support period, at least 5 years
* also needs conformity assessment: falls now under CE
* technical requirements: made available without exploitable vulns, secure by default configutation, software updates, acces control , data confidentiality and integrity, security logging, availability of essential functions, control data outflow, data detletiin, limit attack surfaces, limit impact of attacks, minimisation of data processing
* security updates for free, functional updates - you can take money; so maayb separate tehm
* data deletion: even comissioning is to be kept in mind; even if thrown away, how to delete the data safeyl?
* product lifecycle management design, develop and production -> deliver< -> maintenance
* minimum of five years support period
  * five years individually from product launch for each device sales date
* CE marking for manufacturers: identify applicable directives -> create eu declatation of conformity and affic the CE marking, ... SEE PHOTO
* requirements are governed by the EU new legislative directirves
* manfacturer ms conduct regular audits and tests and evaluations
* take care that 3rd parties and open source components do not compromise product secrity
* requirements for vuln management: single reporting platfom by enisa by september 2026
* timelines for reporting: 24h for th first report on the vulnerability; max 72 hours comprehensive description of the vulnerability and incident
* todo photo of the decision tree: for the CRA compliance check


-------------

## John Oster: Resilience - navigating the CRA for resilience and competitive advantage
* lead for th cyber security deparment there, chair for some uptane standard (update for automotive, 5 ears with toradex)
* "its the cyber resilience act, not the cyber seuritct act or cyber defense act"" - he liked that sentence
* risk managemtn four tools: prevent the risk (ideal); mitigate the damage from the threat, transfer (the risk - CRA does not allow this; full responsibility as manufacturer); accept (residual risk - jsut accept this)
* CRA standards process (i brief)
  * horizontal standards: general standars, that apply across all pridouct categories
  * vertical standards: more detailed standards, specific to a particular product category
* vertical standars will be harmonized: more efficient to apply them; presumption by applying them - means you apply all the standards  
* ETSI standards (verticals): like WP38 tamper resistant microcontrollers


* quesiton: do securitsy products have to have automatic updates? not gonna make sense; due to closed networks, etc. cra is risk management framework -> so docment in the risk assessment what the intendendd reasonable uses are; then done
  * asutomatic updates text: ".. if applicable .."
  * so when you plug in a usb-stick, that the updates start: when reaosnable without more user interaction? in person via usb-stick could be fitting; but have to see how the regulators will view this
  
-------------

## 3rd talk: BE solutions - icing on the cake - philippe dmitiry - fix the name TODO
* different from ten years ago to now
* 10y ago: hardware features differnetiated; software had to run along with it
* today the situation has changed: dveloping produt has to be delveope, maintained and to be secured
* major difference is the cber threats: 10y ago nobody cared because not important
* buainess requirements versus techncial requirements:
  * business req: fater time to market, ( major); reduced engineering effort; predictable lifecycle costs, reduced operational risk; compliance readiness
  * technical requirements: secure OTA updates; containerized applications; fleet monitoring; reproducible deyploemnets, secure software supply chain; vulnerability manangement; long term maintenance
* maintaining the product - is now a major requirement; over OTA; and when secure - even better
* vukn. habve to be found, managed, ttracked and fixes to be deployed
* so to fulfill the market needs you need to cover everything
* more important: to have a platform for all those topics is more important than just a build system (like yocto)
* 10 people inthe copmpany so limited team and ressources: so how to handle this? SBOm, OTA, vuln management, monitoring, containers, fleet management ... all already included
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
* 




-------------

* challenge: sbom generation for c++ products; cdxgen - works, but reports too many, example stm32 project; then do some curation ... but is this not a source for failure because not fully automateable?


* using fable 5 to rename a vairable ..
  * talk about how breaking the flow, like for creating a document is interrupting your work. so even when overkill i saometimes dictate directl to the agent, then tell him to create the document himself. less overhead.
