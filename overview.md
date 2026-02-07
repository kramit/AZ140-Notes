# Azure Virtual Desktop (AVD) Overview and Initial Setup

Azure Virtual Desktop is a comprehensive desktop and application virtualization service that runs on Azure. It allows organizations to deliver a full Windows desktop experience to users from anywhere, on any device, while maintaining security and compliance.

This guide mirrors the common AZ-140 module flow so your notes align to the course sequence while still describing a simple, first-time AVD deployment. Each component includes what it does and why it is needed.

## AVD Architecture Overview

AVD uses a **shared responsibility model** where Microsoft manages the control plane (Web Access, Gateway, Connection Broker, Diagnostics) and you manage the data plane (Session hosts, networking, identity, storage).

### Microsoft-Managed Components (Control Plane)
- **Web Access**: HTML5 browser-based portal for accessing desktops and apps
- **Gateway**: Remote Desktop Protocol (RDP) connectivity service  
- **Connection Broker**: Session orchestration and load balancing
- **Diagnostics**: Event logging and monitoring
- **Extensibility APIs**: REST APIs and PowerShell for management

### Customer-Managed Components (Data Plane)
- Identity and access (Microsoft Entra ID, AD DS)
- Virtual networking
- Session host virtual machines
- Storage for profiles and data
- All configuration and security policies

## Module 1: Plan an Azure Virtual Desktop architecture

### Identity and Access
- **Microsoft Entra ID (Azure AD)**
  - **What it does:** Authenticates users and admins; provides identity and access management.
  - **Why needed:** AVD uses Entra ID for sign-in, conditional access, MFA, and Intelligent Security Graph integration.
  - **Setup note:** Can be hybrid with on-premises AD DS using Azure AD Connect for seamless integration.

- **Active Directory Domain Services (AD DS / Azure AD DS / Entra ID Joined)**
  - **What it does:** Provides domain join, Group Policies, and profile management.
  - **Why needed:** Enterprise deployments require domain services for centralized policy management, user authentication, and integration with existing infrastructure.
  - **Options:**
    - **On-premises AD DS** (hybrid with Entra ID via Azure AD Connect)
    - **Microsoft Entra Domain Services** (managed in Azure)
    - **Entra ID joined** (newer option for modern deployments)

### Networking
- **VNet and Subnet**
  - **What it does:** Hosts session host VMs and provides isolated network connectivity.
  - **Why needed:** Session hosts must communicate securely with domain services, storage, and applications. Can connect to on-premises via VPN or Azure ExpressRoute.
  - **Considerations:**
    - Should support expected number of session hosts
    - Network Security Groups (NSGs) control inbound/outbound traffic
    - No inbound RDP ports required (uses Reverse Connect architecture)

- **DNS**
  - **What it does:** Resolves domain services, internal resources, and Azure services.
  - **Why needed:** Required for domain join, service discovery, and reliable access to internal resources.
  - **Setup note:** Point to AD DS DNS servers for domain services resolution

### Storage
- **File Share for User Profiles (FSLogix)**
  - **What it does:** Stores FSLogix profile containers as VHD/VHDX files.
  - **Why needed:** 
    - Ensures fast logons across pooled session hosts
    - Provides profile consistency and roaming
    - Reduces local disk requirements
  - **Options:**
    - Azure Files with SMB shares
    - Azure NetApp Files (for high-performance requirements)
  - **Key benefit:** Critical for multi-session host pools to avoid profile bloat

### Host Pool Strategy
- **Pooled vs Personal Host Pools**
  - **Pooled hosts** (multi-session):
    - **What it does:** Multiple users share same VMs
    - **Why needed:** Cost-effective for general workforce, better resource utilization
    - **OS:** Windows 11/10 multi-session or Windows Server
  
  - **Personal hosts** (single-session):
    - **What it does:** Each user assigned dedicated VM
    - **Why needed:** Better isolation, compliance requirements, power users with specific app needs
    - **OS:** Windows 11/10 Enterprise or Windows Server

- **Session Host Operating System**
  - **Windows 11 Enterprise (multi-session or single-session)**
    - Latest OS, better performance, modern security features
  - **Windows 10 Enterprise (multi-session or single-session)**
    - Proven stability, wide application compatibility
  - **Windows Server 2022 / 2019**
    - For application servers, terminal server scenarios, higher density
  - **Why it matters:** Determines concurrency limits, application compatibility, licensing costs, and support lifecycle

