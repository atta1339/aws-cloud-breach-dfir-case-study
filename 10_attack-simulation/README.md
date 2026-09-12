\# 🔥 Attack Simulation



This folder contains the full AWS attack simulation used to generate CloudTrail, GuardDuty, and S3 access telemetry for DFIR analysis.



The attack chain is executed in five phases:



\## 1. Initial Access

The attacker logs into the AWS console using compromised IAM credentials, generating `ConsoleLogin` events.



\## 2. Reconnaissance

Enumeration of IAM identities and S3 buckets using AWS CLI:

\- `aws iam list-users`

\- `aws iam list-roles`

\- `aws s3 ls`

\- `aws s3api list-buckets`



\## 3. Privilege Escalation

Creation of a backdoor IAM user and assignment of administrative privileges:

\- `aws iam create-user`

\- `aws iam attach-user-policy`

\- `aws iam create-access-key`



\## 4. Persistence

Inline IAM policy added to maintain long-term access:

\- `aws iam put-user-policy`



\## 5. S3 Data Exfiltration

Sensitive objects are listed and downloaded from the target S3 bucket:

\- `aws s3 ls s3://prod-data-bucket`

\- `aws s3 cp s3://prod-data-bucket/<object> .`



\---



\## 📄 Detailed Steps

The full attack sequence is documented in:



\*\*`attack-steps.md`\*\*



This file contains all commands required to reproduce the attack and generate evidence for forensic analysis.



\---



\## ⚠️ Important Notes

\- All actions are performed in a controlled AWS lab environment.

\- No real data is used.

\- This simulation is designed for DFIR, SOC, and cloud security training.



