# 20260611 CRA Summit - NXP & Toradex in Munich
* 09:00 to 17:30

## Agenda
```text
Navigate The EU Cyber Resilience Act With Confidence
The EU Cyber Resilience Act (CRA) is redefining the rules for device manufacturers - and non-compliance is no longer an option.
Products that fail to meet CRA standards risk losing their CE certification, effectively closing the door to the entire EU market.
To help you navigate these changes, the Torizon CRA Summit cuts through the noise. You’ll get a clear understanding of what the CRA requires from you and how to meet those requirements in practice.
This exclusive, by-invitation-only, one-day summit - hosted by Toradex and NXP - is your opportunity to engage with industry leaders, security architects, and technical innovators.
Together, we’ll explore practical, real-world approaches for building CRA-compliant, secure, and market-ready embedded systems.
Who Should Attend

    CTOs
    Security Compliance Officers
    Technology Leaders and Product Managers

What You’ll Take Away

    How CRA will impact your business model, roadmap, and supply chain
    Practical tips on how to comply, while reducing risk, and effort
    Talk in-person with EU CRA experts, industry leaders, and security experts

09:00 - 09:30
Registration and Networking
09:30 - 09:45
Opening Remarks and Introduction
Daniel Lang | GM and Vice President
Torizon
09:45 - 10:15
Keynote: What should I do to be CRA-compliant?
David Osterberger | OT Security | Business Unit Cybersecurity Services
TÜV SÜD
10:15 - 10:30
Coffee Break and Networking
10:30 - 11.00
Keynote: Navigating CRA for Strategic Resilience
Jon Oster | Principal Product Security Architect
Torizon
11:00 - 11.15
Customer Spotlight
Dimitri Philippe | CEO
BE.services
11:15 - 11:45
Product Liability meets the CRA
Amelia Alder | CoC Product Security | Cybersecurity GRC Manager, R/IMS
KNORR-BREMSE Systeme für Schienenfahrzeuge
11:45 - 12:30
Industry Panel: Incident Response under CRA
NXP TÜV SÜDProduct Security Guru
12:30 - 13:40
Lunch: Connect With Experts
13:40 - 13:45
Afternoon Kickoff
13:45 - 14:15
How NXP Hardware Security Features Make CRA Compliance Easier
Jenirathese Nadar | Technical System Sales Lead - Security
NXP
14:15 - 15:00
Beyond the Myths: The Real Obstacles in CRA Compliance
Piet De Vaere | Product Security Consultant | Computer Scientist
Product Security Guru
15:00 - 15:15
Coffee Break and Networking
15:15 - 15:45
Risk Assessment of Essential Product Requirements by Example
Burkhard Stubert | Solopreneur and Chief Architect
Small Step Systems
15:45 - 16:30
Keynote: Build vs. Buy under CRA
Jon Oster | Principal Product Security Architect
Torizon
16:30 - 17:15
Fireside Panel: Open Source Proprietary Software and Risk under the CRA
Security Pattern Small Step Systems Product Security Guru KNORR-BREMSE Systeme für Schienenfahrzeuge
17:15 - 17:30
Closing Remarks
Daniel Lang | GM and Vice President
Torizon
17.30 onwards
One-on-One Sessions
Apéro and Networking
Why This Event Is Different
Actionable CRA
Compliance Roadmaps
Strategic Perspectives for Executives
Industry-Leading Voices
```

* ~100 participants in the Bürgerbräukeller

## 1st Talk: CRA Overview — David Osterberger (TÜV Süd)

* Reporting obligations begin September 2026 for vendors
* December 2027: all requirements must be applied
* Products in scope:
  * Hardware products
  * Laptops
  * Clients
  * Software clients (e.g., operating systems)
  * Remote software data processing capabilities (cloud)
* Excluded:
  * Hobby software
  * Software only sold to friends
* Products under other standards (military, marine, medical) do not fall under this regulation
* Categorization into four different groups
* Reporting obligations:
  * If a vulnerability is discovered in a library you use, you must find a way to fix it
* Provide software updates during the support period for at least 5 years
* Needs conformity assessment:
  * Falls under CE marking
* Technical requirements:
  * Available without exploitable vulnerabilities
  * Secure-by-default configuration
  * Software updates
  * Access control
  * Data confidentiality and integrity
  * Security logging
  * Availability of essential functions
  * Control data outflow
  * Data deletion
  * Limit attack surfaces
  * Limit impact of attacks
  * Minimization of data processing
* Product lifecycle management:
  * Design, development, and production
  * Delivery
  * Maintenance
