# 20260628 - Medical Equipment by Design: Building Secure, Safe and High‑Performance Systems with NXP's i.MX 9 Series Applications Processors and QNX
* webinar; not sure if live or canned ..

```
Hospital medical equipment is expected to deliver continuous uptime, deterministic performance, and uncompromising safety and security—all while meeting strict regulatory requirements. Achieving this level of reliability starts with the right system architecture.

In this joint webinar, NXP and QNX will show how i.MX 9 application processors combined with the QNX OS enable medical device platforms that are secure by design, scalable, and ready for certification. Using real world medical use cases, we’ll explore how architectural choices at the hardware and OS level translate into reliable, compliant products in clinical and laboratory environments.

What You Will Learn

    Design approaches for medical device platforms that deliver reliable performance, continuous uptime, and strong safety and security
    How multi core SoCs support real time control and high-performance data processing
    How microkernel based RTOS provides determinism, fault isolation, and reliability for medical systems
    How architectural design choices can simplify and accelerate functional safety and regulatory compliance in medical devices
```

* speakers: Daniel Lodu QNX, Sara Monteiro NXP, Rohitaswa Bhattacharya NXP
```
Daniel Lodu
Senior Product Marketing Manager, QNX
1776803979-bb61221622988c05
Sara Monteiro
Global System Marketing Manager - Healthcare Applications, NXP
1778184277-622d6d985c6a22fe
Rohitaswa Bhattacharya
Technical Director, Systems Architecture, NXP Semiconductors
1748363541-acd43608b2971696
Ken Briodagh
Editor in Chief Embedded Computing Design
```

* QNX is a division of Blackberry; worldwide, several locations; 45 years; failure is not an option (high-performance, reliable operating systems)
* NXP: 33k employees; also silicon for hearing aids

## Talk
* regulatory compliance is not just a requirement - it is a strategic enabler for safety and market access
* FDA database gets over 2 million medical device reports annually - failures, issues, whatever
* ongoing vigilance needed by device manufacturers and their suppliers
* trends in the medical device market: complexity and connectivity; scrutiny of software; regulatory focus; safety and security approach; cybersecurity
* path to regulatory approval: IEC 62304 software lifecycle; risk management; quality management ISO 13485; product safety IEC 60601

* expanded regulatory expectations
  * requires an SBOM for transparency
  * expect ongoing vulnerability management and patching
  * place full cybersecurity responsibility on the manufacturer
* increased risk surface
  * increasing software complexity expands the attack surface
  * connectivity exposes devices to remote threats
  * vulnerabilities can impact safety-critical functions
* device manufacturer challenges
  * no single dominant standard

* aspects: culture, standards, assessment, expertise, protection, architecture, monitoring, lifecycle
* safety and security as a system design and user responsibility
* safe medical application - concept mapping
