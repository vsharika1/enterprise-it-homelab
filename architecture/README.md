# Enterprise IT Lab Architecture

## Overview

This section documents the architecture and design of the **Enterprise IT Administration Home Lab**.

The environment is designed to simulate the infrastructure of a small organization named **NorthStar Technologies** with approximately 25 employees across multiple departments.

The lab will integrate on-premises infrastructure with Microsoft cloud services to provide hands-on experience with enterprise identity, endpoint management, networking, security, automation, and IT support.

---

## Organization

**Company:** NorthStar Technologies
**Environment:** Simulated enterprise IT environment
**Users:** Approximately 25

### Departments

- Information Technology
- Human Resources
- Finance
- Sales
- Operations
- Management

---

## Planned Infrastructure

The lab will include the following core systems:

| System | Purpose |
|---|---|
| Windows Server | Active Directory and infrastructure services |
| Active Directory Domain Services | Centralized identity and authentication |
| DNS | Internal name resolution |
| DHCP | Automatic IP address assignment |
| Group Policy | Centralized Windows configuration |
| Windows 11 Clients | Simulated employee workstations |
| Microsoft 365 | Cloud productivity and administration |
| Microsoft Entra ID | Cloud identity and access management |
| Microsoft Intune | Endpoint and device management |
| PowerShell | Administration and automation |

---

## Planned Architecture

```text
                         INTERNET
                            |
                            |
                     Microsoft 365
                            |
                    Microsoft Entra ID
                            |
             +--------------+--------------+
             |              |              |
            MFA            RBAC      Conditional Access
                            |
                            |
                         Intune
                            |
                    Managed Endpoints
                            |
                            |
              =========================
              Enterprise Lab Network
              =========================
                            |
                      Windows Server
                         DC01
                            |
                 Active Directory DS
                            |
         +------------------+------------------+
         |                  |                  |
        DNS                DHCP          Group Policy
         |                  |                  |
         +------------------+------------------+
                            |
                   Windows 11 Clients
                    CLIENT01 / CLIENT02
```

---

## Network Design

The internal lab network is planned to use a private IPv4 address range.

### Planned Network

```text
Network: 192.168.10.0/24
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1
```

| Device | Role | Planned IP Address |
|---|---|---|
| DC01 | Domain Controller / DNS Server | 192.168.10.10 |
| CLIENT01 | Windows Client | DHCP |
| CLIENT02 | Windows Client | DHCP |
| Gateway | Default Gateway | 192.168.10.1 |

### Planned DHCP Scope

```text
192.168.10.100 - 192.168.10.200
```

DNS services will initially be provided by the domain controller.

> The network configuration may be adjusted depending on the final virtualization platform and networking capabilities available on the host system.

---

## Active Directory Design

The Active Directory environment will use a structured Organizational Unit design to separate users, computers, servers, and administrative objects.

```text
NorthStar Technologies
|
+-- Users
|   |
|   +-- IT
|   +-- HR
|   +-- Finance
|   +-- Sales
|   +-- Operations
|   +-- Management
|
+-- Computers
|   |
|   +-- Workstations
|
+-- Servers
|
+-- Groups
|
+-- Disabled Users
```

### Planned Security Groups

```text
GG-IT
GG-HR
GG-Finance
GG-Sales
GG-Operations
GG-Management
```

Security groups will be used to provide role-based access to shared resources and demonstrate the principle of least privilege.

---

## Identity and Access Management Design

The lab will simulate the complete identity lifecycle of an employee.

```text
Employee Hired
      |
      v
Account Provisioning
      |
      v
Department Assignment
      |
      v
Security Group Assignment
      |
      v
Microsoft 365 Licensing
      |
      v
MFA Registration
      |
      v
Application and Resource Access
      |
      v
Ongoing Access Management
      |
      v
Employee Offboarding
      |
      v
Access Removal / Account Disablement
```

The identity management portion of the lab will demonstrate:

- User provisioning and deprovisioning
- Group-based access control
- Role-Based Access Control
- Least-privilege administration
- Multi-Factor Authentication
- Conditional Access
- License assignment
- Account lifecycle management
- Access review and troubleshooting

---

## Endpoint Management Design

Microsoft Intune will be used to simulate centralized endpoint management.

Planned endpoint management activities include:

- Device enrollment
- Microsoft Entra ID registration or join
- Compliance policies
- Configuration profiles
- Application deployment
- Microsoft Defender configuration
- BitLocker configuration
- Windows Update management
- Device synchronization
- Device retirement
- Endpoint troubleshooting

The goal is to simulate the lifecycle of a managed corporate workstation.

```text
New Device
    |
    v
Entra ID Registration / Join
    |
    v
Intune Enrollment
    |
    v
Configuration Policies
    |
    v
Security Policies
    |
    v
Application Deployment
    |
    v
Compliance Evaluation
    |
    v
Managed Corporate Endpoint
```

