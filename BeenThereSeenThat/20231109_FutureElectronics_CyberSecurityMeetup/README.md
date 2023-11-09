# 20231109 Future Electronics - Cybersecurity Meeting
* Frank Moelendorp invited; Markus Kirschner is the director senior sales Bavaria
* 10 visitors, three speakers already lined up; more people joined later - so 15 visitors?

* cybersecurity comes to Europe, no matter if we want it or not

## Nicolas Guilbaud (Future Electronics) - Regulation and Securing Connected Product
* cybersecurity is not functional safety - just defending system against attacks
* why take care of CS in product design?
* do you need CS?
* if your product is connected, you need it - yes
* if your product is upgradable, then yes
* does your product store private data: then yes (GDPR) - name, passwords, SSID for network...
* security regulatory rules apply to your product: yes
* privacy age: GDPR, Cyber Act (EU), 2021 Biden Executive Order on Cybersecurity, UN cyber for cars (R155)
* 2021 already 1.5 Bn attacks on devices
* the threat could come from anywhere and reach anywhere
* attacks can happen from all systems
* CS has some standards depending on product
  * medical: IEC 62304, 81001-5-1, and 60601-4-5
  * road vehicles: ISO 21434 - also for development process
  * industrial: IEC 62443
  * ETSI 303645 is the basis of new CE certification
* getting a certain product certified for multi-market can be challenging, due to the different standards
* in Europe: do cybersecurity by design
* new RED CE marking: regulation in 2024 <-- check: 2025?
* as well as CRA: European Cyber Resilience Act
* CE certification - RED
  * covers: internet-connected radio equipment, worn or strapped on any part of the body, or anything used to transfer money, monetary value, or virtual currency; except medical devices
* CRA: objectives
 * improve security of products throughout the whole lifecycle; up to 5 years after selling the product you have to support it
 * ensure coherent cybersecurity framework; facilitating compliance for hardware and software products; also see the work of the Linux Foundation
 * enhance transparency of security properties: you will have to do an SBOM: list all dependencies on your product, where they are coming from
 * enable business and consumers to use products with digital elements securely
 * financial sanction if a company does not apply those regulations: up to 2.5% of the WW annual turnover
 * will gain traction in 2026 <-- check: 2026?, but due to the pipeline, it will take some time to implement
 * will be in practice: 90% of the products are self-assessment, 10% will be Class 1 or 2; standard or third-party assessment; cloud SaaS are out of scope (covered by another act); just for hard- and software
 * TODO: check: German guide for SBOM for CRA
 * personal data is any data which can be linked to your person, directly or via a database (therefore SSID - big databases)

### CS Simplified Flow
* Start with risk assessment; else overengineering (too much cost, then not competitive anymore)
* Access level on physical level matters (satellite vs. login-terminal)
* Next: design and implementation
* Test & certification
* Manufacturing
* Maintenance (patch rolled out with new firmware)

* There will be a standard to select chipset:
 * Security standard used for electronic components
 * NIST FIPS 140-2 and 3; NIST security level for crypto module
 * Or Common Criteria: EAL1 to 7;
 * For microcontrollers: SESIP 1 to 5; focus to industrial and IoT market
 * There is also an ARM related initiative: PSA-certified: level 1 to 3; covers hardware, but also some software
 * SESIP, PSA-certified and Common Criteria, share some similarities; it is easy to reach the other two
 * MPU/MCU area covers most of the time level 1 to 4, TPM starts with level 4 to 7; government attack level
 * ETSI 303 645 is quite broad: has some quick solutions for challenges
  * Like: no default passwords; quality processes and customer relationship processes; firmware update and secure boot; secure storage; use certified cipher suite on network protocols; debug interface disabling; usage for HW protection, secure boot, secure storage; power tree with backup, examine system telemetry data: mainly SW, log analysis; make installation and maintenance of the devices easy; validate input data
  * Secure boot: good protection against malware and SW counterfeiting
  * Optional encryption of the SW: mandatory if the binary is on a public network; should be encrypted to prevent some reverse engineering
  * Authentication and integrity of the SW running in the CPU
* Secure boot: ROM bootloader starts and verify; flash bootloader: does decrypt & verify application SW select partition, jump to application -> selects start of either first or second partition (A: version N; B: version N-1)
* Cryptography:
  * For confidentiality: problem with symmetric key, because shared and getting them on customer device compromises the cloud as well
  * For authentication: public key algorithms (PKA)
  * For integrity: hash algorithms
* How to store secrets: don't put it on external flash; quite easy to extract there
* Use internal flash on the MCU - good against low-level attacks
* Or: internal flash with internal barrier
* Good: internal HW secure block + TrustZone; external secure element; -> low level of physical attacks and high level of SW attacks
* How does this affect logistics (external flashing of the boards)?
* Best: TPM: high level of physical attacks (needs bigger software stack)
[Cut short in some topics because 5 min over time]

