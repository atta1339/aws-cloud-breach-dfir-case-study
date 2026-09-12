███████╗██████╗ ███████╗██████╗     ██████╗ ██████╗ ███████╗ █████╗ ██████╗ ██╗  ██╗
██╔════╝██╔══██╗██╔════╝██╔══██╗    ██╔══██╗██╔══██╗██╔════╝██╔══██╗██╔══██╗██║ ██╔╝
█████╗  ██████╔╝█████╗  ██████╔╝    ██████╔╝██████╔╝█████╗  ███████║██████╔╝█████╔╝ 
██╔══╝  ██╔══██╗██╔══╝  ██╔══██╗    ██╔══██╗██╔══██╗██╔══╝  ██╔══██║██╔══██╗██╔═██╗ 
███████╗██║  ██║███████╗██║  ██║    ██║  ██║██║  ██║███████╗██║  ██║██║  ██║██║  ██╗
╚══════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝    ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝

              AWS CLOUD BREACH — DFIR CASE STUDY

# ☁️ AWS Cloud Breach — DFIR Case Study

A full end‑to‑end digital forensics and incident response (DFIR) investigation of a simulated AWS cloud breach. This project demonstrates real-world cloud security analysis, detection engineering, and incident reporting workflows used by SOC and DFIR teams.

---

## 🔥 What This Project Covers

### **1. Attack Simulation**
A realistic attacker scenario:
- Compromised IAM credentials  
- Reconnaissance (IAM + S3)  
- Privilege escalation  
- Backdoor user creation  
- Long‑lived access key generation  
- S3 data exfiltration  

### **2. Evidence Collection**
Stored under `20_evidence/`:
- CloudTrail logs  
- GuardDuty findings  
- VPC Flow Logs  
- Screenshots  

### **3. Forensic Analysis**
Located in `30_analysis/`:
- Timeline reconstruction  
- Indicators of Compromise (IOCs)  
- Detection & hunting queries  
- Screenshots and notes  

### **4. MITRE ATT&CK Mapping**
Located in `50_mitre-attack/`:
- Technique mapping  
- Coverage matrix  

### **5. Documentation**
Located in `docs/`:
- Incident report  
- Architecture diagrams  
- Lab setup instructions  
- Case summary  

---

## 🧩 Repository Structure

aws-cloud-breach-dfir-case-study/
│
├── 10_attack-simulation/        # Attacker steps & reproduction
├── 20_evidence/                 # Logs, findings, screenshots
├── 30_analysis/                 # Timeline, IOCs, queries
├── 50_mitre-attack/             # ATT&CK coverage
└── docs/                        # Reports, architecture, lab setup


---

## 🎯 Skills Demonstrated

- Cloud forensics (AWS)
- IAM breach analysis
- S3 exfiltration investigation
- CloudTrail Lake & Athena querying
- GuardDuty interpretation
- MITRE ATT&CK mapping
- Incident reporting
- Detection engineering
- DFIR documentation

---

## 📘 Case Summary

See: `docs/case-summary.md`

---

## 🚨 Incident Report

See: `docs/incident-report.md`

---

## 🧪 Lab Setup

See: `docs/lab-setup.md`

---

## 🏗 Architecture

See: `docs/architecture.md`

---

## 💼 Why This Project Matters

This case study is designed to demonstrate practical DFIR and cloud security skills relevant to:

- SOC Analyst  
- DFIR Analyst  
- Cloud Security Engineer  
- Detection Engineer  
- Security Consultant  