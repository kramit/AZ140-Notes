# AZ-140T00A-ENU-Powerpoint_02.pptx

## Slide 4-7: Network bandwidth, latency, and RTT planning
- Remote Desktop Protocol (RDP) bandwidth requirements: https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth

Instructor Notes: RDP bandwidth requirements  
Overview: RDP adapts to network conditions, but user experience depends on available bandwidth and workload type.  
Key points:
- Bandwidth varies by graphics intensity, resolution, and frame rate.
- Use workload-based estimates (light/medium/heavy/power) as starting points.
- Monitor real sessions to validate assumptions before scaling.

- Azure Virtual Desktop network topology and connectivity design guidance (Experience Estimator and RTT): https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/azure-virtual-desktop/eslz-network-topology-and-connectivity#avd-networking-recommendations

Instructor Notes: Experience Estimator and RTT planning  
Overview: The Experience Estimator provides RTT samples to help pick the best Azure region for session hosts.  
Key points:
- Place session hosts close to users to reduce RTT and improve UX.
- RTT under ~150 ms is generally a good target for responsiveness.
- Re-evaluate latency periodically as regions expand.

- Prerequisites for Azure Virtual Desktop (network and latency guidance): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#network

Instructor Notes: AVD network prerequisites  
Overview: AVD requires outbound connectivity to the service and appropriate VNet/DNS setup.  
Key points:
- Session hosts need a VNet in the same region and DNS connectivity to identity.
- Users and hosts connect to the service over TCP 443.
- RTT to the host pool region should be kept low for performance.

## Slide 8-10: OS recommendation and client choices
- Prerequisites for Azure Virtual Desktop (operating systems and licenses): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#operating-systems-and-licenses

Instructor Notes: Supported OS for session hosts  
Overview: AVD supports specific Windows client and server OS images with defined licensing.  
Key points:
- Windows 10/11 Enterprise multi-session is supported for pooled hosts.
- Windows Server is supported with RDS CAL requirements.
- Choose OS based on workload needs and licensing entitlement.

- Connect to Azure Virtual Desktop (Windows App and clients): https://learn.microsoft.com/en-us/azure/virtual-desktop/connect-azure-virtual-desktop

Instructor Notes: Client options  
Overview: Users connect via Windows App or Remote Desktop clients on supported platforms.  
Key points:
- Windows App is the recommended client for AVD.
- Multiple platform options: Windows, macOS, iOS/iPadOS, Android, web.
- Client choice impacts feature support and device redirection.

- What is Windows App?: https://learn.microsoft.com/en-us/windows-app/overview

Instructor Notes: Windows App overview  
Overview: Windows App is the modern gateway for AVD, Windows 365, and Dev Box.  
Key points:
- Single app to access desktops and apps across services.
- Available on major OS platforms and web browsers.
- Designed for secure, streamlined connectivity.

## Slide 11-13: Load balancing methods
- Configure host pool load balancing in Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-load-balancing

Instructor Notes: Breadth-first vs depth-first  
Overview: Load balancing controls how new sessions are distributed across pooled hosts.  
Key points:
- Breadth-first spreads users to improve performance.
- Depth-first packs users to reduce costs.
- Max session limits are required for depth-first.

## Slide 14-15: Subscriptions and management groups
- Elevate access to manage all Azure subscriptions and management groups: https://learn.microsoft.com/en-us/azure/role-based-access-control/elevate-access-global-admin

Instructor Notes: Elevate access for Global Administrators  
Overview: Global Admins can temporarily elevate access to manage all subscriptions and management groups.  
Key points:
- Grants User Access Administrator at root scope.
- Use for recovery, auditing, or broad access changes.
- Remove elevated access after completing required tasks.

- What are Azure management groups?: https://learn.microsoft.com/en-us/azure/governance/management-groups/overview

Instructor Notes: Management groups basics  
Overview: Management groups provide hierarchical governance across subscriptions.  
Key points:
- Root management group is the top-level container.
- Policies and RBAC can be applied at group scope.
- New subscriptions inherit governance from the hierarchy.

## Slide 16-17: Metadata location and geography
- Data locations for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/data-locations

Instructor Notes: AVD metadata and geography  
Overview: AVD stores service metadata in the geography of the selected region.  
Key points:
- Host pools, app groups, and workspaces have a metadata location.
- Metadata location is separate from session host VM location.
- Data residency depends on the selected geography.

- Prerequisites for Azure Virtual Desktop (regions that store metadata): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#azure-regions

Instructor Notes: Supported metadata regions  
Overview: Only certain Azure regions can host AVD service metadata.  
Key points:
- Host pools, workspaces, and app groups must be in supported regions.
- Session hosts can run in any Azure region.
- Align related objects to the same metadata region.

## Slide 18-19: Performance requirements and monitoring
- Monitor Azure Virtual Machines (host vs guest metrics): https://learn.microsoft.com/en-us/azure/virtual-machines/monitor-vm#overview-monitor-vm-host-and-guest-metrics-and-logs

Instructor Notes: Host vs guest monitoring  
Overview: Host metrics are automatic; guest metrics require the Azure Monitor agent.  
Key points:
- Host metrics include CPU, disk, and network at the hypervisor level.
- Guest metrics give OS and app insights, requiring AMA + DCR.
- Use guest metrics for capacity planning and troubleshooting.

- Create diagnostic settings in Azure Monitor: https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/create-diagnostic-settings

Instructor Notes: Diagnostic settings  
Overview: Diagnostic settings route platform metrics and logs to Log Analytics or storage.  
Key points:
- Enables central log analytics and alerting.
- Choose destinations based on operational needs.
- Helps standardize monitoring across host pools.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_06]]
- [[overview]]
- [[AZ-140T00A-ENU-Powerpoint_03]]
- [[AZ-140T00A-ENU-Powerpoint_04]]
