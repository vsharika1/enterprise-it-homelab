# Architecture Decision 001 — Virtualization Strategy

## Status

**Accepted**

---

## Context

The Enterprise IT Administration Home Lab is being developed on an **Apple Silicon M1 Mac**.

The lab requires both Windows Server and Windows client operating systems to simulate a Microsoft-based enterprise environment.

Apple Silicon uses the ARM architecture, while the standard Windows Server 2025 release used for this lab is designed for x64 systems.

Running Windows Server locally on the M1 Mac would therefore require x64 emulation rather than native ARM virtualization. While this is technically possible using tools such as UTM or QEMU, it would introduce additional performance overhead and could reduce the reliability of the lab environment.

The goal of this project is to create a stable and realistic environment for practicing:

- Windows Server administration
- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- Windows client administration
- Microsoft 365
- Microsoft Entra ID
- Microsoft Intune
- PowerShell
- Identity and Access Management
- IT support and troubleshooting

---

## Decision

The initial Windows Server and Active Directory infrastructure will be hosted in **Microsoft Azure**.

The Azure environment will provide the primary infrastructure for:

- Windows Server 2025
- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- Windows domain-joined clients
- Private virtual networking
- Infrastructure troubleshooting

A local Windows 11 ARM virtual machine may later be deployed using **Parallels Desktop** for Microsoft Intune, Microsoft Entra ID, and endpoint-management testing.

This approach allows the lab to use Windows Server in a supported x64 cloud environment while still taking advantage of the Apple Silicon Mac for administration, documentation, GitHub, and future ARM-based endpoint testing.

---

## Reasons

This approach was selected to:

- Avoid the performance overhead of x64 Windows Server emulation on Apple Silicon
- Use a supported Windows Server platform
- Maintain a realistic multi-system enterprise environment
- Gain practical experience with Microsoft Azure
- Allow Windows Server and Windows client systems to communicate over a private virtual network
- Support Active Directory, DNS, DHCP, and Group Policy testing
- Support future integration with Microsoft 365
- Support future integration with Microsoft Entra ID
- Support future integration with Microsoft Intune
- Provide a scalable lab environment that can be expanded over time

---

## Planned Azure Environment

The initial Azure environment will use the following naming convention.

| Resource | Planned Name |
|---|---|
| Resource Group | `rg-northstar-homelab` |
| Virtual Network | `vnet-northstar-lab` |
| Subnet | `snet-corporate` |
| Domain Controller | `DC01` |
| Windows Client | `CLIENT01` |

---

## Planned Network

The lab will use the following private IPv4 network:

```text
Network: 192.168.10.0/24
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1
```

### Planned Addressing

| Device | Role | Planned Address |
|---|---|---|
| DC01 | Domain Controller / DNS Server | `192.168.10.10` |
| CLIENT01 | Windows Client | DHCP |
| Gateway | Virtual Network Gateway | `192.168.10.1` |

The planned DHCP range is:

```text
192.168.10.100 - 192.168.10.200
```

The final network configuration may be adjusted depending on Azure networking requirements and technical limitations discovered during implementation.

---

## Planned Architecture

```text
                         M1 Mac
                            |
                            |
                         Internet
                            |
                            |
                     Microsoft Azure
                            |
                            |
                  vnet-northstar-lab
                    192.168.10.0/24
                            |
                            |
             +--------------+--------------+
             |                             |
             |                             |
           DC01                         CLIENT01
    Windows Server 2025               Windows 11
       192.168.10.10                    DHCP
             |
             |
     +-------+-------+-------+-------+
     |               |       |       |
   AD DS            DNS     DHCP     GPO
```

---

## Planned Server Roles

The Windows Server virtual machine named `DC01` will be used for the following services:

### Active Directory Domain Services

Active Directory Domain Services will provide:

- Centralized identity management
- User authentication
- Computer authentication
- Security group management
- Organizational Unit management
- Domain-based administration

### DNS

DNS will provide:

- Internal name resolution
- Active Directory service discovery
- Domain controller lookup
- Client-to-server name resolution

### DHCP

DHCP will be used to practice:

- IP address assignment
- DHCP scopes
- DHCP reservations
- DNS configuration
- Default gateway configuration
- Lease management

### Group Policy

Group Policy will be used to centrally configure:

- Password policies
- Account lockout settings
- Windows security settings
- User restrictions
- Drive mappings
- Endpoint configuration
- Administrative policies

---

## Planned Client Configuration

`CLIENT01` will be used as a simulated corporate workstation.

The client will be used to practice:

