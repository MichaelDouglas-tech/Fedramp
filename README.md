# Fedramp# FedRAMP Moderate Gap Assessment & POA&M Project

## Project Overview

This project demonstrates a mock Governance, Risk, and Compliance (GRC) assessment against the
Federal Risk and Authorization Management Program (FedRAMP Moderate) baseline for a cloud-hosted
SaaS environment deployed in AWS.

The assessment evaluates security control implementation, identifies compliance gaps, documents
risk ratings, and produces a Plan of Action and Milestones (POA&M) for remediation tracking.

## Assessment Objectives

- Assess control implementation against FedRAMP baseline
- Identify deficiencies in security controls
- Assign risk ratings to discovered gaps
- Develop remediation milestones
- Produce a POA&M for continuous monitoring

---

# Repository Structure

```text
FedRAMP-Gap-Assessment-Project/
│
├── README.md
├── FedRAMP_Baseline_Gaps.xlsx
├── POAM.xlsx
├── Evidence/
│   ├── IAM_MFA_Report.pdf
│   ├── Tenable_Scan_Report.pdf
│   ├── AWS_Config_Evidence.pdf
│
└── Diagrams/
    └── FedRAMP_Control_Mapping.png
```

---

# Excel Worksheet 1 — FedRAMP Baseline Gaps

| Control ID | Control Name | Status | Gap | Risk |
|-----------|---------------|--------|-----|------|
| AC-2 | Account Management | Partial | Inactive accounts not removed | High |
| AC-6 | Least Privilege | Partial | Admin rights in production | High |
| IA-2(1) | MFA Privileged Accounts | Not Implemented | Root account lacks MFA | Critical |
| AU-11 | Audit Retention | Not Implemented | 30 days retained vs 90 required | High |
| RA-5 | Vulnerability Scanning | Partial | No 15-day critical remediation SLA | High |
| CP-10 | Disaster Recovery Testing | Not Implemented | No annual recovery exercise | High |
| IR-8 | Incident Response Plan | Not Implemented | Plan incomplete | High |
| CA-7 | Continuous Monitoring | Not Implemented | No ConMon strategy | High |

---

## Control Analysis

### AC-6 Least Privilege
Issue:
Developers have excessive AdministratorAccess privileges in production.

Risk:
Violates least privilege principles and increases privilege escalation exposure.

Recommendation:
Replace broad permissions with role-based IAM policies.

---

### IA-2(1) Multi-Factor Authentication
Issue:
Root AWS account lacks hardware MFA.

Risk:
Potential full cloud compromise if credentials are stolen.

Recommendation:
Deploy hardware tokens (YubiKeys) and enforce MFA.

---

### AU-11 Audit Retention
Issue:
CloudWatch logs retained only 30 days.

Requirement:
FedRAMP requires:

90 days online  
1 year archived

Gap:
Noncompliant retention period.

---

# Excel Worksheet 2 — Risk Register

| Risk ID | Description | Likelihood | Impact | Score | Rating |
|---------|-------------|------------|--------|-------|--------|
| R-001 | Root account no MFA | 5 | 5 | 25 | Critical |
| R-002 | Excessive admin privileges | 4 | 5 | 20 | High |
| R-003 | Inadequate log retention | 4 | 4 | 16 | High |
| R-004 | Missing ConMon strategy | 4 | 4 | 16 | High |

Formula:

Risk Score = Likelihood x Impact

Example:

5 x 5 = 25 (Critical)

---

# Excel Worksheet 3 — POA&M

| POAM ID | Weakness | Control | Status | Due Date |
|---------|----------|---------|--------|---------|
| POAM-001 | Root account no MFA | IA-2(1) | Open | 45 Days |
| POAM-002 | Log retention gap | AU-11 | Open | 30 Days |
| POAM-003 | Patch SLA missing | RA-5 | Open | 60 Days |
| POAM-004 | Excessive admin access | AC-6 | Open | 21 Days |

---

## Example POA&M Entry

### POAM-001

Weakness:
AWS root account lacks hardware MFA.

Resources Required:
- 2 YubiKeys
- 4 engineering hours

Milestones:
1. Purchase hardware keys  
2. Enable MFA  
3. Update runbook  
4. Validate implementation

Status:
Open

Risk:
Critical

---

# Security Findings Summary

## Critical Findings
- Privileged account MFA missing
- Overprivileged IAM access

## High Findings
- Audit retention deficiency
- Disaster recovery testing gap
- Continuous monitoring absent

Overall Risk Rating:

HIGH

Authorization Recommendation:

Conditional Approval Pending Remediation

---

# Skills Demonstrated

- FedRAMP Control Assessment
- NIST 800-53 Mapping
- POA&M Development
- Vulnerability Management
- Risk Register Creation
- Continuous Monitoring
- AWS Security Governance

---

# Tools Referenced

- Tenable / Nessus
- AWS IAM
- AWS Config
- CloudWatch
- GuardDuty
- Jira
- YubiKey

---

# Portfolio Summary

Conducted a mock FedRAMP Moderate control assessment of a cloud-hosted SaaS system. Identified control gaps, assigned risk ratings, developed a remediation POA&M, and mapped findings to NIST 800-53 control requirements using structured GRC methodology.
