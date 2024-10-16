# 20241016 Security Tech Afternoon - Toradex & NXP

* to check:
  * OPCUA
  * lightweightM2M (for sensors)


## Agenda
```
Agenda
1:30 – 2:00 pm
Registration
2:00 – 4:00 pm
Keynote Address and Technical Insights
	Industry Trends: Security Regulations, AI, Vision, Safety, and more
	Real-World Use Cases: Practical Applications across Multiple Sectors
	Introduction to the New i.MX 95 SoC: Features, Capabilities, and Innovations
	How to Join the i.MX 95 Beta Program
	Scaling from Prototype to Volume Production: Minimizing Risk and Cost
	Exclusive Insights into the Product Roadmap
4:00 - 5:30 pm

Track 01
Coffee with Experts

Enjoy the unique opportunity to engage with our specialists in a relaxed setting.

Discuss your questions and projects directly with NXP and Toradex experts.

Track 02
Technical Deep Dive
	i.MX 95 Secure Enclave, Secure Boot, and Software Enablement
	i.MX 95 AI and Computer Vision Pipeline
5:30 pm onward
Networking Happy Hour
	Talk to our Experts and Industry Peers
	Discover interesting demos from NXP, Toradex, and partners
```

## Intro
* why? Cyber resilience act: adopted by E. council last week
* has to be adopted for existing and new devices
* different regulations in different regions
* legally complex, but shared similarities in technical aspects
* CRA and RED - Cyber Resilience Act and Radio Equipment Directive
* today as well: on-device AI
* most people used NXP products, some Toradex, but good blend of software and hardware engineers
* Toradex from Lucerne, Switzerland
* embedded systems on modules
* focus on 5 pillars: healthcare, industrial & robotics, transportation & logistics, energy & renewables (charging stations), smart city
* annual volume: 500 to 100k pcs per project/customer
* more than 25 i.MX-based products
* moving into SMARC (modules)
* Torizon: Torizon OS, Visual Studio integration, software ecosystem (Docker); remote updates, device monitoring, TorizonCore builder
* fleet services: fleet monitoring, fleet management, offline updates, remote access, extendable

## Introduction to i.MX 95 family
* newest SoC with highest computational power, compared to i.MX 8M Plus
* designed for secure connected edge markets
* NPU accelerator, immersive graphics by ARM Mali GPU
* high-performance data throughput and expansion: 10 Gbps Ethernet
* powerful application domain: 6 ARM cores, A55
* dedicated real-time domain: ARM Cortex-M7 CPU
* ultra-wide capability: 3840x1440P60
* EdgeLock secure enclave; up to 8 cameras with 2x MIPI-CSI 4 lane interface with virtual channels
* i.MX 959 is the superset: has all the capabilities, all other versions are downscaled based on specific use-cases
* EVKs are available for early supporters
  * i.MX 95 Verdin EVK is available: by default with DSI-to-HDMI adapter
  * what is OctalSPI Flash for fast boot? -> `OctalSPI (Octal Serial Peripheral Interface) is an advanced version of the SPI communication protocol that enhances data transfer rates by utilizing eight parallel data lines.`
  * offers Boot2Qt image for quick start; but also Docker containers from Qt
  * pricing starts at 699€

## Vision IP highlights
* comparison of i.MX 8M Plus and i.MX 95
* more output, higher quality, more OS agnostic, higher resolutions
* direct integration via V4L
* eIQ Neutron .. 2 TOPS dense, 7 TOPS sparse
* NPU was developed in-house
* TODO add image of benchmark chart
* edge AI workload acceleration for facial recognition, access control, classification, predictive maintenance, pose detection, traffic monitoring, voice-to-intent
* support for TFLite, PyTorch, Caffe2, ONNX
* question about the Qt SafeRender: TODO check this https://doc.qt.io/QtSafeRenderer/

## EU Cyber Resilience Act
* global annual cost of cybercrime: 5.5 trillion € - equal to spending 1 million € per day for the next 15k years
* do botnets with coffee machines
* why now?
  * motivation on device manufacturer side was too low; there was no forcing legal framework
  * customers do not understand the security of devices
* goals of CRA are: framework for cybersecurity requirements; products are designed, developed, and produced with cybersecurity in mind; transparency in handling cybersecurity risks and incidents
* 90% of products: are in the default category, self-assessment
* 10% of products: critical class I: either standard or third-party assessment, critical class II: third-party assessment
* why should you comply? because the fines are huge
* requirements simplified:
  * free security patches for 5 years or the lifetime of the product
  * protect the device, security by default, secure boot
  * no known exploitable vulnerabilities
  * protect customer data at rest and in transit
  * automatic security updates that are enabled as default setting(!)
  * limit attack surfaces, including external interfaces
  * document software used: provide an SBOM
  for vulnerabilities, early warning in 24h, full notification in 72h
  * address vulnerabilities and patch with no delay (no time mentioned)
  * provide a secure update mechanism
* discussion of GDPR implications in B2C relations
* how to provide the vulnerabilities, which were discovered
* patching independent of vulnerability
* if you are using the downstream kernel, do you have to report those CVEs on your product as well? not answerable
* check, who handles this: open source software "steward"?
* by default you don't have to provide the SBOM to customer; so they can't know which things are affected by vulnerabilities
* Torizon offers help with SBOM, risk management, secure-by-default, vulnerability monitoring, updates

## NXP EdgeLock secure enclave
* own CPU core and ROM; isolated from the rest of the SoC
* provides enhanced isolation for execution

## Transformation
* TODO add the photo here
* be faster, be secure, be reliable
* TorizonCloud: OTA, remote access & control (console!); fleet management, ..
* example: Splunk video - did not work; uses full stack from Toradex; hardware, TorizonOS, own HMI framework
* traditional or bare-metal Debian deployments: no zero-conf, no monitoring, remote access, OTA -> customers end up with messy fleets
* demo gallery: CodeSys Demo, Crank GUI, Slint UI, ROS - check the first ones
* application containerization (Dockerization): OTA services, container runtime, Linux kernel as base: on top the applications
  * needs a bit more memory, and a bit more boot time
  * but running the app directly is also possible

## QNX: secure RTOS for next Toradex project
* Thomas de Lellis
* QNX is part of the BlackBerry IoT pillar
* customers: automotive, industrial automation, medical devices, defense, heavy machinery, energy, rail ..
* QNX is Unix-like, but not built on top of Linux; is a microkernel
* every software component is isolated as a process: drivers, stacks, OS services, applications
* can restart any component individually, without interrupting the kernel
* all processes can use the same APIs: POSIX PSE54 and C11, C++14/17/20 - greatly simplifies embedded development
* hypervisor host domain: microkernel with scheduler
* separation of mixed criticality components can facilitate certification efforts
  * failure in non-safety-critical components does not create failure in safety-critical components

* talked with Burkhard Stubert a bit about licensing

## Breakout session with advanced security
* EdgeLock secure enclave as root of trust in the system
* hosts secrets and platform integrity credentials
* post-quantum cryptography: Dilithium 3.1 signature verification
* clock frequency monitor, glitch detector
* secure debug enforcement: challegene-reponse based authentication for enablement in the field

