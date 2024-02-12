# Azure Honeynet & SOC: Cyber Attacks in Real-Time

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/5f1e5174-b99e-40ef-9cae-e6cae8ebeae7.png">


## Introduction and Objective 

In this project, I create a live honeynet to lure attackers into our environment. To accomplish this, vulnerable virtual machines lacking safeguards in Azure were set up and deployed to the public internet. To be able to collect and query logs from different sources Log Analytics Workspace was set up, while Microsoft Sentinel is leveraged to generate attack maps, alerts, and incidents. Microsoft Sentinel measured the metrics of an insecure environment for 24 hours. Following this phase, security controls were implemented to fortify the virtual environment, and another 24-hour metric measurement was conducted. The objective of this project is to illustrate the importance of security controls (NIST 800-53), effective incident response strategies by using NIST 800-61, and how to investigate/analyze event alerts while also trying to understand the attacker's tactics, techniques, and procedures. 

## Technologies, Regulations, and Azure components Employed 
* Azure Virtual Network (VNet)
* Azure Network Security Groups (NSG)
* Virtual Machines (2x Windows, 1x Linux)
* Log Analytics Workspace with Kusto Query Language (KQL) Queries
* Azure Key Vault for Secure Secrets Management
* Azure Storage Account for Data Storage
* Microsoft Sentinel for Security Information and Event Management (SIEM)
* Microsoft Defender for cloud to protect cloud resources
* Windows Remote Desktop for Remote Access
* Secure Shell for Remote Access 
* Command line Interface (CLI) for System Management
* [NIST SP 800-53 Revision 5 For Security Controls](https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home)
* [NIST SP 800-61 Revision 2 for Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

## Architecture Before Hardening / Security Controls 

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e5c4589e-3f05-4171-b20e-be21a58e94bb.png">


Before hardening Measures and Security Controls:
* In this stage our Linux and Windows machine's NSG's were left wide open 



---


## Architecture After Hardening / Security Controls

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e7cb31c1-15e1-4ebd-a9e7-b26a7d8f5998.png">



