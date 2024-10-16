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
* CRA and RED - cyber resilience act and radio equipment directive
* today as well: on-device AI
* most people used BXP products, some toradex, but good blend of software and hardware engineers
* Toradex from Lucerne, Switzerland
* embedded systems on modules
* focus on 5 pillars: healthcare, industrila&robotcs, transportation&logistics, energy&reneweables (charging stations), smart city
* annual volume: 500 to 100k pcs per project/customer
* more than 25 i.MX based products
* moving into SMARC (modules)
* torizon: torizon OS, visual studio integration, software ecosystem(docker); remote updates, device monitoring, torizonCore builder
* fleet services: fleet monitoring, fleet management, offline updates, remote access, extendable

## Introduction to i.MX 95 family
* newest SoC with highest omputational power, compared to imx8mplus
* designed for secure connected edge markets
* NPU accelerator, immersive graphics by ARM Mali GPU
* high performance data throughput and expansion: 10 Gbps ethernet
* powerful application domain: 6 ARM cores, A55
* dedicated realtime domain: arm corex-m7 cpu
* ultrawide capability: 3840x1440P60
* edgelock secure enclave; up to 8 cameras with 2x MIPI-CSI 4 lane interface with virtual channels
* i.MX959 is the superset: have all the capabilites, all other versions are downsampled based on specific use-cases
* EVK are available for early supporters
  * i.MX95 Verdin EVK is available: by default with DSI2HDMI-adapter
  * what is OctalSPI Fash for fast boot? -> `OctalSPI (Octal Serial Peripheral Interface) is an advanced version of the SPI communication protocol that enhances data transfer rates by utilizing eight parallel data lines.`
  * offers Boot2Qt-image for quick start; but also docker containers from Qt
  * pricing starts at 699€

## Vision IP highlights
* comparison of imx8.mplus and i.mx95
* more output, higher quality, more OS agnostic, higher resolutions
* direct integration via V4L
* eIQ Neutron .. 2 tOPS dense, 7 TOPS sparse
* NPU was developed in house
* TODO add image of benchmark chart
* edge ai workload acceleration for facial recognition, access control, classification, preditctive maintenance, pose detection, traffic monitoring, voice-to-intent
* support for TFLite, PyTorch, Caffee2, ONNX
*
