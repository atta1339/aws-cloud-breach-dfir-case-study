# 📌 Case Summary — AWS Cloud Breach DFIR Investigation

## 1. Overview
This case study documents a simulated AWS cloud breach involving compromised IAM credentials, privilege escalation, backdoor account creation, and S3 data exfiltration. The project demonstrates a full DFIR workflow including evidence collection, timeline reconstruction, MITRE ATT&CK mapping, and incident reporting.

## 2. Key Events
- Attacker logged in using compromised IAM user `dev-analyst`.
- Reconnaissance performed across IAM and S3.
- Backdoor user `system-backup` created and granted admin privileges.
- Long‑lived access key generated for persistence.
- Sensitive S3 objects (`records.csv`, `customers.json`) exfiltrated.

## 3. Impact
- Exposure of sensitive data.
- Unauthorized privilege escalation.
- Creation of persistent access mechanisms.
- Full administrative compromise of the AWS account.

## 4. Detection Highlights
- CloudTrail logs captured all attacker actions.
- GuardDuty flagged anomalous IAM activity.
- S3 access logs revealed unusual object downloads.
- VPC Flow Logs supported exfiltration analysis.

## 5. MITRE ATT&CK Techniques
- **T1078** — Valid Accounts  
- **T1580** — Cloud Infrastructure Discovery  
- **T1136** — Create Account  
- **T1098** — Additional Cloud Credentials  
- **T1530** — Data from Cloud Storage  
- **T1567.002** — Exfiltration to Cloud Storage  

## 6. Lessons Learned
- Enforce MFA for all IAM users.
- Restrict IAM privilege escalation via SCPs.
- Monitor access key creation events.
- Enable CloudTrail Lake for advanced detection.
- Apply GuardDuty findings to automated response workflows.

## 7. Purpose of This Case Study
This project serves as a practical demonstration of:
- Cloud DFIR methodology  
- AWS security analysis  
- Detection engineering  
- Incident reporting  
- MITRE ATT&CK mapping  

It is designed to showcase real-world skills relevant to SOC, DFIR, and cloud security engineering roles.