---

## Security Architecture

The lab will incorporate common enterprise security principles throughout the environment.

### Planned Security Controls

- Principle of least privilege
- Role-Based Access Control
- Multi-Factor Authentication
- Conditional Access
- Strong password policies
- Account lockout policies
- Controlled administrative permissions
- Endpoint encryption
- Microsoft Defender
- Device compliance
- Secure user onboarding and offboarding
- Sign-in monitoring
- Security group-based access
- Documented access-management procedures

Administrative privileges will be separated from standard user access wherever practical.

---

## PowerShell Automation

PowerShell will be used to automate common IT administrative tasks.

Planned automation includes:

```text
Bulk user creation
User provisioning
User deprovisioning
Security group management
Inactive-user reporting
Locked-account reporting
Computer inventory
Account auditing
```

Automation scripts will be documented and tested within the controlled lab environment.

---

## Help Desk Integration

The environment will also be used to simulate common IT support incidents.

Example scenarios will include:

```text
Account lockout
Password reset
Shared-drive access failure
DNS resolution failure
DHCP issue
Group Policy failure
Microsoft 365 licensing issue
MFA registration problem
Shared mailbox access issue
Intune enrollment failure
Device compliance failure
Employee onboarding
Employee offboarding
```

Each simulated incident will document:

```text
Issue
  |
  v
Investigation
  |
  v
Troubleshooting
  |
  v
Root Cause
  |
  v
Resolution
  |
  v
Verification
```

---

## Architecture Principles

The environment is being designed around several core principles:

### Centralized Identity

Users and access will be managed through Active Directory and Microsoft Entra ID.

### Least Privilege

Users and administrators will receive only the permissions required for their roles.

### Group-Based Access

Security groups will be used instead of assigning permissions directly to individual users wherever practical.

### Centralized Endpoint Management

Managed devices will be configured and monitored through Microsoft Intune.

### Automation

PowerShell will be used to reduce repetitive administrative tasks.

### Documentation

Major configurations, troubleshooting scenarios, and changes will be documented within this repository.

---

## Planned Architecture Diagram

A visual architecture diagram will be added after the virtualization platform and final lab topology have been selected.

The final diagram will represent the relationship between:

```text
Internet
   |
   +-- Microsoft 365
   |      |
   |      +-- Microsoft Entra ID
   |      |      |
   |      |      +-- MFA
   |      |      +-- Conditional Access
   |      |      +-- RBAC
   |      |
   |      +-- Microsoft Intune
   |             |
   |             +-- Managed Windows Endpoints
   |
   +-- Enterprise Lab Network
          |
          +-- DC01
          |    |
          |    +-- Active Directory Domain Services
          |    +-- DNS
          |    +-- DHCP
          |    +-- Group Policy
          |
          +-- CLIENT01
          |
          +-- CLIENT02
```

Once created, the diagram will be stored in:

```text
architecture/
├── README.md
└── diagrams/
    └── northstar-lab-architecture.png
```

---

## Implementation Status

| Component | Status |
|---|---|
| Architecture Planning | 🟡 In Progress |
| Virtualization Platform | ⏳ Pending |
| Lab Network | ⏳ Planned |
| Windows Server | ⏳ Planned |
| Active Directory Domain Services | ⏳ Planned |
| DNS | ⏳ Planned |
| DHCP | ⏳ Planned |
| Group Policy | ⏳ Planned |
| Windows Clients | ⏳ Planned |
| File Services | ⏳ Planned |
| Microsoft 365 | ⏳ Planned |
| Microsoft Entra ID | ⏳ Planned |
| MFA | ⏳ Planned |
| Conditional Access | ⏳ Planned |
| Microsoft Intune | ⏳ Planned |
| PowerShell Automation | ⏳ Planned |
| Help Desk Scenarios | ⏳ Planned |
| Knowledge Base Documentation | ⏳ Planned |

---

## Architecture Changes

The architecture documented here represents the planned environment.

As the lab is implemented, architecture decisions may change because of virtualization requirements, licensing limitations, platform compatibility, or improvements discovered during testing.

Significant architecture changes will be documented within this repository.

---

## Current Phase

**Phase 1 — Infrastructure Planning**

Current activities:

- Define lab architecture
- Design internal network
- Select virtualization platform
- Plan Active Directory structure
- Prepare documentation repository

---

## Project Scope and Data Safety

This environment is a controlled home lab created for learning and professional development.

It does not contain:

- Production systems
- Real employee information
- Corporate credentials
- Authentication tokens
- API keys
- Private organizational data

All company names, users, departments, systems, and support incidents documented in this project are fictional unless otherwise stated.

Sensitive information will not be committed to the repository.

---

## Next Step

Select and configure the virtualization platform for hosting the Windows Server and Windows client environment.

The virtualization approach will account for the Apple Silicon architecture of the host Mac.