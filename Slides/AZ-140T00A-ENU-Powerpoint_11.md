# AZ-140T00A-ENU-Powerpoint_11.pptx

## Slide 4-5: Connect to Azure Virtual Desktop with the Remote Desktop client for Windows / Windows App
- Connect to Azure Virtual Desktop (Windows App or Remote Desktop client): https://learn.microsoft.com/en-us/azure/virtual-desktop/connect-azure-virtual-desktop
- Get started with Windows App to connect to devices and apps: https://learn.microsoft.com/en-us/windows-app/get-started-connect-devices-desktops-apps?pivots=azure-virtual-desktop

Instructor Notes: Client connections  
Overview: Users connect using Windows App (recommended) or the Remote Desktop client with a workspace subscription.  
Key points:
- Windows App replaces the Remote Desktop client for AVD connectivity.
- Users must sign in with the correct account and have resources assigned.
- Workspace URL discovery is handled in Windows App for external clouds.

## Slide 6-7: Configure session timeout properties
- Configure session time limits (RDS Session Time Limits via Group Policy/Intune): https://learn.microsoft.com/en-us/azure/virtual-desktop/autoscale-create-assign-scaling-plan#configure-a-time-limit-policy

Instructor Notes: Session timeouts  
Overview: Session Time Limits policies control idle/disconnected session behavior to balance UX and resource usage.  
Key points:
- Policies live under Remote Desktop Session Host > Session Time Limits.
- Configure disconnected/idle/active time limits and end sessions when limits are reached.
- Apply via Group Policy or Intune and reboot to take effect.

## Slide 8-9: Implement Start VM on Connect
- Configure Start VM on Connect: https://learn.microsoft.com/en-us/azure/virtual-desktop/start-virtual-machine-connect

Instructor Notes: Start VM on Connect  
Overview: Lets users power on session hosts on demand to reduce costs.  
Key points:
- Configure per host pool after assigning required RBAC roles.
- Works with personal and pooled host pools (starts VMs as capacity is needed).
- Users see a “VM is being powered on” message while connecting.

## Slide 10-11: Configure Universal Print
- Printing on Azure Virtual Desktop using Universal Print: https://learn.microsoft.com/en-us/universal-print/fundamentals/universal-print-avd
- Set up Universal Print (overview): https://learn.microsoft.com/en-us/universal-print/set-up-universal-print

Instructor Notes: Universal Print on AVD  
Overview: Universal Print provides cloud-based printing with per-user printer installs and roaming.  
Key points:
- Printers install per-user and roam with profiles (FSLogix supported).
- Location-based search can use the client device location with location override enabled.
- Universal Print can replace classic printer redirection scenarios.

## Slide 12-13: Configure device redirections
- Set custom RDP properties (default device redirection properties): https://learn.microsoft.com/en-us/azure/virtual-desktop/customize-rdp-properties#default-host-pool-rdp-properties
- Configure audio and video redirection (audiocapturemode/audiomode): https://learn.microsoft.com/en-us/azure/virtual-desktop/redirection-configure-audio-video
- Configure USB redirection (usbdevicestoredirect): https://learn.microsoft.com/en-us/azure/virtual-desktop/redirection-configure-usb

Instructor Notes: Device redirection  
Overview: Device redirection is controlled by host pool RDP properties and session host policy.  
Key points:
- Use RDP properties such as audiocapturemode, audiomode, camerastoredirect, and usbdevicestoredirect.
- Most restrictive setting (host or client) wins for redirection behavior.
- USB redirection can be scoped by device class GUIDs or instance IDs.

## Slide 14-16: Troubleshoot Azure Virtual Desktop clients
- Troubleshoot Azure Virtual Desktop service connections (no feed/resources): https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-desktop/troubleshoot-service-connection
- Troubleshoot connections to Microsoft Entra joined VMs (credentials/logon attempt failed): https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-desktop/troubleshoot-azure-ad-connections

Instructor Notes: Client troubleshooting  
Overview: Common issues include missing resources and authentication errors.  
Key points:
- Verify correct account, workspace association, and app group assignment.
- For credential errors, confirm VM User Login role and Conditional Access settings.
- “Logon attempt failed” often ties to Entra join requirements or PKU2U.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_11_Script]]
- [[AZ-140T00A-ENU-Powerpoint_03]]
- [[AZ-140T00A-ENU-Powerpoint_06]]
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