## Module 2: Implement an Azure Virtual Desktop infrastructure

### Core AVD Objects

- **Host Pool**
  - **What it does:** A logical grouping of similar session hosts that provides connection settings and load-balancing rules.
  - **Why needed:** 
    - Organizes and manages session hosts
    - Enables load balancing to distribute user sessions
    - Controls connection behavior (single or multiple connections per user)
    - Supports scaling of resources
  - **Key properties:**
    - **Host pool type:** Pooled (multi-session) or Personal (single-session)
    - **Load balancing algorithm:** Breadth-first (spreads load) or Depth-first (fills each host)
    - **Max session limit:** Controls maximum concurrent sessions per host
    - **Location:** Where metadata is stored (must be in supported region)

- **Session Host VMs**
  - **What it does:** The Windows virtual machines that users actually connect to for their desktop/app experience.
  - **Why needed:** 
    - Provides the compute and storage for running user workloads
    - Hosts the desktop environment and applications
    - Must be domain-joined for enterprise authentication
  - **Critical requirements:**
    - Must be joined to Active Directory domain
    - Must have network connectivity to domain services and file storage
    - Should be sized appropriately for expected user density
    - Must be deployed in Azure region (can differ from host pool metadata region)
  - **Sizing considerations:**
    - **CPU:** Typically 2-4 vCPUs per VM for pooled scenarios
    - **Memory:** 4-8GB minimum, 8GB+ recommended for multi-session
    - **Storage:** 100GB+ OS disk, additional disk for applications
    - **User density:** 4-6 users per VM for light workloads, 2-3 for heavy workloads

- **Application Group**
  - **What it does:** A collection of resources (full desktops or specific applications) that are published together.
  - **Why needed:** 
    - Determines what users can launch
    - Provides granular access control
    - Can isolate different workloads or departments
  - **Types:**
    - **Desktop application group:** Users get full desktop experience (default)
    - **RemoteApp application group:** Users access only specific applications without full desktop
  - **Key feature:** Associates with a workspace to be discoverable by users

- **Workspace**
  - **What it does:** A logical container that holds application groups and serves as the user-facing entry point.
  - **Why needed:** 
    - Users see workspace where they discover assigned desktops and apps
    - Provides organizational grouping of resources
    - Enables per-workspace configuration
  - **Best practice:** One workspace per business unit or organization typically

### Load Balancing Methods

- **Breadth-First** (Recommended for most scenarios)
  - Distributes sessions evenly across session hosts
  - Minimizes resource contention
  - Better for power users and performance-sensitive applications

- **Depth-First** (Cost optimization)
  - Fills one session host completely before moving to next
  - Allows more hosts to be powered down, reducing costs
  - Suitable for light workloads and development/test environments

### Initial Build (Simple Lab / Small Deployment)

**Prerequisites:**
- Azure subscription with appropriate RBAC roles (Desktop Virtualization Contributor, Virtual Machine Contributor)
- Virtual Network and subnet configured
- Active Directory Domain Services available (on-premises or Azure AD DS)
- User accounts in AD DS / Entra ID

**Deployment Steps:**

1. Create a **resource group** in your chosen region.
2. Create a **VNet/subnet** and verify DNS settings for your directory service.
   - Ensure connectivity to domain controllers
   - Configure Network Security Groups for session host traffic
3. Create a **host pool** (pooled is typical for labs) with **breadth-first** load balancing.
   - Enable diagnostics settings to send logs to Log Analytics (recommended)
   - Configure validation environment if testing features
4. Deploy **1-2 session hosts** (Windows 11 multi-session is common for training).
   - Join to Active Directory domain during creation
   - Ensure VM size: 2-4 vCPUs, 8GB+ RAM minimum (Standard_D2s_v3 or similar)
   - Install AVD agent and Boot Loader agent automatically during creation
   - Verify connectivity to domain services and file storage
5. Create a **desktop application group** and associate it to the host pool.
   - Type: Desktop (full desktop experience)
   - Name: e.g., "General Access Desktop"
6. Create a **workspace** and register the application group.
   - Workspace makes resources discoverable to users
   - Name logically for your organization
7. Assign **test users** to the application group.
   - Add Azure AD users or AD DS security groups
   - Verify users can authenticate and connect

## Module 3: Manage access and security

