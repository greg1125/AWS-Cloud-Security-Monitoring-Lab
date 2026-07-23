# AWS-Cloud-Security-Monitoring-Lab
Designed and implemented an end-to-end AWS cloud security monitoring lab using CloudTrail, S3, SQS, and Elastic SIEM. Developed custom KQL detections, validated security alerts, and created a SOC dashboard for cloud threat monitoring.


---

# Project Objectives

- Design and deploy AWS infrastructure for security monitoring.
- Configure AWS CloudTrail to capture management events.
- Forward CloudTrail logs into Elastic using S3 and SQS.
- Develop custom KQL detection rules for common AWS attack techniques.
- Validate detections by generating real AWS events.
- Build a SOC dashboard for cloud security monitoring and investigation.

---

# Architecture

```
                    AWS Account
                         │
      ┌──────────────────┴──────────────────┐
      │                                     │
   IAM / EC2 / S3 / VPC              CloudTrail
                                           │
                                           ▼
                                    Amazon S3 Bucket
                                           │
                                           ▼
                                       Amazon SQS
                                           │
                                           ▼
                                    Elastic Agent
                                           │
                                           ▼
                                   Elasticsearch
                                           │
                                           ▼
                                        Kibana
                                           │
                     ┌─────────────────────┴─────────────────────┐
                     │                                           │
              Detection Rules                            SOC Dashboard
```

---

# AWS Infrastructure

The following AWS services were deployed and configured as part of the lab:

- IAM Users
- IAM Groups
- IAM Roles
- IAM Policies
- Amazon EC2
- Amazon S3
- Amazon VPC
- Security Groups
- CloudTrail
- CloudWatch
- Amazon SNS

---

# Log Pipeline

AWS CloudTrail management events are delivered through the following ingestion pipeline:

```
CloudTrail
     │
     ▼
Amazon S3
     │
     ▼
Amazon SQS
     │
     ▼
Elastic Agent
     │
     ▼
Elasticsearch
     │
     ▼
Kibana
```

This architecture enables near real-time visibility into AWS management activity while preserving logs in S3.

---

# Detection Engineering

The project includes ten custom KQL detection rules designed to identify common cloud attack techniques.

| Detection | Severity | Event |
|------------|----------|----------------------------|
| Root Console Login | Critical | ConsoleLogin |
| Create Access Key | High | CreateAccessKey |
| Delete Access Key | Medium | DeleteAccessKey |
| Attach Administrator Policy | High | AttachUserPolicy |
| IAM User Created | Medium | CreateUser |
| IAM User Deleted | Medium | DeleteUser |
| Stop CloudTrail Logging | Critical | StopLogging |
| Delete CloudTrail | Critical | DeleteTrail |
| Security Group Changes | High | AuthorizeSecurityGroupIngress / RevokeSecurityGroupIngress |
| IAM Role Assumed | Low | AssumeRole |

Each detection includes:

- KQL query
- Severity
- MITRE ATT&CK mapping
- Investigation guidance
- False positive considerations

---

# Detection Testing

Each rule was validated by generating the corresponding AWS activity.

Examples include:

- Logging into the AWS Management Console as the root user.
- Creating and deleting IAM users.
- Creating and deleting IAM access keys.
- Attaching AdministratorAccess policies.
- Assuming IAM roles.
- Modifying Security Group ingress rules.
- Stopping CloudTrail logging.
- Deleting a CloudTrail trail.

Alerts were successfully generated and verified within Elastic.

---

# SOC Dashboard

A Kibana dashboard was created to provide visibility into AWS activity and security events.

Dashboard panels include:

- Total CloudTrail Events
- CloudTrail Activity Timeline
- Top AWS API Calls
- Top IAM Identities
- Detection Alert Table
- Alerts by Severity
- Top Source IP Addresses

The dashboard enables analysts to quickly identify suspicious AWS activity and investigate generated alerts.

---

# Technologies Used

## AWS

- IAM
- EC2
- S3
- SQS
- VPC
- CloudTrail
- CloudWatch
- SNS

## Elastic Stack

- Elastic Cloud
- Elastic Agent
- Elasticsearch
- Kibana
- Detection Engine
- Lens Visualizations

## Query Language

- Kibana Query Language (KQL)

---

# Skills Demonstrated

- AWS Cloud Security
- CloudTrail Configuration
- Elastic SIEM Administration
- Detection Engineering
- Security Monitoring
- SOC Operations
- Cloud Log Ingestion
- KQL Development
- IAM Administration
- Incident Investigation
- Dashboard Development
- MITRE ATT&CK Mapping

---

# Lessons Learned

Through this project I gained hands-on experience with:

- Designing a cloud security monitoring architecture.
- Configuring AWS CloudTrail for centralized logging.
- Building a log ingestion pipeline using S3, SQS, and Elastic Agent.
- Creating and validating custom detection rules.
- Mapping AWS events to MITRE ATT&CK techniques.
- Building analyst-focused SOC dashboards.
- Investigating AWS management activity using CloudTrail logs.

---

# Future Improvements

- Integrate Amazon GuardDuty findings.
- Monitor VPC Flow Logs.
- Monitor CloudWatch Logs.
- Add Lambda-based automated remediation.
- Expand detections for persistence and privilege escalation.
- Detect anomalous IAM behavior.
- Add EventBridge automation.
- Implement Infrastructure as Code using Terraform.

---

# Repository Structure

```
AWS-Cloud-Security-Monitoring-Lab
│
├── README.md
├── architecture/
├── detections/
├── dashboard/
└── screenshots/
```

---
