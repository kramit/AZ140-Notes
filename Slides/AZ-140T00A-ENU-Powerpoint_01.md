# AZ-140T00A-ENU-Powerpoint_01.pptx

## Slide 1-2: Azure Virtual Desktop Architecture
- Azure Virtual Desktop service architecture and resilience: https://learn.microsoft.com/en-us/azure/virtual-desktop/service-architecture-resilience

Instructor Notes: Azure Virtual Desktop service architecture and resilience  
Overview: Azure Virtual Desktop (AVD) is a Microsoft-managed control plane that brokers user connections to customer-managed session hosts, designed for global resiliency and secure access.  
Key points:
- Core control-plane services include web service, broker, gateway, resource directory, and geographical database.
- User connections involve feed discovery and RDP connection orchestration through Azure Front Door and regional gateways.
- Resilience comes from multi-region service distribution and redundant instances of control-plane services.

- Azure Virtual Desktop for the enterprise (architecture): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#architecture

Instructor Notes: Azure Virtual Desktop for the enterprise (architecture)  
Overview: The reference architecture shows the split between Microsoft-managed services and customer-managed resources and how traffic flows from clients to session hosts.  
Key points:
- Microsoft manages web access, gateway, broker, diagnostics, and extensibility (APIs/PowerShell).
- Customers manage host pools, session hosts, identity, networks, and storage (Azure Files/ANF).
- Typical designs include hub-spoke VNets and on-premises connectivity via VPN/ExpressRoute.

## Slide 3: Introduction (topic map)
- Azure Virtual Desktop for the enterprise: https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop

Instructor Notes: Azure Virtual Desktop for the enterprise  
Overview: AVD is an Azure-native VDI platform with Microsoft-managed brokering and customer-managed compute, identity, and network resources.  
Key points:
- Provides desktop/app virtualization without running gateway servers.
- Supports broad enterprise use cases (security, remote workforce, specialized workloads).
- Design considerations emphasize security, cost optimization, and scalability.

- Azure Virtual Desktop components (managed and customer-managed): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#architecture

Instructor Notes: Azure Virtual Desktop components  
Overview: The architecture separates the control plane (Microsoft-managed) from the data plane (customer-managed).  
Key points:
- Microsoft-managed: web access, gateway, broker, diagnostics, extensibility APIs.
- Customer-managed: VNets, identity integration, session hosts, storage for profiles.
- This split drives shared-responsibility and operational planning.

- Personal and pooled desktops (host pools): https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology

Instructor Notes: Host pools (personal vs pooled)  
Overview: Host pools are collections of session hosts; personal pools map users to specific VMs, pooled pools share VMs across users.  
Key points:
- Personal pools provide persistent desktops; pooled pools optimize cost and density.
- Pooled host pools use load-balancing algorithms and require profile roaming (FSLogix).
- Choose host pool type based on workload consistency and user experience needs.

- Service updates for Azure Virtual Desktop (Windows servicing): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#windows-servicing

Instructor Notes: Windows servicing options  
Overview: AVD session hosts can be patched using enterprise tooling or by refreshing images on a schedule.  
Key points:
- Options include MECM, Windows Update for Business, Azure Update Management, and image refresh.
- Image-based updates are recommended for consistent, compliant pools.
- Use Azure Monitor/Log Analytics to track update compliance.

- Azure Virtual Desktop service limits: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-virtual-desktop-service-limits

Instructor Notes: Service limits  
Overview: AVD has specific object limits per tenant/workspace/host pool that affect scaling plans.  
Key points:
- Limits include workspaces, host pools, app groups, RemoteApps, and session hosts.
- Capacity planning should consider Azure subscription quotas as well.
- Use limits early in design to avoid re-architecture later.

- Session host VM sizing guidelines: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/session-host-virtual-machine-sizing-guidelines

Instructor Notes: Session host sizing guidelines  
Overview: Sizing guidance provides baseline vCPU/RAM/storage recommendations by workload type and session model.  
Key points:
- Multi-session hosts need more resources due to higher concurrency.
- Workload types (light/medium/heavy/power) drive sizing and density.
- Use guidelines as a starting point, then validate with real workload testing.

- Pricing and cost optimization considerations: https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#considerations

Instructor Notes: Pricing and cost optimization  
Overview: Cost optimization focuses on multi-session, licensing benefits, and reserved capacity.  
Key points:
- Windows Enterprise multi-session reduces per-user compute costs.
- Azure Hybrid Benefit and Reservations can significantly reduce VM costs.
- Cost controls include right-sizing and scaling plans.

