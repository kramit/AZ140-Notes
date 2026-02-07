# AZ-140T00A-ENU-Powerpoint_03.pptx

## Slide 4-7: Licensing model and personal vs multi-session
- Licensing Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/licensing

Instructor Notes: Licensing overview  
Overview: Licensing depends on OS type (Windows client vs Windows Server) and internal vs external use.  
Key points:
- Windows 10/11 Enterprise multi-session is supported with eligible M365/Windows licenses.
- Windows Server requires RDS CALs with Software Assurance.
- External users can use per-user access pricing where applicable.

- Azure Virtual Desktop terminology (host pools/personal vs pooled): https://learn.microsoft.com/en-us/azure/virtual-desktop/terminology#host-pools

Instructor Notes: Personal vs pooled desktops  
Overview: Host pool type drives user experience, cost, and profile strategy.  
Key points:
- Personal pools map a user to a dedicated VM (persistent).
- Pooled pools share session hosts for higher density.
- Pooled pools typically require FSLogix profile roaming.

## Slide 8-9: FSLogix profile containers
- User profile management for Azure Virtual Desktop with FSLogix profile containers: https://learn.microsoft.com/en-us/azure/virtual-desktop/fslogix-profile-containers

Instructor Notes: FSLogix profile containers  
Overview: FSLogix stores the full user profile in a VHD/VHDX to enable roaming across sessions.  
Key points:
- Profiles attach at sign-in and appear like local profiles.
- Improves performance and supports non-persistent desktops.
- Recommended for pooled host pools.

- Storage options for FSLogix profile containers: https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile

Instructor Notes: FSLogix storage options  
Overview: Azure Files is the recommended storage option for most AVD profiles.  
Key points:
- SMB file shares are required.
- Azure Files and Azure NetApp Files are common choices.
- Storage should be in the same region as session hosts.

## Slide 10-15: Desktop client deployment and RDP
- Connect to Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/connect-azure-virtual-desktop

Instructor Notes: Client connectivity  
Overview: Users access AVD via Windows App or Remote Desktop clients across platforms.  
Key points:
- Windows App is the preferred client for AVD.
- Supports Windows, macOS, iOS/iPadOS, Android, and web.
- Admins must publish desktops/apps for users to see resources.

- Prerequisites for Azure Virtual Desktop (connecting to a remote session): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#connecting-to-a-remote-session

Instructor Notes: Client requirements  
Overview: AVD requires supported clients and allowed URLs for connectivity.  
Key points:
- Windows App or Remote Desktop client is required.
- RADC and MSTSC are not supported.
- Ensure firewall allows required FQDNs.

- What is Windows App?: https://learn.microsoft.com/en-us/windows-app/overview

Instructor Notes: Windows App overview  
Overview: Windows App consolidates access to AVD and other Windows cloud services.  
Key points:
- Single app experience across platforms and browsers.
- Supports multiple accounts and device redirection.
- Recommended replacement for legacy clients.

- Remote Desktop Protocol (RDP) bandwidth requirements: https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth

Instructor Notes: RDP planning  
Overview: RDP adapts to conditions but needs adequate bandwidth for rich workloads.  
Key points:
- Graphics workloads drive the most bandwidth.
- Resolution and frame rate significantly impact requirements.
- Monitor real sessions to validate sizing.

## Slide 16-21: Hybrid identity and Microsoft Entra Connect
- What is Microsoft Entra Connect?: https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect

Instructor Notes: Entra Connect overview  
Overview: Entra Connect syncs identities and enables hybrid sign-in options.  
Key points:
- Synchronizes users, groups, and password hashes.
- Supports PHS, PTA, and federation options.
- Central tool for hybrid identity configuration.

- Hybrid scenarios (PHS, PTA, Federation): https://learn.microsoft.com/en-us/entra/identity/hybrid/common-scenarios

Instructor Notes: Hybrid authentication methods  
Overview: Three primary methods support hybrid identity with SSO options.  
Key points:
- PHS is simplest and cloud-resilient.
- PTA validates passwords on-prem via agents.
- Federation uses AD FS and is most complex.

- Choose the right authentication method for your Microsoft Entra hybrid identity solution: https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn

Instructor Notes: Choosing PHS vs PTA vs Federation  
Overview: Selection depends on security, infrastructure, and resiliency needs.  
Key points:
- PHS is recommended for most organizations.
- PTA avoids password hashes in cloud but needs agents.
- Federation is for advanced requirements and existing AD FS.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_10]]
- [[AZ-140T00A-ENU-Powerpoint_11]]
- [[FSLogix Overview]]
- [[AZ-140T00A-ENU-Powerpoint_05]]
