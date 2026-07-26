# Delete Access Key Detection

## Overview

Detects deletion of IAM access keys.

Deletion may indicate credential rotation or an attacker attempting to remove evidence.

---

## MITRE ATT&CK

| Tactic | Technique |
|---------|-----------|
| Defense Evasion | T1070 |

---

## Severity

Medium

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:"DeleteAccessKey"
```

---

## Test Procedure

Delete an IAM user's access key.

---

## Investigation

- Verify expected credential rotation.
- Determine whether unauthorized users deleted credentials.

---

## False Positives

- Scheduled key rotation
- User offboarding