### RBAC (Role-Based Access Control)
- **What it does:** Controls who administers AVD resources and what they can do.
- **Why needed:** Enforces least-privilege operations and security governance.
- **Key AVD-specific roles:**
  - **Desktop Virtualization Contributor:** Full management of AVD resources (host pools, workspaces, application groups)
  - **Desktop Virtualization User:** Assigned to end users for workspace access
  - **Desktop Virtualization Virtual Machine Contributor:** Manages session host VMs in host pool
  - **Virtual Machine Contributor:** Creates and manages individual VMs
  - **Desktop Virtualization Power User:** Limited administrative capabilities
- **Recommendation:** Assign roles at resource group scope for ease of management in labs

### User Assignment and Access Control
- **What it does:** Grants access to desktops and applications through application group membership.
- **Why needed:** Only assigned users can discover and launch resources.
- **Best practices:**
  - Assign Azure AD users or security groups (not individuals when possible)
  - Use Azure AD groups from on-premises AD DS for consistency
  - Regularly audit and clean up assignments
  - Use separate application groups for different user tiers (if needed)

### Security Features
- **Reverse Connect Architecture**
  - No inbound RDP ports required on session hosts
  - Reduces attack surface significantly
  - Sessions initiated from gateway, not client

- **Conditional Access and MFA**
  - **What it does:** Adds security controls at sign-in (Entra ID level).
  - **Why needed:** Protects against unauthorized access and credential compromise.
  - **Recommended for production:**
    - Require MFA for all users
    - Block sign-in from non-compliant devices
    - Require specific locations/networks for high-risk users
  - **Lab note:** Optional initially, implement before production

- **Network Security**
  - Use Network Security Groups (NSGs) to restrict outbound traffic from session hosts
  - Restrict management ports (RDP 3389, WinRM 5985/5986) to admin networks only
  - No need for public IPs on session hosts

## Module 4: Manage user environments and applications

### FSLogix (Profile Management)
- **What it does:** Redirects user profiles to VHD/VHDX containers stored on a file share.
- **Why needed:** 
  - Consistent profiles across pooled session hosts (critical for multi-session)
  - Much faster logon times (profile loaded from container, not created fresh)
  - Reduces local disk usage on session hosts
  - Enables user settings and application data to roam
- **Storage options:**
  - **Azure Files:** Simplest setup, works with SMB shares
  - **Azure NetApp Files:** High-performance option, better for large deployments
- **Implementation in simple setup:**
  - Create storage account with file share (Standard tier sufficient for labs)
  - Create service account for FSLogix access
  - Apply FSLogix configuration via Group Policy or script on session hosts

### Application Delivery Methods

- **Desktop Application Group** (Full Desktop Access)
  - Users see full Windows desktop
  - All applications visible and available
  - **When to use:** General workforce, development/test, users need various tools
  - Simpler initial deployment

- **RemoteApp Application Group** (Application-Only)
  - Users see only specific published applications
  - Applications appear as if running locally
  - **When to use:** Specific workloads, thin terminals, application-centric environments
  - Better resource utilization, security isolation
  
- **Hybrid Model**
  - Multiple application groups in same host pool
  - Different groups for different user tiers
  - Provides flexibility while maintaining cost control

## Module 5: Monitor and maintain AVD

### Diagnostics and Monitoring
- **What it does:** Sends logs, metrics, and events from AVD components to Log Analytics.
- **Why needed:** 
  - Troubleshooting connection and performance issues
  - Establishing performance baselines
  - Creating alerts for critical events
  - Compliance and audit tracking
- **Key metrics to monitor:**
  - Connection failures and success rates
  - Session host CPU, memory, disk usage
  - User login duration
  - Application response times
  - Gateway availability
- **Setup:** Enable diagnostics during host pool creation or after via portal

### Scaling and Updates
- **Scaling session hosts**
  - **Horizontal scaling:** Add/remove VMs based on demand
  - **Vertical scaling:** Change VM size for more/less resources
  - **Automation:** Use Azure Automation or Scheduled Scaling for predictable patterns
  - **Why needed:** Controls costs and ensures performance during peak usage

- **Image Management and Updates**
  - **OS patching:** Deploy Windows updates to session hosts monthly
  - **Application updates:** Keep published applications current
  - **Golden image approach:** Create updated image, re-deploy hosts
  - **Rolling updates:** Drain sessions, update, bring back online
  - **Why needed:** Security compliance, application stability, support lifecycle

