# AZ-140T00A-ENU-Powerpoint_12.pptx

## Slide 4-5: Create and configure an application group
- Create an application group (Azure portal): https://learn.microsoft.com/en-us/azure/virtual-desktop/deploy-azure-virtual-desktop#create-a-workspace

Instructor Notes: Application groups  
Overview: Application groups publish full desktops or RemoteApps and link host pools to workspaces.  
Key points:
- Two types: Desktop and RemoteApp.
- Application groups must be associated with a workspace.
- RemoteApp groups require adding apps before users can see them.

## Slide 6-7: Assign users to application groups
- Assign users to an application group: https://learn.microsoft.com/en-us/azure/virtual-desktop/deploy-azure-virtual-desktop#assign-users-to-an-application-group

Instructor Notes: Assignments  
Overview: Users or groups get access by assigning them to the application group.  
Key points:
- Use Microsoft Entra security groups for scale.
- Assignments are done on the application group’s Assignments blade.
- Users see resources only after assignment and workspace association.

## Slide 8-9: Publish an application as a RemoteApp
- Publish applications with RemoteApp in Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/publish-applications-stream-remoteapp

Instructor Notes: RemoteApp publishing  
Overview: RemoteApp streams individual apps from session hosts or App Attach packages.  
Key points:
- Apps must be installed on session hosts (or App Attach assigned).
- At least one session host must be powered on to add apps.
- Users access apps via Windows App once assigned.

## Slide 10-11: Implement and manage OneDrive (multisession)
- Install OneDrive in per-machine mode (AVD images): https://learn.microsoft.com/en-us/azure/virtual-desktop/install-office-on-wvd-master-image#install-onedrive-in-per-machine-mode
- Use the OneDrive sync app on virtual desktops (per-machine requirement): https://learn.microsoft.com/en-us/sharepoint/sync-vdi-support

Instructor Notes: OneDrive on AVD  
Overview: OneDrive should be installed per-machine for multi-user environments.  
Key points:
- Per-machine install avoids per-user binaries in profiles.
- Supported with FSLogix for non-persistent AVD.
- Use silent config and KFM policies as needed.

## Slide 12-13: Implement and manage Microsoft Teams for Remote Desktop
- Use Microsoft Teams on Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/teams-on-avd

Instructor Notes: Teams on AVD  
Overview: Teams requires media optimization components and per-machine installation in pooled hosts.  
Key points:
- Set IsWVDEnvironment registry key for optimization.
- Install the WebRTC Redirector Service and supported client versions.
- Validate optimization status in Teams client.

## Slide 14-15: Implement Microsoft 365 Apps on AVD session hosts
- Install Office in shared computer activation mode: https://learn.microsoft.com/en-us/azure/virtual-desktop/install-office-on-wvd-master-image#install-office-in-shared-computer-activation-mode

Instructor Notes: Microsoft 365 Apps  
Overview: Shared computer activation is required for multi-user session hosts.  
Key points:
- Use Office Deployment Tool with shared activation enabled.
- Requires eligible Microsoft 365 licensing per user.
- Update strategy should align with image management.

## Slide 16-20: App attach / MSIX app attach (dynamic app delivery)
- App Attach overview (how it works): https://learn.microsoft.com/en-us/azure/virtual-desktop/app-attach-overview
- App Attach prerequisites: https://learn.microsoft.com/en-us/azure/virtual-desktop/app-attach-setup#prerequisites
- Add an App Attach package (Azure portal): https://learn.microsoft.com/en-us/azure/virtual-desktop/app-attach-setup#add-an-application
- Create an MSIX image for App Attach: https://learn.microsoft.com/en-us/azure/virtual-desktop/app-attach-create-msix-image

Instructor Notes: App Attach vs MSIX app attach  
Overview: App Attach mounts MSIX/Appx images at sign-in to avoid installing apps in the base image.  
Key points:
- App Attach packages are stored on SMB file shares in the same region.
- Host pool validation environment and Windows client OS required.
- MSIX app attach adds apps to Desktop/RemoteApp without full image rebuilds.

## Slide 24: App attach file share permissions (knowledge check)
- App Attach file share permissions (read access + RBAC guidance): https://learn.microsoft.com/en-us/azure/virtual-desktop/app-attach-overview#file-share

Instructor Notes: File share permissions  
Overview: Session hosts must have read access to the share containing app images.  
Key points:
- Configure NTFS and share permissions for computer objects.
- Azure Files with Entra ID requires Reader and Data Access for AVD service principals.
- Keep app attach images on a dedicated storage account when possible.

## Related
- [[AZ-140T00A-ENU-Powerpoint_12_Script]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_11]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[overview]]
