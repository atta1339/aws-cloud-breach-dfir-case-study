# 🧪 Indicators of Compromise (IOCs)

This file contains all extracted Indicators of Compromise related to the AWS Cloud Breach DFIR case study.

---

## 1. IAM Identities
- **Compromised user:** `dev-analyst`
- **Backdoor user:** `system-backup`
- **Access key created:** Yes (long‑lived)

---

## 2. Source IP Addresses
- **Attacker IP:** X.X.X.X  
  (Replace with actual IP from CloudTrail)

---

## 3. CloudTrail Events of Interest
- `ConsoleLogin`
- `ListUsers`
- `ListBuckets`
- `CreateUser`
- `AttachUserPolicy`
- `CreateAccessKey`
- `PutUserPolicy`
- `GetObject`

---

## 4. S3 Objects Accessed
- `records.csv`
- `customers.json`

---

## 5. Regions Involved
- `ap-southeast-2` (example)
- Replace with actual region from logs

---

## 6. User Agents
- AWS Console (browser)
- AWS CLI (programmatic)

---

## 7. MITRE Techniques
- T1078 — Valid Accounts  
- T1580 — Cloud Infrastructure Discovery  
- T1136 — Create Account  
- T1098 — Additional Cloud Credentials  
- T1530 — Data from Cloud Storage  
- T1567.002 — Exfiltration to Cloud Storage  