- Domain joining
- Active Directory authentication
- Group Policy processing
- DNS troubleshooting
- DHCP troubleshooting
- Shared resource access
- User permissions
- Account lockouts
- Password resets
- Administrative troubleshooting

Additional clients may be added later if needed.

---

## Future Endpoint Management

A local Windows 11 ARM virtual machine may later be deployed on the M1 Mac using Parallels Desktop.

This environment may be used for:

- Microsoft Entra ID registration
- Microsoft Entra ID join
- Microsoft Intune enrollment
- Device compliance
- Configuration profiles
- Application deployment
- BitLocker
- Microsoft Defender
- Windows Update management
- Endpoint lifecycle testing

This local ARM-based Windows environment will complement the Azure-hosted Windows Server infrastructure.

---

## Cloud Identity Integration

The lab may later be expanded to integrate with:

- Microsoft 365
- Microsoft Entra ID
- Microsoft Intune
- Exchange Online
- Microsoft Teams
- SharePoint
- OneDrive

The long-term goal is to simulate a hybrid enterprise environment combining traditional Windows Server infrastructure with Microsoft cloud identity and endpoint-management services.

---

## Security Considerations

The lab will follow basic enterprise security principles wherever practical.

These include:

- Principle of least privilege
- Role-Based Access Control
- Separate administrative and standard-user access
- Multi-Factor Authentication
- Conditional Access
- Strong password policies
- Account lockout policies
- Security group-based permissions
- Device compliance
- Endpoint protection
- Secure onboarding and offboarding
- Controlled remote access

Administrative privileges will not be assigned to standard users unless required for a specific lab exercise.

---

## Cost Considerations

Because Microsoft Azure resources may generate usage charges, virtual machines will not be left running unnecessarily.

The expected workflow will be:

```text
Start Virtual Machine
        |
        v
Perform Lab Activities
        |
        v
Document Results
        |
        v
Shut Down / Deallocate
```

Cost-monitoring and budget controls will be configured before significant Azure resources are deployed.

---

## Documentation Approach

Each major configuration or troubleshooting exercise will be documented in the GitHub repository.

Documentation may include:

- Configuration steps
- Architecture diagrams
- Screenshots
- Troubleshooting notes
- Validation steps
- Incident simulations
- Knowledge base articles
- PowerShell scripts

Screenshots will be reviewed before publication to ensure that credentials, tokens, private information, or other sensitive data are not exposed.

---

## Alternatives Considered

### Local x64 Windows Server Emulation

Windows Server could be emulated locally using software such as UTM or QEMU.

This approach was not selected as the primary architecture because x64 emulation on Apple Silicon may introduce additional performance overhead and complexity.

### Local Windows 11 ARM Only

Windows 11 ARM can run locally on Apple Silicon using compatible virtualization software.

However, this approach alone would not provide the same Windows Server environment required for Active Directory Domain Services, DNS, DHCP, and Group Policy testing.

### Fully Cloud-Based Environment

The entire environment could be hosted in Azure.

This remains a possible future option, but a combination of Azure-hosted server infrastructure and local ARM-based endpoint testing provides more flexibility for the current project.

---

## Future Considerations

The architecture may evolve as the project progresses.

Possible future changes include:

- Additional Windows clients
- Additional Windows Server systems
- Azure-hosted management systems
- Microsoft Entra ID integration
- Microsoft Intune deployment
- Microsoft 365 integration
- Hybrid identity testing
- Additional network segments
- Additional security controls
- PowerShell automation
- Infrastructure monitoring

Any significant architecture changes will be documented in this repository.

---

## Current Implementation Status

| Component | Status |
|---|---|
| Virtualization Strategy | ✅ Accepted |
| Azure Account | ⏳ Pending |
| Cost Controls | ⏳ Planned |
| Resource Group | ⏳ Planned |
| Virtual Network | ⏳ Planned |
| Subnet | ⏳ Planned |
| DC01 | ⏳ Planned |
| Windows Server 2025 | ⏳ Planned |
| Active Directory | ⏳ Planned |
| DNS | ⏳ Planned |
| DHCP | ⏳ Planned |
| Group Policy | ⏳ Planned |
| CLIENT01 | ⏳ Planned |
| Domain Join | ⏳ Planned |
| Microsoft 365 | ⏳ Planned |
| Microsoft Entra ID | ⏳ Planned |
| Microsoft Intune | ⏳ Planned |
| Local Windows 11 ARM VM | ⏳ Future |

---

## Next Step

Create or configure the Microsoft Azure environment and establish cost controls before deploying the first lab resources.

The first planned Azure resources will be:

```text
rg-northstar-homelab
        |
        v
vnet-northstar-lab
        |
        v
snet-corporate
        |
        v
DC01
```