* Minimum support period of five years
  * Five years individually from product launch for each device sales date
* CE marking for manufacturers:
  * Identify applicable directives
  * Create EU declaration of conformity
  * Affix the CE marking
  * SEE PHOTO
* Requirements are governed by EU New Legislative Framework directives
* Manufacturers must conduct regular audits, tests, and evaluations
* Ensure that third parties and open-source components do not compromise product security
* Vulnerability management requirements:
  * Single reporting platform by ENISA by September 2026
* Reporting timelines:
  * 24h for the first report on the vulnerability
  * Max. 72 hours for a comprehensive description of the vulnerability and incident
* TODO:
  * Photo of the decision tree for the CRA compliance check

---

## Jon Oster: Resilience — Navigating the CRA for Resilience and Competitive Advantage

* Lead for the cybersecurity department
* Chair for some UPTANE standards (automotive updates)
* 5 years with Toradex
* Quote:
  * "It's the Cyber Resilience Act, not the Cyber Security Act or Cyber Defense Act"
* Risk management: four options
  * Prevent the risk (ideal)
  * Mitigate the damage from the threat
  * Transfer the risk
    * CRA does not allow this
    * Full responsibility remains with the manufacturer
  * Accept the residual risk
* CRA standards process
  * Horizontal standards
    * General standards across product categories
  * Vertical standards
    * Detailed standards for specific product categories
* Vertical standards will be harmonized
  * More efficient to apply
  * Presumption of conformity when applying them
* ETSI standards (verticals)
  * Example: WP38 tamper-resistant microcontrollers

### Question: Do security products have to support automatic updates?

* CRA is a risk-management framework
* Document intended and reasonable usage in the risk assessment
* Automatic updates text:
  * "... if applicable ..."
* Example:
  * Updates via USB stick could be reasonable if they can be applied without additional user interaction
* Final interpretation depends on regulators

---

## 3rd Talk: BE.services — Philippe Dimitri

* Different from ten years ago
* 10 years ago:
  * Hardware features differentiated products
  * Software only had to run on them
* Today:
  * Products must be developed, maintained, and secured
* Major difference:
  * Cyber threats
* Business requirements versus technical requirements

### Business Requirements

* Faster time-to-market
* Reduced engineering effort
* Predictable lifecycle costs
* Reduced operational risk
* Compliance readiness

### Technical Requirements

* Secure OTA updates
* Containerized applications
* Fleet monitoring
* Reproducible deployments
* Secure software supply chain
* Vulnerability management
* Long-term maintenance

* Maintaining the product is now a major requirement
* Vulnerabilities must be found, managed, tracked, and fixed
* To fulfill market needs, you need to cover the entire lifecycle
* Having a platform for all these topics is more important than just a build system (e.g., Yocto)
* Company size:
  * 10 people
  * Limited resources
* Challenges:
  * SBOM
  * OTA
  * Vulnerability management
  * Monitoring
  * Containers
  * Fleet management
* Within one year, they put the first version on the market

---

## 4th Talk: Amelia Alder — Cybersecurity GRC Manager at Knorr-Bremse

* Product liability
* Running unsupported systems may be interpreted as operating below expected safety levels
  * Risk management
  * NIS2
* CRA support period ending is **not** a safe harbor
* Incidents after the support period ends may still lead to claims
* Up to five years after the support period ends:
  * Claims may still be made against the economic operator
* Product includes:
  * Software
  * Digital manufacturing files
* PLD (Product Liability Directive)
  * Applies to products substantially modified when put into service
* A product is defective if it lacks the safety people are entitled to expect or that is required by law

---

# The CRA — A Paradigm Shift (Jeni Nadar)

* Jeni Nadar — System Sales Lead Security
* The unofficial CRA guy from NXP
* Reference:
  * <http://nxp.com/cra>
* Application notes available for multiple appliance categories
* Legal recommendation, not legal advice
* Recommendation:
  * Give the design to another team not involved in development
  * Or use a third party for the risk assessment
* Technology-agnostic approach:
  * CRA sets security principles without specifying how to implement them

### CRA ECRs Cover

* Product configuration
* Product authentication
* Access to product
* Data protection
* Product monitoring and cyber-state awareness
* Vulnerability fixing and product updates
* Reduction of incident impact and product availability

### CRA Does Not Specify

* Level of security
* Required protection level
* Cryptographic algorithms
* Protocols
* PKI
* X.509 certificate formats
* Technology implementations
* Specific security hardware or software

