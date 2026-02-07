# AZ-140T00A-ENU-Powerpoint_08.pptx

## Slide 4-6: Identity strategy for Azure Virtual Desktop
- Supported identities and authentication methods: https://learn.microsoft.com/en-us/azure/virtual-desktop/authentication

Instructor Notes: Identity types  
Overview: AVD supports on‑prem/hybrid and cloud-only identities, with constraints.  
Key points:
- Users must be discoverable in Microsoft Entra ID.
- Hybrid identities sync from AD DS via Entra Connect.
- Cloud-only identities require Entra-joined session hosts.

- Prerequisites for Azure Virtual Desktop (identity scenarios): https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#identity

Instructor Notes: Supported identity scenarios  
Overview: Identity scenarios define how session hosts are joined and users are synchronized.  
Key points:
- Entra ID is always used for service authentication.
- Session hosts can be AD DS, Entra DS, or Entra joined.
- UPN or SID must match for hybrid identities.

## Slide 7-9: Authentication strategy (service, session host, in-session)
- Supported identities and authentication methods (authentication): https://learn.microsoft.com/en-us/azure/virtual-desktop/authentication#authentication-methods

Instructor Notes: Authentication layers  
Overview: Users authenticate to the service, the session host, and then in-session resources.  
Key points:
- Service auth uses Entra ID and supports MFA/passwordless.
- Session host auth can be seamless with SSO.
- Smart card auth requires Entra CBA or AD FS cert auth.

## Slide 10-14: RBAC roles for Azure Virtual Desktop
- Built-in Azure RBAC roles for Azure Virtual Desktop: https://learn.microsoft.com/en-us/azure/virtual-desktop/rbac

Instructor Notes: AVD RBAC roles  
Overview: AVD uses Azure RBAC with specialized roles for host pools, app groups, and workspaces.  
Key points:
- Use least-privilege roles for admin tasks.
- Separate roles exist for session operations vs configuration.
- Scope assignments to host pools, app groups, or workspaces.

## Slide 15-17: Assign roles to AVD service principals
- Assign Azure RBAC roles or Microsoft Entra roles to a service principal: https://learn.microsoft.com/en-us/azure/virtual-desktop/service-principal-assign-roles

Instructor Notes: Service principal permissions  
Overview: Features like Autoscale, Start VM on Connect, and App Attach require SPN roles.  
Key points:
- Assign roles at subscription scope for autoscale/Start VM on Connect.
- Use correct AVD service principal IDs.
- Managed identity is preview for select features.

## Slide 18-19: Enforce MFA with Conditional Access
- Enforce Microsoft Entra multifactor authentication for Azure Virtual Desktop using Conditional Access: https://learn.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa

Instructor Notes: MFA for AVD  
Overview: MFA is enforced at the service sign‑in via Conditional Access.  
Key points:
- Applies to web, desktop, and mobile clients as configured.
- Session host sign‑in is seamless with SSO.
- Sign‑in frequency can be set with Conditional Access.

## Slide 20-21: Using AVD with Microsoft Intune
- Windows Enterprise multi-session remote desktops (Intune support): https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/azure-virtual-desktop-multi-session

Instructor Notes: Intune for multi-session  
Overview: Intune can manage Windows Enterprise multi‑session VMs for device and user policies.  
Key points:
- Device and user scope policies are supported via Settings catalog.
- Apps must be installed in system context for multi-session.
- Requires supported AVD agent version and enrollment.

## Related
- [[AZ-140T00A-ENU-Powerpoint_01]]
- [[overview]]
- [[AZ-140T00A-ENU-Powerpoint_01_Script]]
- [[AZ-140T00A-ENU-Powerpoint_02]]
- [[AZ-140T00A-ENU-Powerpoint_08_Script]]
