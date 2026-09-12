# 🛡️ AWS Cloud Breach DFIR Case Study  
A full end‑to‑end cloud attack simulation, forensic investigation, and MITRE ATT&CK mapping designed to demonstrate real-world DFIR, SOC analysis, and cloud security engineering skills.

---

## 📌 Overview  
This project simulates a targeted breach inside an AWS environment and reconstructs the incident using CloudTrail, GuardDuty, IAM logs, and S3 access telemetry.  
It is designed as a **professional DFIR case file**, showcasing:

- Cloud attack simulation  
- Forensic timeline reconstruction  
- Evidence collection & analysis  
- Detection engineering  
- MITRE ATT&CK mapping  
- Executive-level incident reporting  

This builds on prior cloud security work, including hands-on AWS penetration testing and structured reporting such as:

> “A structured penetration test report helps communicate findings and mitigation strategies.”

---

## 🎯 Objectives  
- Demonstrate realistic attacker behaviour in AWS  
- Collect and analyse CloudTrail, GuardDuty, and VPC Flow Logs  
- Reconstruct a complete forensic timeline  
- Identify Indicators of Compromise (IOCs)  
- Build detection rules and hunting queries  
- Map all activity to MITRE ATT&CK  
- Produce a professional incident report suitable for DFIR/SOC roles  

---

## 🏗️ Cloud Architecture  
The lab uses a minimal but realistic AWS environment:

- **VPC (10.0.0.0/16)** with public subnet  
- **IAM user** (`dev-analyst`) with moderate permissions  
- **S3 bucket** (`prod-data-bucket`) containing synthetic sensitive data  
- **CloudTrail** enabled for management events  
- **GuardDuty** enabled for threat detection  
- **Optional:** Bastion host for controlled SSH access  

Architecture mirrors earlier cloud-hosted setups such as:

> “VPC (10.0.0.0/16) with Internet Gateway, public subnet for web tier, private subnet for future DB tier.”

---

## ⚔️ Attack Scenario  
A simulated attacker gains access to the `dev-analyst` IAM user and performs:

### **1. Initial Access**
- Console login using compromised credentials  
- Reconnaissance: `ListUsers`, `ListRoles`, `ListBuckets`

### **2. Privilege Escalation**
- Creation of a backdoor IAM user: `system-backup`  
- Attachment of `AdministratorAccess`  
- Generation of long-lived access keys  

### **3. Persistence**
- Inline policy added to ensure continued access  
- Additional access key created for redundancy  

### **4. Data Exfiltration**
- `ListObjects` and `GetObject` actions against `prod-data-bucket`  
- Download of sensitive files  

All actions generate CloudTrail and GuardDuty findings for DFIR analysis.

---

## 🔍 Evidence Collected  
Evidence is stored in the `/evidence` directory:

- **CloudTrail logs** (JSON/CSV)  
- **GuardDuty findings**  
- **VPC Flow Logs**  
- **Screenshots** of AWS console events  
- **Extracted IOCs** (IPs, user agents, access keys, timestamps)

---

## 🧪 Forensic Analysis  
The `/analysis` directory contains:

### **Timeline Reconstruction**
Chronological reconstruction of attacker activity using CloudTrail event IDs, timestamps, and IP addresses.

### **IOC Sheet**
- IAM users created  
- Access keys used  
- Source IPs  
- S3 objects accessed  

### **Hunting Queries**
CloudTrail Lake, Athena, and Sigma-style queries for detecting:

- Suspicious IAM privilege escalation  
- Unusual S3 access patterns  
- CloudTrail/GuardDuty configuration changes  

---

## 🧩 MITRE ATT&CK Mapping  
All attacker actions are mapped to ATT&CK techniques, including:

- **Initial Access** – Valid Accounts (T1078)  
- **Discovery** – Cloud Infrastructure Discovery (T1580)  
- **Privilege Escalation** – Create Account (T1136)  
- **Persistence** – Additional Cloud Credentials (T1098)  
- **Collection** – Data from Cloud Storage (T1530)  
- **Exfiltration** – Exfiltration to Cloud Storage (T1567.002)  

Full mapping is available in `/mitre-attack/`.

---

## 🛠️ Detection Engineering  
Detection rules and queries are included in `/rules/`:

- Sigma-style rules for IAM privilege escalation  
- S3 exfiltration detection logic  
- Cloud-native detections using CloudTrail Lake  

---

## 📄 Incident Report  
A full DFIR-style incident report is included in `/docs/incident-report.md`, following the same structure used in earlier assessments:

- Executive Summary  
- Scope  
- Methodology  
- Findings  
- Risk Assessment  
- Mitigation  
- Conclusion  

This mirrors the structured reporting approach used previously:

> “Executive Summary — Overview of findings & impact”

---

## 🔁 Reproduction Guide  
A safe reproduction guide is included in `/docs/setup-guide.md`, covering:

- AWS environment setup  
- IAM user creation  
- S3 bucket configuration  
- CloudTrail/GuardDuty setup  
- Attack simulation steps  
- Log export instructions  

---

## ⚠️ Ethical Considerations  
- All testing performed in an isolated AWS environment  
- No real user data involved  
- All artefacts destroyed after analysis  
- Strict adherence to cloud security best practices  

---

## 📚 Folder Structure  
```text
aws-cloud-breach-dfir-case-study/
├─ 00_lab-setup/
├─ 10_attack-simulation/
├─ 20_evidence/
├─ 30_analysis/
├─ 40_rules/
├─ 50_mitre-attack/
└─ docs/
