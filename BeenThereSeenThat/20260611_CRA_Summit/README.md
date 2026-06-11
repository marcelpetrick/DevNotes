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

## John Oster: Resilience
* TBC

-------------

* challenge: sbom generation for c++ products; cdxgen - works, but reports too many, example stm32 project; then do some curation ... but is this not a source for failure because not fully automateable?