## Slide 4-6: Azure Virtual Desktop for the enterprise and use cases
- Azure Virtual Desktop overview: https://learn.microsoft.com/en-us/azure/virtual-desktop/overview

Instructor Notes: Azure Virtual Desktop overview  
Overview: AVD provides scalable desktop and app virtualization with Microsoft-managed control-plane services.  
Key points:
- Supports full desktops and RemoteApp delivery.
- Access via Windows App/Remote Desktop clients or web client.
- Managed brokering removes the need to deploy gateway/broker servers.

- Azure Virtual Desktop for the enterprise (use cases and considerations): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop

Instructor Notes: Enterprise use cases and considerations  
Overview: AVD addresses regulated industries, remote work, and specialized workloads with centralized control.  
Key points:
- Use cases include compliance-heavy industries, contractors, and BYOD.
- Security best practices include Entra MFA and private networking.
- Architecture emphasizes shared responsibility between Microsoft and the customer.

## Slide 7-9: Azure Virtual Desktop components
- Components Microsoft manages (web access, gateway, connection broker, diagnostics, extensibility): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#architecture

Instructor Notes: Microsoft-managed components  
Overview: The control plane provides brokering, access, and diagnostics at scale.  
Key points:
- Web access provides HTML5 access and feed discovery.
- Gateway brokers RDP connectivity; broker manages session placement and reconnection.
- Diagnostics aggregates events; extensibility includes REST APIs and PowerShell.

- Azure Virtual Network overview: https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview

Instructor Notes: Azure Virtual Network  
Overview: VNets provide private connectivity between session hosts and other resources, and to on-premises networks.  
Key points:
- VNets support subnetting, routing, NSGs, and peering.
- On-prem connectivity uses VPN or ExpressRoute.
- VNet design is critical for AVD performance and security.

- Microsoft Entra ID overview: https://learn.microsoft.com/en-us/entra/fundamentals/whatis

Instructor Notes: Microsoft Entra ID  
Overview: Entra ID provides identity, access management, and security controls for AVD.  
Key points:
- Supports Conditional Access and MFA.
- Integrates with on-prem AD via Entra Connect when needed.
- Centralizes user and group assignments for access control.

- Host pools and session hosts: https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology

Instructor Notes: Host pools and session hosts  
Overview: Host pools contain session host VMs registered to AVD; app groups publish resources to users.  
Key points:
- Session hosts are the VMs users connect to for desktops/apps.
- Host pools define pooled or personal behavior and load balancing.
- App groups control what users see (desktop vs RemoteApp).

## Slide 10-12: Personal and pooled desktops, host pools, app groups
- Host pools (personal vs pooled): https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology#host-pools

Instructor Notes: Personal vs pooled host pools  
Overview: Personal pools provide a 1:1 user-to-VM mapping; pooled pools share hosts across users.  
Key points:
- Personal pools offer persistence; pooled pools improve cost efficiency.
- Pooled pools require a load-balancing algorithm and max session limits.
- FSLogix is recommended for pooled profiles.

- Application groups: https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology#application-groups

Instructor Notes: Application groups  
Overview: Application groups determine which desktops or apps are visible to users.  
Key points:
- Two types: Desktop and RemoteApp.
- A host pool can have one Desktop app group and multiple RemoteApp groups.
- Preferred app group type controls what users see when assigned to both.

- Host pool load balancing (breadth-first, depth-first): https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-load-balancing

Instructor Notes: Load balancing algorithms  
Overview: Load balancing selects which session host receives new user sessions in pooled pools.  
Key points:
- Breadth-first distributes users across hosts for performance.
- Depth-first packs users onto fewer hosts for cost optimization.
- Max session limits are required for depth-first.

## Slide 13-14: Service updates for Azure Virtual Desktop
- Windows servicing options (MECM, Windows Update for Business, Azure Update Management, Log Analytics, custom image): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop#windows-servicing

Instructor Notes: Servicing options summary  
Overview: AVD supports multiple enterprise update methods; image refresh is common for consistency.  
Key points:
- Choose the tool based on OS type and organizational tooling.
- Image-based patching ensures consistent session host state.
- Monitoring verifies compliance and update success.

