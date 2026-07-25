# Security Group Changes Detection

## Overview

Detects inbound security group modifications.

Unexpected firewall changes may expose cloud resources to unauthorized access.

---

## MITRE ATT&CK

Initial Access

---

## Severity

High

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:(
"AuthorizeSecurityGroupIngress"
or
"RevokeSecurityGroupIngress"
)
```

---

## Test Procedure

Add or remove an inbound security group rule.

---

## Investigation

- Review modified ports.
- Verify source CIDRs.
- Confirm business justification.
