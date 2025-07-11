# 🛡️ Azure Honeynet & SOC: Cyber Attacks in Real-Time

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/5f1e5174-b99e-40ef-9cae-e6cae8ebeae7.png" alt="Azure SOC Banner"/>

## 📌 Introduction & Objective

In this project, I created a live honeynet to lure attackers into a vulnerable Azure environment. This involved deploying unsecured virtual machines to the public internet. To collect and analyze telemetry, I configured a **Log Analytics Workspace**, and integrated **Microsoft Sentinel** to generate attack maps, alerts, and incidents.

Microsoft Sentinel monitored the environment for 24 hours, after which I implemented security controls and re-ran monitoring for another 24 hours. The goal was to demonstrate the impact of controls (mapped to **NIST 800-53**) and show how to apply **incident response strategies (NIST 800-61)** while analyzing attacker behavior through logs and alerts.

---

## 🧰 Technologies, Standards & Azure Components Used

- Azure Virtual Network (VNet)
- Azure Network Security Groups (NSG)
- Virtual Machines (2x Windows, 1x Linux)
- Log Analytics Workspace (KQL)
- Azure Key Vault (private endpoints)
- Azure Storage Account
- Microsoft Sentinel (SIEM)
- Microsoft Defender for Cloud
- Windows Remote Desktop / SSH
- Command-Line Interface (CLI)
- [NIST SP 800-53 Rev. 5 – Security Controls](https://csrc.nist.gov/projects/cprt/catalog#/cprt/framework/version/SP_800_53_5_1_0/home)
- [NIST SP 800-61 Rev. 2 – Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

---

## 🛠️ Architecture: Before Hardening

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e5c4589e-3f05-4171-b20e-be21a58e94bb.png" alt="Architecture Before"/>

In the **"Before"** phase:
- All VMs had open ports with unrestricted NSGs and no firewall rules.
- Key Vault and Storage Accounts were publicly accessible.
- Sentinel and Log Analytics were used to monitor this insecure setup.

---

## 🔐 Architecture: After Hardening

<img src="https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/e7cb31c1-15e1-4ebd-a9e7-b26a7d8f5998.png" alt="Architecture After"/>

In the **"After"** phase, I applied hardening tactics based on NIST SP 800-53 SC-7(3):

- **NSGs**: All inbound/outbound traffic was blocked except from my public IP.
- **Private Endpoints**: Key Vault and Storage Account were made accessible only within the virtual network.

---

## 📊 Attack Maps – Before Hardening

> ⚠️ *Attack maps were generated using Sentinel workbooks and prebuilt KQL JSON visualizations.*

### 🔸 NSG Left Open – Allowed Malicious Traffic

![Screenshot (5)](https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/1011e9a2-d674-4ea3-935b-23789c913ec6)

---

### 🔸 Repeated Syslog Authentication Failures

![Screenshot (7)](https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/2c61d9df-02ed-45ff-8228-c9b9566ee33d)

---

### 🔸 Excessive RDP and SMB Failures

![Screenshot (9)](https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/ef136ac5-ebef-4dd6-aefc-3c73fe84c8be)

---

### 🔸 SQL Database Exploitation Attempts

![Screenshot (4)](https://github.com/VanessaMancia/Azure-SOC-Honeynet/assets/112146207/36aeee0d-12af-4038-bed9-8aa153f855dc)

---

## ✅ Attack Maps – After Hardening

> ✔️ *All map queries returned no results, confirming no malicious activity during the hardened 24-hour window.*

---

## 📈 Metrics – Before Security Controls

> ⏱️ *Monitoring period: 2024-02-10 12:58 AM to 2024-02-11 12:58 AM*

| Metric                   | Count   |
|--------------------------|---------|
| SecurityEvent            | 61,472  |
| Syslog                   | 2,708   |
| SecurityAlert            | 36      |
| SecurityIncident         | 377     |
| AzureNetworkAnalytics_CL | 2,653   |

---

## 📉 Metrics – After Security Controls

> ⏱️ *Monitoring period: 2024-02-12 10:46 PM to 2024-02-13 10:46 PM*

| Metric                   | Count |
|--------------------------|-------|
| SecurityEvent            | 11,340|
| Syslog                   | 1     |
| SecurityAlert            | 0     |
| SecurityIncident         | 0     |
| AzureNetworkAnalytics_CL | 0     |

---

## ✅ Summary

This project demonstrates how quickly vulnerable cloud resources are targeted and how applying NIST-aligned security controls dramatically reduces risk. Using Microsoft Sentinel and Defender for Cloud, I was able to monitor, detect, and respond to attacker behavior in real time — reinforcing the importance of proactive cloud security engineering.
