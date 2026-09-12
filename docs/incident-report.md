# 🛡️ Incident Response Report — AWS Cloud Breach Case Study

## 1. Executive Summary
A simulated breach occurred within the AWS environment involving compromised IAM credentials, privilege escalation, persistence mechanisms, and S3 data exfiltration.  
This report documents the attack sequence, forensic findings, impact assessment, and recommended mitigations.

## 2. Scope
- AWS Account (single region)
- IAM identities
- S3 storage
- CloudTrail & GuardDuty telemetry
- No production data involved

## 3. Methodology
- CloudTrail log analysis  
- GuardDuty findings review  
- IAM policy & access key audit  
- S3 access pattern analysis  
- MITRE ATT&CK mapping  
- Timeline reconstruction

## 4. Attack Summary
- Initial Access via compromised IAM user  
- Reconnaissance of IAM & S3  
- Privilege escalation through backdoor user creation  
- Persistence via long-lived access keys  
- Exfiltration of sensitive S3 objects

## 5. Forensic Findings
### 5.1 Initial Access
- `ConsoleLogin` from unfamiliar IP  
- Recon API calls: `ListUsers`, `ListRoles`, `ListBuckets`

### 5.2 Privilege Escalation
- `CreateUser` → `system-backup`  
- `AttachUserPolicy` → `AdministratorAccess`  
- `CreateAccessKey` for persistence

### 5.3 Exfiltration
- `ListObjects` and `GetObject` on `prod-data-bucket`  
- Multiple downloads from attacker IP

## 6. Indicators of Compromise (IOCs)
- Suspicious IP addresses  
- Newly created IAM users  
- Access keys associated with attacker  
- S3 object paths accessed  
- User agents from CloudTrail

## 7. Impact Assessment
- Unauthorized access to sensitive S3 data  
- Full administrative privileges obtained  
- Persistence mechanisms established  
- Potential for lateral movement

## 8. Mitigation Recommendations
- Enforce MFA for all IAM users  
- Replace IAM users with roles + SSO  
- Enable CloudTrail + GuardDuty organization-wide  
- Apply least privilege IAM policies  
- Monitor for anomalous S3 access patterns  
- Rotate all access keys

## 9. Conclusion
The simulated breach demonstrates how quickly attackers can escalate privileges and exfiltrate data in AWS.  
Implementing the recommended controls will significantly reduce risk and improve detection capability.