## Guido Bertoni from Security Pattern S.r.l.
* Penetration testing
* Even if you achieve T0 certification, two years later hackers may be able to gain access
* Therefore, cover the entire lifecycle of the product
* A significant challenge is that customers expect their devices to last 10-15 years
* Worked for STM for 14 years; was part of the SHA-3 algorithm development team
* ISO 27001 certified; partners with Microchip and NXP
* Partner for the ORCHID project (EU): Involving KU Leuven, Technikon, Tropic Square, Texplained, EURECOM, NXP
* Also involved in the QUBIc project: Focused on post-quantum cryptography
* Offers consultancy, development, training, services, and solutions
* Overarching structure includes development teams for cloud, applications, gateways, and IoT/industrial/medical devices
* To examine: Secure Development Lifecycle (SDLC)
* Process: Requirements -> Design and Implementation -> Verification -> Operations and Maintenance
  * Requirements: Threat modeling; security requirements; consider using "STRIDE" (to be checked); or adhere to ETSI standards and "just write a couple of pages"
  * Design: Security architecture; secure coding guidelines
  * Verification: Requirements-driven testing; vulnerability testing, penetration testing (by an individual not privy to internal details; ethical hacker; occasionally as an 'open book' exercise)
  * Operations: Vulnerability management; deploy firmware/software updates; security operations (ensure that users do not misuse features; prevent the creation of open networks when WPA2 is available)
* Governance: Strategy and metrics, policy, and compliance
* Implementing all these aspects requires a higher budget

### SECURITY IS A PROCESS - or: SECURITY IS A COST?
* Insecurity is an even bigger cost, because if you go faster to market, you have to pay the cost later (by mitigating or recalling even the device)
* Responsible: Device manufacturer is obligated to maintain their product secure
  * Required worldwide by different standards
* Vulnerability handling requirements: else the market surveillance authorities have the power to sanction your company
  * If the device is not secure, they can force you to withdraw the product from the market and apply fines: 15 million € or 2.5% of annual worldwide revenue
* Security is an investment
  * Customers care about it because they see a risk or have experienced a CS problem in the past
  * Risk; vulnerability, threat - three different terms
* Risk management process:
  * 1. Model your system and define your risk tolerance level
  * Enumerate threats to your system (threat modeling)
  * Assess threats: Quantify and rank risks
  * Respond to risks: Mitigate the outcome; remove the vulnerability
* Memory-safe implementation; languages
* Example: Test if the device does not accept tampered SW for update, etc.
* Example: Try to use the certificate on another device; try to assess their share of the cloud - should also fail
* See: CVE program: International, community-driven effort to catalog vulnerabilities; launched in 1999
  * CVE-ID: Program receives funding from US NCSD, maintained by MITRE
  * Is used to track known vulnerabilities; has short description, severity, etc.
* Also CWE: Common Weakness Enumeration
  * Based on one or more weaknesses
  * Weaknesses are flaws, faults, bugs in software and hardware implementation..
  * Found flaws require to evaluate the whole workflow
* The layers composing a device: Device model or CBOM = SBOM + HBOM
  * Up to 98% of SBOM is from 3rd parties
  * Vulnerabilities could be everywhere and most likely in the 98% from 3rd parties
* Their company offers a service to handle the SBOM
* Yocto Linux of 6 months ago: more than 400 vulnerabilities
* Help with the prioritization: but minimality is key: the more dependencies you have, the more problems you will have
* Device security improvements in a simple graph: Show a graph, to customers and during assessment; or assess the vulns. with risk assessment and say this does not affect the device
* Create a policy to fix vulnerabilities and inform the customer within X days: this is then our policy; customer should agree to this
* Penetration testing: The depth of the penetration test should be related to the threat model
* Some tests might be more or less relevant depending on the use cases
* External connectivity: Try to impersonate the cloud; try to probe physical ports; try to interact with wireless connectivity
* Board level: Try to use debug ports, try to read flash content, try to probe chip-to-chip connections
* Attack: Remove packaging from chip, then use microprobes
* Secure element die: Active shields; 60 cents
* Probing: Fault injection
  * Run the device outside of its operating conditions, glitch in power supply at the proper time; laser shot to specific portions of the integrated circuit
* Their offer: A product called SUM as a platform, which gives a notification for new vulnerabilities affecting the known devices; Is there also a patch? Continuous monitoring over the whole lifecycle of the IoT device; Automated system
  * They ask for a compilation of files; accurate device model, including SBOM; using a questionnaire, compilation files, and our support - TODO discuss this with Stefan and Alex

## Infineon: CSS - Connected and Secure Systems
* Their products are used in security systems, cars, computers, wearables, passports
* Vault for most valuable stuff
* 127 IoT devices are installed per second
* Security is essential in a connected world
* There is a need for a trusted environment to build trust
* Slogan: Digitalisation and decarbonisation
* Infineon strong in smart cards, biometric cards; also for embedded systems: PCB layouts for smart watches or SBCs; also platform security
* Customer-specific authentication; application-specific authentication <-- check: "aolication" should be "application"
* Also: Edge ID, Enterprise ID, Government ID
* Goal: Prevent that somebody hacks your devices with $500 of equipment
* Also USB solutions nowadays <-- check: "UBW" should be "USB"
* They shape the market: market leader in security; 3 billion ICs/a sold

