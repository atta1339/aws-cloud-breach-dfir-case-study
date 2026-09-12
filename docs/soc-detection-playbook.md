# 🛡 SOC Detection Playbook — AWS Cloud Breach

This playbook outlines how a SOC team should detect, triage, investigate, and respond to the attack simulated in this DFIR case study.

---

## 1. Detection Triggers

### 🔸 CloudTrail
- `ConsoleLogin` from unusual IP  
- `CreateUser`, `AttachUserPolicy`, `CreateAccessKey`  
- Excessive `GetObject` events  

### 🔸 GuardDuty
- IAM anomaly findings  
- Suspicious access key creation  
- Privilege escalation alerts  

### 🔸 S3 Access Logs
- Large volume downloads  
- Access from new identity  

### 🔸 VPC Flow Logs
- Outbound data spikes  
- Traffic to unknown external IPs  

---

## 2. Triage Steps

1. Validate the identity used (`dev-analyst`).  
2. Check login source IP and user agent.  
3. Identify privilege escalation events.  
4. Confirm creation of `system-backup` user.  
5. Check for long-lived access key creation.  
6. Review S3 object access patterns.

---

## 3. Investigation Workflow

1. Build timeline using CloudTrail Lake queries.  
2. Extract IOCs (IPs, user agents, identities).  
3. Correlate S3 access logs with VPC Flow Logs.  
4. Validate GuardDuty findings.  
5. Confirm exfiltration volume and destination.

---

## 4. Response Actions

### 🔸 Immediate
- Disable compromised IAM user.  
- Delete backdoor user and access keys.  
- Rotate all credentials.  
- Block attacker IP at network level.  

### 🔸 Short-Term
- Enable MFA for all IAM users.  
- Restrict IAM privilege escalation via SCPs.  
- Enable CloudTrail Lake for advanced detection.  

### 🔸 Long-Term
- Implement automated detection for IAM anomalies.  
- Apply least privilege IAM policies.  
- Monitor S3 access patterns continuously.

---

## 5. Lessons for SOC Teams

- IAM events are high-signal indicators.  
- Access key creation should always trigger alerts.  
- S3 exfiltration requires correlation across logs.  
- GuardDuty findings should be integrated into SOAR workflows.
