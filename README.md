# 🔐 Active Directory Security Lab

A hands-on enterprise-style Active Directory laboratory environment built using VMware, Windows Server, and Windows 11.

This project demonstrates the deployment, configuration, administration, and testing of an Active Directory environment with multiple domain controllers, DNS, DHCP, Organizational Units, users and groups, Group Policy, a domain-joined Windows 11 client, and disaster recovery concepts.

---

## 📌 Project Overview

The objective of this project was to design and implement a functional Active Directory environment in a virtualized VMware laboratory.

The lab simulates a small enterprise network using the domain:

`cyberlab.local`

The environment includes a Primary Domain Controller, Additional Domain Controller, Read-Only Domain Controller, Windows 11 client, DNS, DHCP, Active Directory Domain Services, and Group Policy.

The project also included testing and verification of domain services, client connectivity, authentication, replication, and Active Directory recovery concepts.

---

## 🎯 Objectives

* Deploy Windows Server in a VMware virtual environment
* Install and configure Active Directory Domain Services
* Create and configure the `cyberlab.local` domain
* Configure a Primary Domain Controller
* Configure an Additional Domain Controller
* Configure a Read-Only Domain Controller
* Configure DNS for Active Directory
* Configure DHCP for automatic IP assignment
* Create Organizational Units, users, and security groups
* Configure and apply Group Policies
* Join a Windows 11 client to the domain
* Verify domain authentication and connectivity
* Understand Active Directory replication
* Explore FSMO roles and disaster recovery concepts
* Document the complete laboratory environment

---

## 🏗️ Lab Architecture

                         cyberlab.local
                              │
                     ┌────────┴────────┐
                     │                 │
               ┌─────▼─────┐     ┌────▼─────┐
               │  SRV-PDC  │     │  SRV-ADC │
               │  PDC      │◄───►│  ADC     │
               │ .10.10    │     │ .10.11   │
               └─────┬─────┘     └────┬─────┘
                     │                 │
                     │           ┌─────▼─────┐
                     │           │ SRV-RODC  │
                     │           │   RODC    │
                     │           │  .10.12   │
                     │           └───────────┘
                     │
                Virtual Network
                     │
              ┌──────▼─────────┐
              │ WIN11-CLIENT   │
              │ Domain Joined  │
              │ .10.100        │
              └────────────────┘


---

## 💻 Lab Environment

| Component       | Configuration                     |
| --------------- | --------------------------------- |
| Hypervisor      | VMware                            |
| Domain          | `cyberlab.local`                  |
| PDC             | `SRV-PDC`                         |
| PDC IP          | `192.168.10.10`                   |
| ADC             | `SRV-ADC`                         |
| ADC IP          | `192.168.10.11`                   |
| RODC            | `SRV-RODC`                        |
| RODC IP         | `192.168.10.12`                   |
| Windows Client  | Windows 11                        |
| Client Hostname | `WIN11-CLIENT`                    |
| Client IP       | `192.168.10.100`                  |
| Subnet Mask     | `255.255.255.0`                   |
| Gateway         | `192.168.10.1`                    |
| DHCP Range      | `192.168.10.100 – 192.168.10.200` |

> All systems were configured inside an isolated virtual laboratory environment.

---

## 🛠️ Technologies Used

* VMware
* Windows Server
* Windows 11
* Active Directory Domain Services
* Active Directory Users and Computers
* DNS
* DHCP
* Group Policy
* Organizational Units
* Security Groups
* Domain Controllers
* Read-Only Domain Controller
* FSMO Roles
* Windows Administrative Tools

---

## 🔧 Active Directory Components

### Primary Domain Controller

The Primary Domain Controller was configured as the main Active Directory server for the `cyberlab.local` domain.

Responsibilities included:

* Active Directory Domain Services
* DNS
* DHCP
* Domain authentication
* User and group management
* Group Policy administration
* Directory services

---

### Additional Domain Controller

An Additional Domain Controller was deployed to provide redundancy and demonstrate Active Directory replication.

`SRV-ADC`

IP address:

`192.168.10.11`

The ADC allows the environment to continue providing directory services if the primary controller becomes unavailable.

---

