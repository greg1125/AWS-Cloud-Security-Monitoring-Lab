# Stop CloudTrail Detection

## Overview

Detects CloudTrail logging being disabled.

Stopping CloudTrail reduces visibility into AWS activity and is a common defense evasion technique.

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
and event.action:"StopLogging"
```

---

## Test Procedure

Stop logging on a CloudTrail trail.

Immediately restart logging after validation.

---

## Investigation

- Determine who stopped logging.
- Review AWS activity immediately before logging stopped.
- Verify CloudTrail has been re-enabled.
