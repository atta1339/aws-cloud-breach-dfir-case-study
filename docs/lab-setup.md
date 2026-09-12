# 🧪 Lab Setup — AWS Cloud Breach DFIR Case Study

## 1. Prerequisites

- AWS account (lab / non-production)
- IAM user with permissions to create:
  - IAM users and policies
  - S3 buckets and objects
  - CloudTrail trails
  - GuardDuty
  - VPC Flow Logs
- AWS CLI configured (`aws configure`)

---

## 2. IAM Setup

1. Create `dev-analyst` user (simulated victim).
2. Assign limited permissions (read access to S3, basic IAM read).
3. Ensure **MFA is disabled** for realism in this scenario.

---

## 3. S3 Setup

1. Create bucket: `prod-data-bucket`.
2. Upload sample data:
   - `records.csv`
   - `customers.json`
3. Enable:
   - S3 server access logging (to a log bucket)
   - Object-level logging if desired.

---

## 4. CloudTrail Setup

1. Enable CloudTrail (if not already).
2. Ensure:
   - Management events enabled.
   - Data events for S3 enabled (read/write).
3. Optionally enable **CloudTrail Lake** for advanced querying.

---

## 5. GuardDuty Setup

1. Enable GuardDuty in the region used for the lab.
2. Keep default detectors active.
3. Optionally configure findings export to S3.

---

## 6. VPC Flow Logs Setup

1. Identify the VPC used by your workloads.
2. Enable VPC Flow Logs to:
   - CloudWatch Logs or
   - S3 bucket
3. Use these logs to correlate exfiltration patterns.

---

## 7. Attack Simulation Execution

Follow `10_attack-simulation/attack-steps.md`:

1. Log in as `dev-analyst` via console.
2. Run reconnaissance commands (IAM, S3).
3. Create `system-backup` user and attach admin policy.
4. Create access key for `system-backup`.
5. Use the key to download objects from `prod-data-bucket`.

---

## 8. Evidence Collection

- Export CloudTrail logs to `20_evidence/cloudtrail/`.
- Export GuardDuty findings to `20_evidence/guardduty/`.
- Export VPC Flow Logs to `20_evidence/vpc-flow-logs/`.
- Save screenshots of key console views to `20_evidence/screenshots/`.

---

## 9. Analysis Workflow

1. Build timeline in `30_analysis/timeline.md`.
2. Extract IOCs in `30_analysis/ioc-list.md`.
3. Run queries from `30_analysis/queries.md`.
4. Map techniques in `50_mitre-attack/coverage-matrix.md`.
5. Finalise `docs/incident-report.md`.
