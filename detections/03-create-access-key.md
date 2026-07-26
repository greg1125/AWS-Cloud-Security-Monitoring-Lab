# Create Access Key Detection

## Overview

Detects the creation of new IAM access keys.

Long-lived access keys provide persistent API access and are frequently abused by attackers to establish persistence within an AWS environment.

---

## MITRE ATT&CK

| Tactic | Technique |
|---------|-----------|
| Persistence | T1098 - Account Manipulation |

---

## Severity

High

---

## KQL Detection

```kql
event.dataset:"aws.cloudtrail"
and event.action:"CreateAccessKey"
```

---

## Test Procedure

1. Navigate to IAM.
2. Select an IAM user.
3. Open **Security Credentials**.
4. Create a new Access Key.
5. Wait for CloudTrail ingestion.

---

## Expected Result

An alert is generated indicating a new IAM access key was created.

---

## Investigation Steps

- Identify the IAM user.
- Determine if key creation was authorized.
- Review recent AWS activity from the same identity.
- Rotate or delete unauthorized access keys.

---

## False Positives

- New developer onboarding
- Application deployment
- Authorized credential rotation

---

## References

- AWS CloudTrail
- MITRE ATT&CK T1098
