# Root Console Login Detection

## Overview

Detects successful AWS root account logins.

Root account usage should be extremely rare.

---

## MITRE ATT&CK

Initial Access

---

## Severity

Critical

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:"ConsoleLogin"
and aws.cloudtrail.user_identity.type:"Root"
```

---

## Test Procedure

Log into the AWS Management Console using the root account.

---

## Investigation

- Verify login legitimacy.
- Review recent root activity.
- Ensure MFA is enabled.
