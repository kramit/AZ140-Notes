# Acronyms

## AD — Active Directory
Active Directory is Microsoft’s directory service for managing identities, computers, and resources in a domain. It provides centralized authentication, authorization, and policy enforcement for Windows environments.

## ADE — Azure Disk Encryption
Azure Disk Encryption protects VM disks by using OS-level encryption (BitLocker for Windows, dm-crypt for Linux). It integrates with Azure Key Vault to store and manage encryption keys and secrets.

## AMA — Azure Monitor Agent
Azure Monitor Agent is the modern data collection agent for Azure Monitor. It collects logs and performance data and uses Data Collection Rules to control what is gathered and where it is sent.

## ANF — Azure NetApp Files
Azure NetApp Files is a high-performance, enterprise-grade file storage service built on NetApp technology. It provides NFS/SMB volumes with predictable low latency and throughput.

## AVD — Azure Virtual Desktop
Azure Virtual Desktop is Microsoft’s cloud VDI platform that delivers Windows desktops and apps from Azure. It supports multi-session Windows, app publishing, and centralized management.

## BCDR — Business Continuity and Disaster Recovery
BCDR refers to planning and processes that keep services running during outages and recover them afterward. It combines high availability, backup, and failover strategies.

## BYOD — Bring Your Own Device
BYOD describes allowing users to access corporate resources from personal devices. It often requires added security controls such as conditional access and device compliance policies.

## CBA — Certificate-Based Authentication
Certificate-Based Authentication uses client certificates to validate user or device identity. It is commonly used for strong authentication in enterprise environments.

## CAL — Client Access License
A Client Access License is a Microsoft license that permits users or devices to access a server product or service. CAL requirements vary by product and licensing model.

## CLI — Command-Line Interface
A CLI is a text-based interface used to execute commands and automate tasks. Azure CLI is the common CLI used for managing Azure resources.

## CMK — Customer-Managed Key
CMK refers to encryption keys that customers create and manage, typically in Azure Key Vault. It provides control over key rotation and access policies.

## CNAPP — Cloud-Native Application Protection Platform
CNAPP is a unified security approach that combines posture management, workload protection, and runtime security for cloud-native apps. It helps manage risks across build, deploy, and run stages.

## CSPM — Cloud Security Posture Management
CSPM tools assess cloud configurations for misconfigurations and compliance gaps. They help maintain secure baselines across subscriptions and resources.

## CWPP — Cloud Workload Protection Platform
CWPP focuses on protecting workloads such as VMs, containers, and serverless functions. It provides threat detection, vulnerability management, and runtime protection.

## DCR — Data Collection Rule
A Data Collection Rule defines what data the Azure Monitor Agent collects and where it sends it. It centralizes data routing for logs and metrics.

## DNS — Domain Name System
DNS translates human-readable names into IP addresses. It is fundamental for service discovery and network connectivity.

## DSCP — Differentiated Services Code Point
DSCP is a field in IP headers used for QoS marking. It helps prioritize network traffic like real-time audio or RDP sessions.

## FOD — Feature on Demand
Feature on Demand refers to Windows components that can be added post-install, such as language packs or optional features. It helps keep base images lean.

## GPO — Group Policy Object
A GPO is a set of policy settings applied to users and computers in Active Directory. It is used to configure security, settings, and software at scale.

## HA — High Availability
High Availability is a design approach that minimizes downtime through redundancy and failover. It improves service resilience within a region or across regions.

## HDD — Hard Disk Drive
HDD is a traditional spinning disk storage device. It is generally lower cost but slower than SSD storage.

## IOPS — Input/Output Operations Per Second
IOPS measures storage performance in terms of read/write operations per second. It is a key metric for sizing storage for profiles and apps.

## KFM — Known Folder Move
Known Folder Move redirects user profile folders (like Desktop and Documents) to OneDrive. It improves data protection and roaming across devices.

## KQL — Kusto Query Language
KQL is the query language used in Azure Monitor and Log Analytics. It is optimized for exploring time-series and log data.

## M365 — Microsoft 365
Microsoft 365 is the cloud productivity suite including Office apps, security, and identity services. It provides licensing for apps used in virtual desktops.

## MECM — Microsoft Endpoint Configuration Manager
MECM (formerly SCCM) is Microsoft’s on-premises endpoint management platform. It manages software deployment, updates, and device compliance.

## MFA — Multi-Factor Authentication
MFA requires two or more verification methods for sign-in. It reduces the risk of credential compromise.

## MSIX — MSIX app package format
MSIX is a Windows app packaging format that improves reliability and security. It supports clean installs, app attach, and simplified updates.

## MSTSC — Microsoft Terminal Services Client
MSTSC is the legacy Remote Desktop client in Windows. It is used to connect to RDP endpoints and AVD session hosts.

## NFS — Network File System
NFS is a file sharing protocol commonly used in Unix/Linux environments. Azure NetApp Files supports NFS for Linux workloads.

## NSG — Network Security Group
NSGs are Azure firewall rules applied to subnets or NICs. They allow or deny inbound and outbound network traffic.

## NTFS — New Technology File System
NTFS is the Windows file system that supports permissions, encryption, and quotas. It is commonly used for profile and file shares.

## ODFC — Office Document Cache (FSLogix Office container)
ODFC is the FSLogix container that stores cached Office data, such as Outlook and OneDrive. It speeds up Office performance and roaming.

## OS — Operating System
The OS is the base software that manages hardware and provides services for applications. AVD session hosts typically run Windows 10/11 or Windows Server.

