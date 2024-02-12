# Azure Honeynet & SOC: Cyber Attacks in Real-Time

## Introduction

In this project, I create a live honeynet to lure attackers into our environment. To accomplish this, vulnerable virtual machines lacking safeguards in Azure were set up and deployed to the public internet. To be able to collect and query logs from different sources Log Analytics Workspace was set up, while Microsoft Sentinel is leveraged to generate attack maps, alerts, and incidents. Microsoft Sentinel measured the metrics of an insecure environment for 24 hours. Following this phase, security controls were implemented to fortify the virtual environment, and another 24-hour metric measurement was conducted. The objective of this project is to illustrate the importance of security controls (NIST 800-53), effective incident response strategies by using NIST 800-61, and how to investigate/analyze event alerts while also trying to understand the attacker's tactics, techniques, and procedures. 

## Architecture Before Hardening / Security Controls 


## Architecture After Hardening / Security Controls
