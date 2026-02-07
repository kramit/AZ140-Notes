# AZ-140T00A-ENU-Powerpoint_06.pptx

## Slide 4-8: Prerequisites, operating systems, and regions
- Prerequisites for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites

Instructor Notes: AVD prerequisites  
Overview: Deployment requires supported identity, OS, network, and subscription readiness.  
Key points:
- Supported identity providers include Entra ID and AD DS scenarios.
- Session hosts must use supported OS images and licensing.
- Network and URL requirements must be met.

- Prerequisites for Azure Virtual Desktop (Azure regions for metadata): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#azure-regions

Instructor Notes: Metadata regions  
Overview: Host pools, app groups, and workspaces must be created in supported metadata regions.  
Key points:
- Metadata location is separate from session host location.
- Keep related objects in the same metadata region.
- Session hosts can be deployed in any Azure region.

## Slide 9-11: Network and client planning
- Prerequisites for Azure Virtual Desktop (network): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#network

Instructor Notes: Network planning  
Overview: Session hosts need VNet/DNS connectivity and outbound access to AVD service endpoints.  
Key points:
- VNet must be in the same region as session hosts.
- Domain connectivity is required for AD DS/Entra DS joins.
- Outbound TCP 443 to required URLs is mandatory.

- Prerequisites for Azure Virtual Desktop (connecting to a remote session): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#connecting-to-a-remote-session

Instructor Notes: Client requirements  
Overview: Users connect using Windows App or Remote Desktop clients on supported platforms.  
Key points:
- RADC and MSTSC are not supported.
- Ensure client platform support and required URLs.
- Windows App is the recommended client.

## Slide 12-14: Create host pools (pooled and personal)
- Deploy Azure Virtual Desktop (create host pools): https://learn.microsoft.com/en-us/azure/virtual-desktop/deploy-azure-virtual-desktop

Instructor Notes: Host pool creation  
Overview: Host pools define how session hosts are managed and how users connect.  
Key points:
- Choose pooled or personal host pool type.
- Configure load balancing and preferred app group type.
- Host pools can be created via portal, CLI, or PowerShell.

- Azure Virtual Desktop terminology (host pool types): https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology#host-pools

Instructor Notes: Host pool types  
Overview: Personal host pools map users to dedicated VMs; pooled host pools share VMs.  
Key points:
- Personal pools are persistent for the user.
- Pooled pools optimize density and cost.
- Load balancing applies to pooled pools.

## Slide 15-16: Apply Windows licenses to session hosts
- Apply a Windows license to session host virtual machines: https://learn.microsoft.com/en-us/azure/virtual-desktop/apply-windows-license

Instructor Notes: Session host licensing  
Overview: Apply appropriate Windows/Windows Server licensing to session hosts.  
Key points:
- Licensing can be auto-applied when created via AVD.
- Custom images may require manual license application.
- Windows Server session hosts need RDS CALs.

## Slide 17-18: Add session hosts to a host pool
- Add session hosts to a host pool: https://learn.microsoft.com/en-us/azure/virtual-desktop/add-session-hosts-host-pool

Instructor Notes: Adding session hosts  
Overview: Session hosts join a host pool using a registration key.  
Key points:
- Registration keys are per host pool and time-bound.
- Use portal, CLI, or PowerShell to add hosts.
- Keep host configuration consistent within a pool.

## Slide 19-20: Customize RDP properties
- Set custom RDP properties on a host pool: https://learn.microsoft.com/en-us/azure/virtual-desktop/customize-rdp-properties

Instructor Notes: Custom RDP properties  
Overview: RDP properties control client behavior (monitors, redirection, audio, etc.).  
Key points:
- Set via portal or `Update-AzWvdHostPool`.
- Properties are semicolon-separated key-value pairs.
- Users must refresh resources to receive updates.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_06_Script]]
- [[overview]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_11]]