## P2S — Point-to-Site
Point-to-Site is a VPN connection from a single client to a virtual network. It is often used for remote access scenarios.

## PHS — Password Hash Synchronization
PHS syncs password hashes from on-premises AD to Microsoft Entra ID. It enables cloud authentication for hybrid identities.

## PKU2U — Peer-to-Peer Kerberos (PKU2U)
PKU2U is a Kerberos variant used for local and peer authentication scenarios. It enables authentication without a domain controller.

## PMK — Platform-Managed Key
PMK refers to encryption keys managed by the cloud provider. It provides encryption at rest without customer key management.

## PTA — Pass-Through Authentication
PTA validates user credentials against on-premises AD during sign-in. It allows cloud sign-in without storing password hashes in the cloud.

## RADC — RemoteApp and Desktop Connections
RADC is the legacy feed mechanism for remote apps and desktops. It is largely replaced by modern workspace feeds.

## RBAC — Role-Based Access Control
RBAC assigns permissions to users and groups based on roles. It provides least-privilege access to Azure resources.

## RDP — Remote Desktop Protocol
RDP is the protocol used to deliver remote desktop and app sessions. AVD relies on RDP for display, input, and device redirection.

## RDS — Remote Desktop Services
RDS is Windows Server’s on-premises remote desktop platform. AVD is the Azure cloud alternative to RDS.

## REST — Representational State Transfer
REST is an API architectural style using standard HTTP methods. Many Azure services expose REST APIs.

## RPO — Recovery Point Objective
RPO is the maximum acceptable data loss measured in time. It defines how far back you can restore data after an outage.

## RTO — Recovery Time Objective
RTO is the maximum acceptable downtime before services must be restored. It drives failover and recovery planning.

## RTT — Round-Trip Time
RTT measures network latency between client and server. It is a key factor for AVD performance and user experience.

## S2S — Site-to-Site
Site-to-Site is a VPN connection between networks, such as on-premises and Azure. It enables private connectivity for hybrid deployments.

## SID — Security Identifier
A SID is a unique identifier for security principals in Windows. It is used internally for permissions and access control.

## SMB — Server Message Block
SMB is the Windows file sharing protocol. FSLogix profile containers are typically stored on SMB shares.

## SPN — Service Principal Name
An SPN uniquely identifies a service instance for Kerberos authentication. It is required for secure service-to-service authentication.

## SSD — Solid-State Drive
SSD is flash-based storage with low latency and high throughput. It is faster and more expensive than HDD storage.

## SSE — Storage Service Encryption
SSE provides encryption at rest for Azure Storage. It is enabled by default and can use PMKs or CMKs.

## SSH — Secure Shell
SSH is a secure protocol for remote administration of Linux systems. It is commonly used for managing Azure Linux VMs.

## SSO — Single Sign-On
SSO lets users access multiple apps with one set of credentials. It improves user experience and security posture.

## STUN — Session Traversal Utilities for NAT
STUN helps discover public-facing IP and ports for NAT traversal. It is commonly used in real-time communications.

## TCP — Transmission Control Protocol
TCP is a reliable, connection-oriented transport protocol. RDP commonly uses TCP for session transport.

## TLS — Transport Layer Security
TLS encrypts network traffic between endpoints. It is used to secure RDP, web services, and APIs.

## TURN — Traversal Using Relays around NAT
TURN relays traffic when direct NAT traversal is not possible. It is used in real-time media scenarios.

## UDP — User Datagram Protocol
UDP is a low-latency transport protocol. RDP Shortpath uses UDP for improved performance.

## UPN — User Principal Name
UPN is a user identifier in the form user@domain. It is commonly used for sign-in in Entra ID and AD.

## URL — Uniform Resource Locator
A URL is the address of a web resource. AVD and Azure services require access to specific URLs.

## USB — Universal Serial Bus
USB is a hardware interface standard for peripherals. AVD can redirect USB devices with policy controls.

## VDI — Virtual Desktop Infrastructure
VDI is the hosting of desktop OS instances in a centralized environment. AVD is Microsoft’s cloud VDI service.

## VDHX — Virtual Hard Disk v2 (typo for VHDX in notes)
VDHX appears in the notes as a variant of VHDX. The correct format is VHDX, the modern virtual disk format.

## VHD — Virtual Hard Disk
VHD is the legacy virtual disk format used by Hyper-V. It supports smaller disk sizes than VHDX.

## VHDX — Virtual Hard Disk v2
VHDX is the modern Hyper-V virtual disk format. It supports larger disks and improved resilience.

## VM — Virtual Machine
A VM is a software-defined computer running an OS and apps. AVD session hosts are Azure VMs.

## VPN — Virtual Private Network
VPN provides encrypted tunnels over public networks. It is used to connect users or sites to Azure securely.

## VSM — Virtual Secure Mode
VSM is a Windows security feature that isolates sensitive processes. It supports features like credential guard.

## VSS — Volume Shadow Copy Service
VSS is a Windows service that creates consistent snapshots of volumes. Azure Backup uses VSS for app-consistent backups.

## WSUS — Windows Server Update Services
WSUS is Microsoft’s on-premises update management service. It distributes and manages Windows updates.

## WVD — Windows Virtual Desktop (former name of AVD)
WVD was the original name of Azure Virtual Desktop. It refers to the same service prior to the rebrand.

## ZRS — Zone-Redundant Storage
ZRS replicates data across multiple availability zones in a region. It improves resilience against datacenter failures.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
- [[AZ-140T00A-ENU-Powerpoint_09]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_08_Script]]
- [[AZ-140T00A-ENU-Powerpoint_05_Script]]
