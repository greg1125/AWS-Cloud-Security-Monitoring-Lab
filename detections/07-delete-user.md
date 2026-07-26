# IAM User Deleted Detection

## Overview

Detects deletion of IAM users.

Unexpected deletion may indicate cleanup or malicious activity.

---

## Severity

Medium

---

## KQL

```kql
event.dataset:"aws.cloudtrail"
and event.action:"DeleteUser"
```

---

## Test Procedure

Delete an IAM user.

---

## Investigation

- Verify user offboarding.
- Determine if deletion was authorized.
