# 🧩 MITRE ATT&CK Coverage Matrix

| Stage | Technique | ID | Evidence Source | Detection Notes |
|-------|-----------|-----|-----------------|-----------------|
| Initial Access | Valid Accounts | T1078 | CloudTrail: ConsoleLogin | Unfamiliar IP, unusual UA |
| Discovery | Cloud Infrastructure Discovery | T1580 | ListUsers, ListRoles, ListBuckets | Baseline deviation |
| Privilege Escalation | Create Account | T1136 | CreateUser | Rare event for IAM users |
| Privilege Escalation | Additional Cloud Credentials | T1098 | CreateAccessKey | High-risk event |
| Persistence | Modify IAM Policies | T1098 | PutUserPolicy | Inline admin policy |
| Collection | Data from Cloud Storage | T1530 | GetObject | Large volume or unusual IP |
| Exfiltration | Exfiltration to Cloud Storage | T1567.002 | S3 cp/download | Cross-region or new identity |
| Defense Evasion (optional) | CloudTrail Tampering | T1562.008 | StopLogging | Critical alert |
