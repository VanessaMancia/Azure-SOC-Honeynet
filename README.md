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

## Architecture Before Hardening and Implementing Security Controls 

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e5c4589e-3f05-4171-b20e-be21a58e94bb.png">

In the "BEFORE" stage, all resources were initially deployed with public exposure to the internet as a way to lure attackers. The Linux and Windows machine, which hosted an SQL database both had their Network Security Groups (NSGs) and built-in firewalls wide open, allowing unrestricted access from any source. The storage account and the key vault were deployed with public endpoints visible to the internet. In this stage, the unsecured environment was monitored by Sentinel using logs aggregated by the Log Analytics Workspace. 

---


## Architecture After Hardening and implementing Security Controls

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e7cb31c1-15e1-4ebd-a9e7-b26a7d8f5998.png">
 
In the "AFTER" stage the main goal was hardening and implementing security controls to satisfy NIST SP 800-53 Rev4 SC-7(3) to improve the environment's overall security posture. The hardening tactics included: 

* Network Security Groups (NSGs): I hardened the NSGs by blocking all inbound and outbound traffic, with the exeption being my own public IP address. This ensured that only authorized traffic was coming into the virtual machine.
* Private Endpoints: To enhance the security of Azure Key Vault and storage containers, public endpoints were replaced with private endpoints. This ensured that both the Azure key Vault and the storage could be accessed privately within the virtual network and subnet only.

* 