### Read-Only Domain Controller

A Read-Only Domain Controller was configured as part of the laboratory environment.

`SRV-RODC`

IP address:

`192.168.10.12`

The RODC provides a read-only copy of the Active Directory database and is useful for scenarios where additional domain services are required while reducing the risk associated with writable domain controllers.

---

## 🌐 Network Configuration

The laboratory uses the following private network:

```text
Network:       192.168.10.0/24
Subnet Mask:   255.255.255.0
Gateway:       192.168.10.1
```

### Static Server Addresses

```text
SRV-PDC      → 192.168.10.10
SRV-ADC      → 192.168.10.11
SRV-RODC     → 192.168.10.12
```

### DHCP

The DHCP scope was configured to provide client addresses within:

```text
192.168.10.100
        ↓
192.168.10.200
```

The Windows 11 client received its network configuration through DHCP.

---

## 👥 Active Directory Structure

The domain was organized using Active Directory Users and Computers.

The laboratory included:

* Organizational Units
* Users
* Security Groups
* Computer accounts
* Domain administrators
* Domain users

This structure was used to demonstrate centralized identity and access management.

---

## 🔐 Group Policy

Group Policy was used to demonstrate centralized management of Windows systems within the domain.

The project included configuration and testing of domain-level policies and security settings.

Group Policy provides administrators with a centralized method of applying configuration and security controls to users and computers.

---

## 🖥️ Windows 11 Domain Client

A Windows 11 virtual machine was configured as a domain client.

Hostname:

`WIN11-CLIENT`

The client was successfully joined to:

`cyberlab.local`

After joining the domain, domain authentication and connectivity were verified.

---

## 🧪 Testing & Verification

The laboratory environment was tested to verify:

* Domain connectivity
* DNS resolution
* DHCP address assignment
* Domain membership
* User authentication
* Active Directory functionality
* Domain controller communication
* Replication concepts
* Group Policy application
* Windows client connectivity

Example verification commands included:

```powershell
ipconfig /all
```

```powershell
nslookup cyberlab.local
```

```powershell
whoami
```

```powershell
gpresult /r
```

---

## 🚨 Disaster Recovery & FSMO Concepts

The project also explored Active Directory disaster recovery concepts and Flexible Single Master Operations (FSMO) roles.

The purpose was to understand:

* FSMO role ownership
* Domain Controller failure scenarios
* Role transfer
* Role seizure concepts
* Domain availability
* Active Directory recovery considerations

This helped demonstrate how Active Directory environments can be designed with redundancy and recovery in mind.

---

## 📸 Screenshots

Screenshots documenting the implementation will be added to this repository.

Planned documentation includes:

* VMware virtual machines
* Windows Server installation
* Active Directory Domain Services
* Domain Controller configuration
* Active Directory Users and Computers
* DNS configuration
* DHCP configuration
* Organizational Units
* Users and Groups
* Group Policy
* Windows 11 domain joining
* Domain verification
* Testing and troubleshooting

---

## 🧠 Key Learnings

Through this project, I gained practical experience with:

* Windows Server administration
* Active Directory architecture
* Domain Controller deployment
* Identity and access management
* DNS and DHCP
* User and group administration
* Group Policy
* Domain joining
* Active Directory replication
* RODC architecture
* FSMO roles
* Virtualized enterprise environments
* Troubleshooting Windows domain services

---

## 🔮 Future Improvements

Future versions of this laboratory could include:

* SIEM integration using Wazuh
* Windows event log monitoring
* Active Directory security auditing
* PowerShell automation
* Advanced Group Policy hardening
* Vulnerability assessment
* Kerberos security testing
* BloodHound-based AD security analysis
* Centralized logging
* Detection and response scenarios

---

## 👩‍💻 Author

**Neha**

B.Sc. IT | Cybersecurity & Ethical Hacking

Interested in:

* Cybersecurity
* Ethical Hacking
* SOC Operations
* Network Security
* Active Directory Security
* Cloud Security

---

## ⚠️ Disclaimer

This project was created for educational purposes in an isolated virtual laboratory environment.

All security testing and experimentation should be performed only on systems for which you have explicit authorization.
