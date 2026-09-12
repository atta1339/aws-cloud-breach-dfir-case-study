# 📅 Forensic Timeline — AWS Cloud Breach

## Legend
- **Actor:** IAM user or role performing the action  
- **Event:** CloudTrail event name  
- **Details:** Key metadata (IP, user agent, region)  
- **MITRE:** Technique mapping  

---

## 🕒 Timeline

### 1. Initial Access
| Timestamp | Actor | Event | Details | MITRE |
|----------|--------|--------|---------|--------|
| 2026-09-12 03:14:22 | dev-analyst | ConsoleLogin | Source IP: X.X.X.X | T1078 |

### 2. Reconnaissance
| Timestamp | Actor | Event | Details | MITRE |
|----------|--------|--------|---------|--------|
| 2026-09-12 03:15:01 | dev-analyst | ListUsers | IAM discovery | T1580 |
| 2026-09-12 03:15:10 | dev-analyst | ListBuckets | S3 discovery | T1580 |

### 3. Privilege Escalation
| Timestamp | Actor | Event | Details | MITRE |
|----------|--------|--------|---------|--------|
| 2026-09-12 03:16:44 | dev-analyst | CreateUser | system-backup created | T1136 |
| 2026-09-12 03:17:02 | dev-analyst | AttachUserPolicy | AdminAccess | T1098 |
| 2026-09-12 03:17:30 | system-backup | CreateAccessKey | Key generated | T1098 |

### 4. Persistence
| Timestamp | Actor | Event | Details | MITRE |
|----------|--------|--------|---------|--------|
| 2026-09-12 03:18:11 | system-backup | PutUserPolicy | Inline persistence policy | T1098 |

### 5. Exfiltration
| Timestamp | Actor | Event | Details | MITRE |
|----------|--------|--------|---------|--------|
| 2026-09-12 03:19:55 | system-backup | GetObject | records.csv | T1530 |
| 2026-09-12 03:20:12 | system-backup | GetObject | customers.json | T1567.002 |

---

## Summary
Attacker escalated privileges within 3 minutes of initial access and exfiltrated data within 6 minutes.
