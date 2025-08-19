---
{"dg-publish":true,"permalink":"/cvss-metrics/"}
---

The Common Vulnerability Scoring System (CVSS) is a standardized framework used to assess the severity of software vulnerabilities. It helps organizations prioritize remediation efforts by providing a numerical score that reflects the intrinsic characteristics of a vulnerability. CVSS is composed of four metric groups:

  
- [NVD - Vulnerability Metrics](https://nvd.nist.gov/vuln-metrics/cvss)
- [CVSS Version 4.0: What's New](https://sysdig.com/blog/cvss-version-4-0-whats-new/?utm_source=chatgpt.com)
## **Base Metrics** / Impact Metrics

The **intrinsic qualities** of a vulnerability 

- Exploitability Metrics 
    - Attack Vector (AV): 
	    - network
		- adjacent network
		- local
		- physical
    - Attack Complexity (AC):
		- The conditions beyond the attacker’s control that must exist to exploit the vulnerability (e.g., low or high).
    - Privileges Required (PR): The level of privileges an attacker must possess (e.g., none, low, high).
    - User Interaction (UI): Whether user interaction is required for exploitation (e.g., none, required).
- Impact Metrics: The consequences of a successful exploit on the [[Confidentiality\|Confidentiality]], [[Integrity\|Integrity]], and [[Availability\|Availability]] ([[CIA triad\|CIA triad]]) of the affected system. This includes:
    - Confidentiality Impact (C): The impact on the confidentiality of information (e.g., none, low, high).
    - Integrity Impact (I): The impact on the integrity of information (e.g., none, low, high).
    - Availability Impact (A): The impact on the availability of the system (e.g., none, low, high).
        

## Threat Metrics

These metrics reflect the characteristics of a **vulnerability** that change over time. They include:

- Exploit Maturity (E): The current state of exploit techniques or code availability (e.g., unproven, proof-of-concept, functional, high).
- Remediation Level (RL): The availability of a fix or mitigation (e.g., official fix, temporary fix, workaround, unavailable).
- Report Confidence (RC): The level of confidence in the existence of the vulnerability and the credibility of the technical details (e.g., unconfirmed, uncorroborated, confirmed).
    
## Environmental Metrics

These metrics represent the characteristics of a vulnerability that are unique to a **user’s environment**. They include:

- Collateral Damage Potential (CDP): The potential impact on physical assets or financial loss if the vulnerability is exploited (e.g., none, low, medium-high, high).
- Target Distribution (TD): The proportion of vulnerable systems in the environment (e.g., none, low, medium, high).
- Security Requirements (CR, IR, AR): The importance of [[Confidentiality\|confidentiality]], [[Integrity\|integrity]], and [[Availability\|availability]] to the organization (e.g., low, medium, high).

## Supplemental Metrics

- Automatable (AU)
  - Indicates whether an attacker can automate the exploitation of the vulnerability across multiple targets.
  - A higher value suggests that the vulnerability is more easily exploited at scale.
  
- Safety (S)
  - Assesses the potential for human harm resulting from the exploitation of the vulnerability.
  - A higher value indicates a greater risk to human safety.
  
- Recovery (R)
  - Evaluates how quickly and effectively a system can recover after an attack exploiting the vulnerability.
  - A lower value suggests longer recovery times and greater impact.
  
- Value Density (VD)
  - Measures the concentration of valuable assets within the affected system.
  - A higher value indicates that the system contains more critical assets.
  
- Vulnerability Response Effort (VRE)
  - Estimates the effort required to respond to the vulnerability, including mitigation and remediation.
  - A higher value suggests more resources are needed to address the vulnerability.
  
- Provider Urgency (PU)
  - Reflects the urgency assigned by the vendor or provider regarding the vulnerability.
  - A higher value indicates that the provider considers the vulnerability more critical.