* No requirement explicitly states that security must be implemented in hardware
* NXP recommends hardware-backed security
* Secure Enclave as a newer feature, sometimes combined with TrustZone

---

# Dr. Piet — Product Security Guru

* Encourages companies to perform their own risk assessments
* One-person company specializing in CRA and RED
* Linux Foundation survey:
  * 68% of organizations are unaware of the CRA
  * Last year: 66%
* Many organizations still have significant work ahead to become CRA-compliant
* Maturity needed:
  * Learn to build secure devices

### Myth: The CRA Legal Text Gives Clear Requirements

* It does not
* Essential requirements become specific through standards
* One sentence can expand into a 100-page standard

Example:

* "Software may not harm kittens"
* Standard:
  * "Where lasers are used to create a product, optical power shall not exceed 1 mW"

* CRA assessment procedures:
  * TODO: add photo

### Establish Product Context

* Home or factory?
* Risk acceptance criteria
* Asset identification
* Threat identification
* Risk assessment
* Security requirements
* Secure design
* Secure implementation
* Testing and validation
* Risk monitoring and review

* As manufacturer, you are responsible for the whole product:
  * Your own software
  * Components
  * Libraries
  * Dependencies

---

# Burkhard Stubert — From Threat Modeling to Risk Assessment

* A threat is a violation of an essential product property

### Example

* Access control
  * Threat:
    * Unauthorized access
  * Security measure:
    * Authentication
    * Identity management
    * Access management
    * Reporting

### Adam Shostack's Four-Question Framework

1. What are we working on?
2. What can go wrong?
3. What are we going to do about it?
4. Did we do a good job?

* Mitigate supplier risk by asking suppliers about their assessments
* Use Security Decision Records (SDRs)
  * Markdown files
  * Stored in Git repositories
* Add user stories to SDR context
* Slides available on website
* Brainstorm mitigation efforts for violations

### Security-Critical Functionality on Demand

* Limits attack windows
* Requires physical access
* Requires intentional activation

* Mitigations should only improve security, never worsen it
* Validate risk assessments after important updates
* Personal opinion:
  * CRA stands for continuous risk assessment

---

# Build Versus Buy Under the CRA — Jon Oster

* The toaster project:
  * Build everything from scratch
* Overbuilding has failure modes
* Buying also has failure modes

### Rules of Thumb

* Open is better than closed
* Standards-based is better than custom
* A system you fully understand is better than a black box
* For open source:
  * Paid maintainers are better than hobby projects
* OSS projects dominated by a single company can be risky

* It cost a meaningful amount of development time
* Don't roll your own crypto (Bruce Schneier)

### What Is a Software Update System?

It consists of four elements:

1. Repository for updates and metadata
2. Update agent
3. One or more installation backends
4. Protocol connecting all elements

* New ENISA technical advisory on secure update mechanisms

### Vulnerability Handling

* Use standard VEX formats:
  * CycloneDX VEX
  * OpenVEX
* Goal:
  * Reduce false positives
  * Avoid missing real issues

### Vulnerability Funnel

* ~500k CVEs
* ~2k apply to your SBOM
* VEX reduces this to ~50
* Threat modeling reduces this to ~10
* Remediate those

### Tools Mentioned

* Torizon Vulnerability Manager
* Ariana (Security Pattern)
* vulnscout.io
* Dependency-Track
* OneKey
* GUAC

---

# CRA Summit — Key Facts

## Biggest Insights

* **You own the entire product**, including open-source components, libraries, suppliers, and dependencies
* **Security is now a lifecycle responsibility**
* **CRA is a risk-management framework**, not a checklist
* **Support becomes a product feature**
* **The real challenge is operations**
  * SBOMs
  * Vulnerability management
  * OTA updates
  * Monitoring
  * Incident response

## Biggest Risks for Embedded Companies

* No SBOM / software inventory
* No vulnerability management process
* No secure update mechanism
* Unknown risks in third-party software
* Treating CRA as a legal instead of an engineering problem

## What To Do

1. Build SBOM and dependency visibility
2. Establish threat modeling and risk assessments
3. Create a secure OTA/update strategy
4. Implement vulnerability and incident management
5. Document security decisions and keep them under version control

## My Takeaway

The competitive advantage is no longer **building devices**.

It is **maintaining secure devices for years after shipment**.

---

## Open Question

* Challenge:
  * SBOM generation for C++ products
* cdxgen works, but reports too many dependencies in some STM32 projects
* Requires manual curation
* Question:
  * Does this become a source of failure because it is not fully automatable?
