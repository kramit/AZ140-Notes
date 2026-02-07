# AZ-140T00A-ENU-Powerpoint_07.pptx

## Slide 4-5: Create a golden image (managed image)
- Create an image of a VM in the portal: https://learn.microsoft.com/en-us/azure/virtual-machines/capture-image-portal

Instructor Notes: Managed (golden) image creation  
Overview: Capture a generalized VM to create a reusable image for session hosts.  
Key points:
- Generalize the VM (Sysprep) before capture.
- Images can be stored as managed images or in a Compute Gallery.
- A consistent golden image simplifies updates and scaling.

## Slide 6-9: Azure VM Image Builder
- Azure VM Image Builder overview: https://learn.microsoft.com/en-us/azure/virtual-machines/image-builder-overview

Instructor Notes: VM Image Builder  
Overview: Fully managed service to build customized VM images using templates and scripts.  
Key points:
- Uses Marketplace or custom images as sources.
- Automates image customization and distribution.
- Integrates with Azure Compute Gallery for versioning.

## Slide 10-13: Azure Compute Gallery
- Store and share images in an Azure Compute Gallery: https://learn.microsoft.com/en-us/azure/virtual-machines/shared-image-galleries

Instructor Notes: Compute Gallery basics  
Overview: Compute Gallery manages image definitions, versions, and replication.  
Key points:
- Supports versioning and regional replication.
- Enables sharing across subscriptions/tenants with RBAC.
- Improves availability with ZRS in supported regions.

- Store and share resources in Azure Compute Gallery (replication/HA): https://learn.microsoft.com/en-us/azure/virtual-machines/azure-compute-gallery#high-availability

Instructor Notes: Replication and resiliency  
Overview: Replicas in multiple regions improve deployment scale and resilience.  
Key points:
- Configure replica counts per region.
- Replication reduces throttling in multi-VM deployments.
- ZRS offers zone-level resilience.

## Slide 14-15: Licensing for session hosts
- Apply a Windows license to session host virtual machines: https://learn.microsoft.com/en-us/azure/virtual-desktop/apply-windows-license

Instructor Notes: Session host licensing  
Overview: Apply AVD licensing to Windows client/server session hosts.  
Key points:
- Auto-applied when created via AVD service.
- Can be applied manually to existing VMs.
- Not for non-session-host roles (file servers/DCs).

## Slide 16-17: Language packs in AVD images
- Add language packs to a Windows 10 multi-session image: https://learn.microsoft.com/en-us/azure/virtual-desktop/language-packs

Instructor Notes: Language packs  
Overview: Add languages to multi-session images via ISO-based repositories.  
Key points:
- Requires Language, FOD, and Inbox Apps ISOs.
- Use a file share repository accessible by the build VM.
- Image customization can support multiple languages in one pool.

## Related
- [[AZ-140T00A-ENU-Powerpoint_07_Script]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_12]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_06]]