### Trends on Cybersecurity Prevention - Detlef Houdeau
* ISO 24089 - Road Vehicle Software Update Management System - have a look
* IIoT market and stakeholders: Industrie 4.0, Robot Revolution (Japan), Industrial Internet (USA), Made in China 2025 (China)
* 6500 companies as machine producers in Germany; 80k companies in Europe: small to medium enterprises; headcount less than 250
* Change in architecture: zero trust; Zero Trust Network Architecture, Digital Twin, and Digital Product Passport (for CE products)
* Home network is not a secure environment
* CIA: Confidentiality, Integrity, Availability
* No harmonization in the market: each vertical pillar has its own set of regulations
* Germany 20 million residential buildings, 40 million households; diverse market; no reference architecture
* Price, feature list will be completed by carbon footprint
* IoT Security Label: status 11/2023: Singapore label; Level 1 baseline security; Level 2 adherence to international standards; Level 3 adherence to principles of security by design; Level 4 resistance against common cyber attacks
  * Levels 1 and 2 can be self-declared; Levels 3 and 4 need help by TÜV, UL, etc.
  * Migration from IoT to IoTT (Internet of Thinking Things) - more intelligence inside
  * Smartphones will be certified in the future
* Security by design is defined!
* IT security for AI, IT security with AI (defense tool - class); IT security against AI; there is an asymmetry between defender and attacker; defender can use an Intrusion Detection System (IDS) (from market), but the attacker has the same opportunity and can analyze the IDS and circumvent it
  * See GAN - Generative Adversarial Networks
  * Maybe honeypots will work beside firewalls and intrusion detection systems in the future, but it's an ongoing game

### SEMPER Secure - Marcel Gluebert
* FA engineer at Infineon for automotive
* Currently, more MCUs come without much own flash; not integrated anymore but external
* Low total cost of ownership; ISO26262, ASIL-B, ASPICE Level 2 compliant, fast time to market <-- check: Level 2
* Potential security threats:
  * Modify or replace boot-loader/application code
  * Delete flash contents
  * Steal IP by reading program memory
  * Steal user data or other assets from storage
  * Monitor, intercept, or replay messages on the system bus
  * Steal keys on host and/or flash
* All happens by the external flash which has an integrated Cortex M0 processor
* Public versus private market; European Commission is just checking the public market <-- check: just

## Security at Microchip - Reiner Ziegler
* FAE-Engineer, Sales representation
* Microchip as a broadliner; many companies acquired, business volume 4 billion, 1 billion of that in the DACH region alone; 22k employees
* Security is not just a single component, but really something that requires systems thinking
* Simplifying security from consumables (stand-alone) to cloud to enterprise
* Components also designed so that when cutting one off, the first paths of the conductor are removed, so it does not work anymore
* Full product lifecycle: from concept, development, production, utilization, support (live update) to retirement (scramble and irretrievably delete everything)
* Threat modeling: developing hack-resilient systems
  * Define system requirements
  * Legislation requirements
  * Risk analysis
* From standards to use cases:
  * Unique ID; monotonic counters; ...
* Common Criteria JIL rating (Joint Interpretation Library)
  * JIL rating can be converted to EAL; if not hackable by experts for 6 weeks, then JIL 31 as the highest value
* Trust Platform Design Suite: guide the customer (for developers, so they don't forget to implement security as a feature)
* Fitted for mass market with low MOQ including provisioning and Microchip certificates
* Architecture agnostic with any cloud, any PKI, any controller

## Renesas - [TODO: Add Title]
* Security requires a solid foundation
* "Solid security cannot be added later"
* Initially, a developer creates a prototype in a known and controlled environment; later, it transitions to mass production in a product within an unknown, uncontrolled environment
* Wrapping versus encrypting: Take data, encrypt it, producing encrypted data; it can be decrypted with the key to retrieve the original data; however, if a corrupted key is used, the result is garbage data
* Wrapping at Renesas: An extra fixture to check the integrity of the data
* Each MCU from Renesas has a unique key

## Lattice Semiconductors
* Dr. Hardik Shah & Dr. Baris Konuk
* Altera, Xilinx, and Lattice are all quite old companies: now only existing as Intel, AMD, and Lattice; but Lattice sells the most
* Focus on smallest size and also low power, security from the ground up
* 14 continuous quarters of growth
* Cybersecurity failure costs millions to OEMs
* Yesterday's security paradigm: centralized computing citadel
* Huge security problem in an automotive system
* Quantum algorithms and computers will break many of the current cryptography algorithms, like AES256, ECC, RSA, ECDH, ECDSA
* A decade seems like a long time, but many devices built today will be in the field for much longer than 10 years
* "Steal now, decrypt later" strategy
* NIST has already made a choice for PQC (Post-Quantum Cryptography) algorithms
* Root of trust should always be the first one to wake up
* Secure boot as part of the CIA triad - CIA as the acronym for Confidentiality, Integrity, Availability, not the agency

## Summary
* Change of mindset
* Security is not just an add-on
* Maintenance during the lifetime is a new aspect
