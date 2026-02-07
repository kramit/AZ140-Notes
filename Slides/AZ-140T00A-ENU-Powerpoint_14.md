# AZ-140T00A-ENU-Powerpoint_14.pptx

## Slide 4-7: Disaster recovery for Azure Virtual Desktop
- Azure Virtual Desktop service architecture and resilience: https://learn.microsoft.com/en-us/azure/virtual-desktop/service-architecture-resilience
- Multiregion Business Continuity and Disaster Recovery (BCDR) for AVD: https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop-multi-region-bcdr
- Active-active vs active-passive host pool designs: https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop-multi-region-bcdr#active-active-vs-active-passive
- Failover and failback guidance (AVD + Site Recovery): https://learn.microsoft.com/en-us/azure/architecture/example-scenario/azure-virtual-desktop/azure-virtual-desktop-multi-region-bcdr#failover-and-failback
- Azure Site Recovery overview: https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview
- Azure Virtual Desktop network connectivity: https://learn.microsoft.com/en-us/azure/virtual-desktop/network-connectivity
- FSLogix BCDR options (profiles): https://learn.microsoft.com/en-us/fslogix/concepts-container-recovery-business-continuity
- Azure Files data redundancy (profile storage): https://learn.microsoft.com/en-us/azure/storage/files/files-redundancy
- Microsoft Entra identity overview: https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra
- Azure VM backup overview: https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction

Instructor Notes: Disaster recovery for AVD  
Overview: Plan for outages across regions by separating Microsoft-managed and customer-managed components.  
Key points:
- Use active-active for minimal RTO/RPO, or active-passive for lower cost with manual failover.
- Site Recovery can replicate session host VMs between regions.
- Ensure network connectivity, identity, and profile storage are resilient (FSLogix + Azure Files redundancy).

## Slide 8-10: Design and implement a backup strategy for AVD
- Azure VM backup overview: https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction
- Recovery Services vaults overview: https://learn.microsoft.com/en-us/azure/backup/backup-azure-recovery-services-vault-overview
- Encryption of Azure VM backups: https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction#encryption-of-azure-vm-backups
- Back up encrypted Azure VMs (ADE/CMK support): https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-encryption

Instructor Notes: Backup strategy  
Overview: Use Azure Backup with Recovery Services vaults to protect session hosts and data.  
Key points:
- Backups use scheduled snapshots and app-consistent VSS on Windows.
- Vaults provide centralized policies, retention, and restore points.
- Encryption supports SSE (PMK/CMK) and Azure Disk Encryption.

## Slide 11-14: Monitor costs by using Azure Cost Management
- View forecast costs in Cost Analysis: https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-analysis-common-uses#view-forecast-costs
- View forecast costs grouped by service: https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-analysis-common-uses#view-forecast-costs-grouped-by-service
- View forecast costs for a service: https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-analysis-common-uses#view-forecasted-costs-for-a-service
- View cost breakdown by Azure service: https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/cost-analysis-common-uses#view-cost-breakdown-by-azure-service

Instructor Notes: Cost Management  
Overview: Use Cost Analysis to forecast and break down AVD costs by service.  
Key points:
- Forecasts are based on historical usage and shown as shaded areas.
- Group by Service name to compare contributors.
- Use Cost by service and table views for detailed breakdowns.

## Related
- [[AZ-140T00A-ENU-Powerpoint_14_Script]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_09]]
- [[AZ-140T00A-ENU-Powerpoint_13]]
- [[SC-401T00A-ENU-PowerPoint_01]]
