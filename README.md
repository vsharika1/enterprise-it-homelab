# Enterprise IT Administration Home Lab

## Overview

This project documents the design, configuration, administration, and troubleshooting of a simulated enterprise IT environment.

The lab is designed to develop and demonstrate practical hands-on skills relevant to IT Support, Service Desk, Identity & Access Management (IAM), Microsoft 365 Administration, Endpoint Management, and Junior Systems Administration roles.

The environment simulates the IT infrastructure of a fictional organization, **NorthStar Technologies**, with approximately 25 employees across multiple departments.

> **Status:** 🚧 In Development  
> This lab is being continuously expanded as additional technologies, configurations, automation, and troubleshooting scenarios are implemented.

---

## Project Objectives

The primary objectives of this home lab are to gain practical experience with:

- Windows Server administration
- Active Directory Domain Services (AD DS)
- Microsoft Entra ID
- Microsoft 365 administration
- Identity and Access Management (IAM)
- Microsoft Intune
- Windows endpoint management
- DNS and DHCP
- Group Policy
- Role-Based Access Control (RBAC)
- Multi-Factor Authentication (MFA)
- Conditional Access
- PowerShell automation
- IT troubleshooting
- User onboarding and offboarding
- Technical documentation
- Help Desk incident management

---

## Planned Lab Environment

### Organization

**Company:** NorthStar Technologies  
**Environment:** Simulated enterprise organization  
**Users:** Approximately 25  
**Departments:**

- Information Technology
- Human Resources
- Finance
- Sales
- Operations
- Management

---

## Technologies

| Category | Technologies |
|---|---|
| Server Infrastructure | Windows Server 2025 |
| Directory Services | Active Directory Domain Services |
| Cloud Identity | Microsoft Entra ID |
| Productivity | Microsoft 365 |
| Email | Exchange Online |
| Endpoint Management | Microsoft Intune |
| Operating Systems | Windows 11 |
| Networking | DNS, DHCP, TCP/IP |
| Security | MFA, Conditional Access, RBAC, BitLocker, Microsoft Defender |
| Automation | PowerShell |
| Documentation | Markdown, GitHub |
| Support | Incident Troubleshooting, Knowledge Base Documentation |

---

## Planned Architecture

```text
                    Microsoft 365
                         │
                  Microsoft Entra ID
                         │
              ┌──────────┼──────────┐
              │          │          │
             MFA       RBAC    Conditional
                                  Access
                         │
                       Intune
                         │
                  Windows Endpoints

                         │

                  Windows Server
                         │
              Active Directory DS
                         │
           ┌─────────────┼─────────────┐
           │             │             │
          DNS           DHCP          GPO
                         │
                  Windows Clients
```

A detailed architecture diagram will be added as the environment is developed.

---

## Project Modules

### 1. Windows Server & Active Directory

Planned activities include:

- Installing Windows Server
- Deploying Active Directory Domain Services
- Creating an Active Directory forest and domain
- Designing Organizational Units
- Creating users and security groups
- Joining Windows clients to the domain
- Configuring Group Policy
- Managing NTFS and shared-folder permissions
- Configuring DNS
- Configuring DHCP

---

### 2. Microsoft 365 Administration

Planned activities include:

- User creation and administration
- License management
- Microsoft 365 groups
- Exchange Online
- Shared mailboxes
- Distribution groups
- Microsoft Teams
- SharePoint
- OneDrive

---

### 3. Microsoft Entra ID & Identity Management

Planned activities include:

- User and group administration
- Role-Based Access Control
- Multi-Factor Authentication
- Self-Service Password Reset
- Conditional Access
- Sign-in log analysis
- Least-privilege administration
- Identity lifecycle management

---

### 4. Microsoft Intune

Planned activities include:

- Device enrollment
- Compliance policies
- Configuration profiles
- Application deployment
- Windows security configuration
- BitLocker
- Microsoft Defender
- Windows Update management
- Device lifecycle administration

---

### 5. PowerShell Automation

PowerShell will be used to automate common IT administrative tasks such as:

- User provisioning
- User deprovisioning
- Bulk account creation
- Group membership management
- Active Directory reporting
- Account auditing
- Computer inventory

---

### 6. Help Desk & Troubleshooting

The lab will include simulated enterprise support incidents involving:

- Account lockouts
- Password resets
- Active Directory permissions
- DNS problems
- DHCP problems
- Group Policy
- Microsoft 365
- MFA
- Exchange Online
- Intune enrollment
- Device compliance
- Application deployment
- User onboarding
- User offboarding

Each scenario will document:

**Issue → Investigation → Troubleshooting → Root Cause → Resolution → Verification**

---

### 7. Technical Documentation

The repository will contain documentation including:

- Network diagrams
- Configuration procedures
- User onboarding procedures
- User offboarding procedures
- Troubleshooting guides
- Knowledge base articles
- PowerShell documentation
- Security configuration explanations

---

## Security & Privacy

This project uses a controlled lab environment and fictional company information.

No production credentials, authentication tokens, API keys, private user information, or organizational data are stored within this repository.

Screenshots containing sensitive information will be sanitized before publication.

---

## Current Progress

| Module | Status |
|---|---|
| Lab Architecture | ⏳ Planned |
| Windows Server | ⏳ Planned |
| Active Directory | ⏳ Planned |
| DNS & DHCP | ⏳ Planned |
| Group Policy | ⏳ Planned |
| Microsoft 365 | ⏳ Planned |
| Microsoft Entra ID | ⏳ Planned |
| Microsoft Intune | ⏳ Planned |
| PowerShell Automation | ⏳ Planned |
| Help Desk Scenarios | ⏳ Planned |
| Knowledge Base | ⏳ Planned |

---

## About This Project

This home lab is part of my ongoing professional development in enterprise IT administration, identity and access management, Microsoft cloud technologies, endpoint management, infrastructure support, and IT security.

The project is intended to demonstrate practical learning through documented hands-on implementation rather than production experience.
