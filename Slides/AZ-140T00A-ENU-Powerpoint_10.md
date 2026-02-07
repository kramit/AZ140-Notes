# AZ-140T00A-ENU-Powerpoint_10.pptx

## Slide 3-6: Overview of FSLogix and key capabilities
- What is FSLogix (key capabilities): https://learn.microsoft.com/en-us/fslogix/overview-what-is-fslogix

Instructor Notes: FSLogix overview  
Overview: FSLogix virtualizes user profiles for consistent sign-in experience in AVD and other desktop environments.  
Key points:
- Uses profile containers to present a local-profile experience from remote storage.
- Includes Office data support (ODFC) and Cloud Cache for resiliency.
- Reduces profile load times and simplifies image management.

## Slide 7-9: Understanding FSLogix containers (Profile and ODFC)
- Types of containers (profile and ODFC): https://learn.microsoft.com/en-us/fslogix/concepts-container-types
- When to use Profile and ODFC containers: https://learn.microsoft.com/en-us/fslogix/concepts-container-types#when-to-use-profile-and-odfc-containers

Instructor Notes: Container types  
Overview: FSLogix uses Profile and ODFC containers to store user data in VHD(X) files.  
Key points:
- Profile container includes most of C:\Users\%username% by default.
- ODFC focuses on Microsoft 365 data and is optional when using profile containers.
- Dual containers can separate Office data for size and isolation scenarios.

## Slide 10-11: Configuring FSLogix Profile Containers
- Configure profile containers using FSLogix: https://learn.microsoft.com/en-us/fslogix/how-to-configure-profile-containers

Instructor Notes: Profile container configuration  
Overview: Profile containers redirect the full profile to a VHD(X) on a storage provider (commonly SMB).  
Key points:
- Single container configuration is recommended.
- Requires FSLogix install, storage permissions, and registry/GPO settings.
- Works well for pooled AVD host pools to preserve user settings.

## Slide 12-13: Configuring FSLogix Office Containers (ODFC)
- Configure ODFC containers: https://learn.microsoft.com/en-us/fslogix/how-to-configure-odfc-containers

Instructor Notes: ODFC containers  
Overview: ODFC containers store Microsoft 365 app data separately from the rest of the profile.  
Key points:
- Used with third-party profile solutions or in dual-container scenarios.
- Not needed if profile container is the primary solution (single container).
- Requires correct exclusions if paired with other profile tools.

## Slide 14-15: Configuring profile containers with Cloud Cache
- Cloud Cache overview: https://learn.microsoft.com/en-us/fslogix/concepts-fslogix-cloud-cache
- Tutorial: Configure profile containers with Cloud Cache: https://learn.microsoft.com/en-us/fslogix/tutorial-cloud-cache-containers

Instructor Notes: Cloud Cache  
Overview: Cloud Cache adds resiliency by using local cache and multiple storage providers.  
Key points:
- Mitigates short-term/intermittent storage connectivity issues.
- Uses CCDLocations instead of VHDLocations.
- Suitable for HA/BCDR designs with multiple storage providers.

## Slide 16-18: Using FSLogix Apps RuleEditor and Rule Sets
- FSLogix Apps RuleEditor and Rule Sets (types of rules): https://learn.microsoft.com/en-us/fslogix/concepts-fslogix-apps-rule-editor-rule-sets

Instructor Notes: RuleEditor and rules  
Overview: Rule Sets control visibility, redirection, and registry settings for apps and resources.  
Key points:
- Rule types include hiding, redirection, and specify value.
- Applied at sign-in by FSLogix Apps Services.
- Useful for app masking and policy-driven customization.

## Slide 19-20: Creating and implementing Rule Sets for application masking
- Tutorial: Create and Implement Rule Sets (Application Masking): https://learn.microsoft.com/en-us/fslogix/tutorial-application-rule-sets

Instructor Notes: Application masking  
Overview: Rule Sets can hide apps (example: Chrome) for specific users or groups.  
Key points:
- RuleEditor can scan installed apps to generate hiding rules.
- Assignments target users/groups, processes, or other conditions.
- Rule files are deployed to the FSLogix rules folder and apply immediately.

## Slide 23: Azure Files performance tiers (knowledge check)
- Storage options for FSLogix profile containers in Azure Virtual Desktop (Azure Files tiers): https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile#azure-files-tiers

Instructor Notes: Azure Files tiers  
Overview: Standard vs Premium file shares map to workload size and performance needs.  
Key points:
- Light workloads (<200 users) often fit standard file shares.
- Premium is recommended for higher scale or heavier workloads.
- Standard + multiple shares can scale beyond 200 users.

## Related
- [[FSLogix Overview]]
- [[AZ-140T00A-ENU-Powerpoint_10_Script]]
- [[AZ-140T00A-ENU-Powerpoint_05]]
- [[AZ-140T00A-ENU-Powerpoint_03]]
