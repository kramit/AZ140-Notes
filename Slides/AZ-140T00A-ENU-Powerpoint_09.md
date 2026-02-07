# AZ-140T00A-ENU-Powerpoint_09.pptx

## Slide 3-6: Security recommendations and shared responsibility for Azure Virtual Desktop
- Security recommendations for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/security-recommendations

Instructor Notes: Shared responsibility and boundaries  
Overview: AVD uses a shared responsibility model where Microsoft manages the control plane while customers manage identity, session hosts, and network controls.  
Key points:
- Review the shared responsibility table for AVD components.
- Security boundaries (network, kernel, process, session, VM, VSM) help isolate trust domains.
- Multi-session trust scenarios are addressed in the security boundaries section.

- Security boundaries in Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/security-recommendations#security-boundaries

## Slide 7-10: Connect subscriptions to Microsoft Defender for Cloud and secure score
- Connect your Azure subscriptions to Microsoft Defender for Cloud: https://learn.microsoft.com/en-us/azure/defender-for-cloud/connect-azure-subscription

Instructor Notes: Defender for Cloud overview  
Overview: Defender for Cloud is a CNAPP that includes CSPM, DevSecOps, and CWPP capabilities.  
Key points:
- CNAPP, CSPM, and CWPP definitions are covered in the Defender for Cloud introduction.
- Enabling Defender for Cloud provides Foundational CSPM and secure score visibility.

- What is Microsoft Defender for Cloud (CNAPP/CSPM/CWPP): https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction

- Secure score in Defender for Cloud: https://learn.microsoft.com/en-us/azure/defender-for-cloud/secure-score-security-controls
- Secure score calculation (every 8 hours): https://learn.microsoft.com/en-us/azure/defender-for-cloud/secure-score-security-controls#calculation-of-the-secure-score

## Slide 11-12: Microsoft Defender for Endpoint for Azure Virtual Desktop sessions
- Onboard Windows devices in Azure Virtual Desktop (Defender for Endpoint): https://learn.microsoft.com/en-us/defender-endpoint/onboard-windows-multi-session-device

Instructor Notes: Onboarding methods  
Overview: AVD hosts can be onboarded via golden image/startup script, group policy, management tools, or Defender for Cloud integration.  
Key points:
- Use the AVD-specific onboarding guidance.
- Script placement and timing matter for pooled host pools.

## Slide 13-15: Apply Zero Trust principles to Azure Virtual Desktop
- Apply Zero Trust principles to an Azure Virtual Desktop deployment: https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-avd
- Apply Zero Trust principles to Storage in Azure: https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-storage
- Apply Zero Trust principles to a hub virtual network in Azure: https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-networking
- Apply Zero Trust principles to virtual machines in Azure: https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-virtual-machines
- Azure Private Link with Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/private-link-overview
- Set up Private Link with Azure Virtual Desktop (private endpoints): https://learn.microsoft.com/en-us/azure/virtual-desktop/private-link-setup
- Azure Virtual Desktop Insights: https://learn.microsoft.com/en-us/azure/virtual-desktop/insights

## Slide 16-18: Conditional Access policies for Azure Virtual Desktop
- Enforce Microsoft Entra multifactor authentication for Azure Virtual Desktop using Conditional Access: https://learn.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa

## Related
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[AZ-140T00A-ENU-Powerpoint_08_Script]]
- [[AZ-140T00A-ENU-Powerpoint_09_Script]]
- [[AZ-140T00A-ENU-Powerpoint_14]]