- Microsoft Endpoint Configuration Manager (MECM): https://learn.microsoft.com/en-us/mem/configmgr

Instructor Notes: MECM  
Overview: MECM provides enterprise-scale OS and app update management for Windows clients and servers.  
Key points:
- Centralized patching and reporting.
- Fits organizations already using Configuration Manager.
- Common for traditional Windows servicing models.

- Windows Update for Business: https://learn.microsoft.com/en-us/windows/deployment/update/waas-manage-updates-wufb

Instructor Notes: Windows Update for Business  
Overview: WUfB is a cloud-managed Windows update model that uses update rings and policies.  
Key points:
- Controls deferrals and update cadence without WSUS.
- Suitable for Windows 10/11 multi-session.
- Integrates with Intune and group policy.

- Azure Update Management: https://learn.microsoft.com/en-us/azure/automation/update-management/overview

Instructor Notes: Azure Update Management  
Overview: Update Management (Azure Automation) coordinates patching for Windows and Linux VMs.  
Key points:
- Central patch orchestration with scheduling.
- Compliance reporting across VM fleets.
- Common for server-based session hosts.

- Azure Log Analytics (Azure Monitor Logs): https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-overview

Instructor Notes: Azure Log Analytics  
Overview: Log Analytics centralizes log collection and query for operational insights.  
Key points:
- Ingests diagnostics from AVD and session hosts.
- KQL enables troubleshooting and compliance checks.
- Often used with AVD Insights.

- Capture a custom managed image: https://learn.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource

Instructor Notes: Custom managed images  
Overview: Managed images capture a standardized VM state for repeatable session host deployment.  
Key points:
- Use sysprep to generalize images before capture.
- Store in Azure and reuse across host pools.
- Foundation for image-based patching and consistency.

## Slide 15-16: Azure Virtual Desktop limitations
- Azure Virtual Desktop service limits table: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-virtual-desktop-service-limits

Instructor Notes: AVD service limits  
Overview: The service has defined limits for objects and assignments that impact scaling design.  
Key points:
- Limits apply to workspaces, host pools, app groups, RemoteApps, roles, and session hosts.
- Exceeding limits can require support requests or multi-tenant design.
- Track limits during growth to avoid operational blockers.

## Slide 17-18: Virtual machine sizing
- Session host virtual machine sizing guidelines: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/session-host-virtual-machine-sizing-guidelines

Instructor Notes: VM sizing for session hosts  
Overview: Sizing is workload-driven; multi-session density and performance trade-offs must be tested.  
Key points:
- Use workload categories to estimate baseline resources.
- Favor more smaller VMs over fewer large VMs for flexibility.
- Validate with pilot tests and adjust based on metrics.

## Slide 19-20: Azure Virtual Desktop pricing and cost drivers
- Windows Enterprise multi-session overview: https://learn.microsoft.com/en-us/azure/virtual-desktop/windows-multisession-faq

Instructor Notes: Windows Enterprise multi-session  
Overview: Multi-session enables multiple concurrent users on Windows 10/11 Enterprise, reducing cost per user.  
Key points:
- Exclusive to AVD and approved providers.
- User density depends on workload and VM size.
- Supports pooled host pool scenarios.

- Azure Hybrid Benefit for Windows Server: https://learn.microsoft.com/en-us/azure/virtual-machines/windows/hybrid-use-benefit-licensing

Instructor Notes: Azure Hybrid Benefit  
Overview: Reuses on-prem Windows Server licenses to reduce Azure compute costs.  
Key points:
- Requires Software Assurance or eligible subscriptions.
- Applies to Windows Server VMs used as session hosts.
- Often combined with reservations for additional savings.

- Azure Reservations (Reserved VM Instances): https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/save-compute-costs-reservations

Instructor Notes: Azure Reservations  
Overview: Reserved instances reduce VM costs with 1- or 3-year commitments.  
Key points:
- Discounts apply to eligible VM usage.
- Best for steady-state workloads.
- Pair with Hybrid Benefit for higher savings.

- Load-balancing modes for cost optimization: https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-load-balancing

Instructor Notes: Load balancing for cost  
Overview: Load balancing affects how efficiently session host capacity is used.  
Key points:
- Depth-first maximizes utilization for cost savings.
- Breadth-first favors user experience and performance.
- Switch based on business priorities and peak usage.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
- [[AZ-140T00A-ENU-Powerpoint_06]]
- [[overview]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_06_Script]]
