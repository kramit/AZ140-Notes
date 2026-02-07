# AZ-140T00A-ENU-Powerpoint_05.pptx

## Slide 4-5: FSLogix profile containers and storage planning
- User profile management for Azure Virtual Desktop with FSLogix profile containers: https://learn.microsoft.com/en-us/azure/virtual-desktop/fslogix-profile-containers

Instructor Notes: FSLogix profile containers  
Overview: FSLogix stores full user profiles in VHD/VHDX containers for roaming across sessions.  
Key points:
- Containers attach at sign-in and behave like local profiles.
- Recommended for pooled host pools to preserve user settings.
- Improves logon performance and profile consistency.

- Storage options for FSLogix profile containers in Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile

Instructor Notes: FSLogix storage options  
Overview: Azure Files is the default recommendation; Azure NetApp Files is for high performance.  
Key points:
- SMB file shares are required.
- Place storage in the same region as session hosts.
- Consider workload type and user count when sizing.

## Slide 6-7: Azure storage management options
- Azure Files overview: https://learn.microsoft.com/en-us/azure/storage/files/storage-files-introduction

Instructor Notes: Azure Files  
Overview: Fully managed SMB/NFS file shares accessible from Azure and on-premises.  
Key points:
- Supports hybrid access with Azure File Sync.
- Common choice for FSLogix profiles.
- Integrates with AD DS or Entra Domain Services.

- Azure NetApp Files introduction: https://learn.microsoft.com/en-us/azure/azure-netapp-files/azure-netapp-files-introduction

Instructor Notes: Azure NetApp Files  
Overview: Enterprise-grade, high-performance SMB/NFS volumes for latency-sensitive profiles.  
Key points:
- Uses capacity pools and service levels.
- Suitable for large-scale or performance-critical AVD.
- Supports snapshots and backup options.

- Storage Spaces Direct overview: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/storage-spaces-direct-overview

Instructor Notes: Storage Spaces Direct  
Overview: On-premises software-defined storage for file shares and VM workloads.  
Key points:
- Often used in Azure Local scenarios.
- Provides high availability and scale-out storage.
- Requires on-prem infrastructure management.

## Slide 8-9: Azure Files tiers
- Azure Files tiers for FSLogix profiles: https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile#azure-files-tiers

Instructor Notes: Azure Files tiers  
Overview: Standard (HDD) vs Premium (SSD) file shares with different cost/performance.  
Key points:
- Premium offers low latency and consistent IOPS.
- Standard is cost-effective for light workloads.
- Workload type and user count drive tier choice.

## Slide 10-11: Azure NetApp Files tiers
- Azure NetApp Files service levels: https://learn.microsoft.com/en-us/azure/azure-netapp-files/azure-netapp-files-service-levels

Instructor Notes: ANF service levels  
Overview: Service level (Ultra/Premium/Standard) defines throughput per TB.  
Key points:
- Performance scales with provisioned capacity.
- Choose tier based on workload intensity and user count.
- Higher tiers reduce latency for heavy workloads.

## Slide 12-13: Storage account types for Azure Files
- Storage account overview (types of storage accounts): https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview#types-of-storage-accounts

Instructor Notes: Storage account types  
Overview: Azure Files uses GPv2 (standard) or FileStorage (premium) account types.  
Key points:
- GPv2 supports standard file shares and other services.
- FileStorage supports premium file shares only.
- Choose account type based on tier and performance needs.

## Related
- [[AZ-140T00A-ENU-Powerpoint_10]]
- [[FSLogix Overview]]
- [[AZ-140T00A-ENU-Powerpoint_05_Script]]
- [[AZ-140T00A-ENU-Powerpoint_03]]
- [[AZ-140T00A-ENU-Powerpoint_10_Script]]
