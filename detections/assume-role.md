# Assume Role Detection

## Overview

Detects AWS IAM role assumption.

Role assumption is common but should be monitored for unusual identities or patterns.

---

## MITRE ATT&CK

Credential Access

---

## Severity

Low

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:"AssumeRole"
```

---

## Test Procedure

Assume an IAM role or trigger a service role assumption.

---

## Investigation

- Identify the source identity.
- Determine which role was assumed.
- Verify expected behavior.

---

## False Positives

- Normal AWS service activity
- IAM role switching
- Cross-account automation
