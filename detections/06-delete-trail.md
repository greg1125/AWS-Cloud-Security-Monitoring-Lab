# Delete CloudTrail Detection

## Overview

Detects deletion of CloudTrail trails.

Deleting audit logs is a high-confidence malicious indicator.

---

## MITRE ATT&CK

Defense Evasion

T1562.008

---

## Severity

Critical

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:"DeleteTrail"
```

---

## Test Procedure

Create a temporary CloudTrail trail.

Delete the temporary trail.

---

## Investigation

- Determine who deleted the trail.
- Verify whether replacement logging exists.