### Backup and Disaster Recovery
- **Session host backup:** Azure Backup can protect VMs
- **Configuration backup:** Document host pool and app group settings
- **Profile backup:** FSLogix containers stored on backed-up file shares
- **Why needed:** Business continuity and data protection

---

## Prerequisites Checklist for Deployment

Before starting your AVD deployment, ensure you have:

**Subscription and Permissions:**
- [ ] Active Azure subscription
- [ ] Desktop Virtualization Contributor role
- [ ] Virtual Machine Contributor role
- [ ] Access to assign RBAC roles

**Networking:**
- [ ] Virtual Network created and DNS configured
- [ ] Subnets for session hosts and other resources
- [ ] Network Security Groups with appropriate rules
- [ ] Connectivity to domain controllers (on-premises or Azure AD DS)

**Identity:**
- [ ] Active Directory Domain Services (on-premises or Azure AD DS)
- [ ] Microsoft Entra ID tenant configured
- [ ] User accounts created in AD DS or Entra ID
- [ ] Azure AD Connect (if hybrid scenario)

**Storage (for FSLogix):**
- [ ] Storage account created (or will create during setup)
- [ ] File share for profile containers
- [ ] Service account for FSLogix access

**Regional Selection:**
- [ ] Chosen supported Azure region for host pool metadata
- [ ] Confirmed session host region availability

---

## Common Licensing Questions

**Do I need separate Windows licenses?**
- Windows 10/11 Enterprise multi-session and Windows Server 2022: License included with Microsoft 365 (formerly Office 365) or Azure subscription
- Use Azure Hybrid Benefit if you have existing volume licenses
- License automatically applied when using Azure Virtual Desktop service

**What about Office/Applications?**
- Microsoft 365 subscription handles Office 365 ProPlus licensing for users
- Other applications need appropriate licenses (CALs, subscriptions, etc.)

---

## Supported Azure Regions (Host Pool Metadata)

Host pool metadata must be stored in a supported region. Session hosts can be deployed to other regions. Check [Azure Virtual Desktop Prerequisites](https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#azure-regions) for current supported regions including:
- East US
- West US 2
- North Europe
- West Europe
- And others...

---

## Quick Reference: Component Relationships

```
Workspace
  ├─ Application Group (Desktop)
  │   ├─ Host Pool
  │   │   ├─ Session Host 1
  │   │   ├─ Session Host 2
  │   │   └─ Session Host N
  │   └─ Connected to VNet
  └─ Application Group (RemoteApp) [optional]
      └─ Same or different Host Pool
```

User → Workspace → Application Group → Host Pool → Session Host

---

## Minimal Lab Example (Quick Start)

**Resource List:**
- **Networking:** 1 VNet, 1 Subnet, NSG
- **Identity:** AD DS connection, test user account
- **Workspace:** 1 Workspace
- **Host Pool:** 1 Host Pool (Pooled, breadth-first load balancing)
- **Session Hosts:** 2 Session Hosts (Windows 11 multi-session, VM size: D2s_v3 or similar)
- **Application Group:** 1 Desktop application group
- **User Assignment:** Test user(s) assigned to application group
- **Storage:** Storage account with file share for FSLogix profiles

**Estimated Costs:**
- Session Hosts: ~$50-100/month each (based on VM sizing)
- Storage: ~$20-30/month (file share)
- Networking: ~$30-50/month
- **Total: ~$150-200/month for simple 2-host lab**

---

## Official References

- [Azure Virtual Desktop Overview](https://learn.microsoft.com/en-us/azure/virtual-desktop/overview)
- [Service Architecture and Resilience](https://learn.microsoft.com/en-us/azure/virtual-desktop/service-architecture-resilience)
- [Deployment Guide](https://learn.microsoft.com/en-us/azure/virtual-desktop/deploy-azure-virtual-desktop)
- [Prerequisites](https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites)
- [Security Recommendations](https://learn.microsoft.com/en-us/azure/virtual-desktop/security-recommendations)
- [Design Architecture (MS Learn)](https://learn.microsoft.com/en-us/training/modules/design-azure-virtual-desktop-architecture/)

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_06]]
- [[AZ-140T00A-ENU-Powerpoint_06_Script]]
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
- [[AZ-140T00A-ENU-Powerpoint_12_Script]]
