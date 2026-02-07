# FSLogix Profile Containers for Azure Virtual Desktop

## Entra ID–only users + Azure Files (Storage Account Key–based)

  

This document is a **complete, reproducible tutorial** for configuring **FSLogix Profile Containers** in an **Azure Virtual Desktop (AVD) lab** using:

  

- Entra ID–only users (cloud-only, no AD)

- Azure Files

- Storage account **key-based authentication**

- Windows 11 Enterprise multi-session session hosts

  

This approach avoids Kerberos and hybrid identity requirements and is ideal for labs, demos, and training environments.

  

---

  

## Architecture Overview

  

- **Session hosts**: Windows 11 Enterprise multi-session, Entra ID–joined

- **Profiles**: FSLogix VHDX stored in Azure Files

- **Auth to storage**: Storage account access key (computer context)

- **Identity**: Entra ID only

- **No AD DS / No Entra Domain Services / No Entra Kerberos**

  

---

  

## Prerequisites

  

- Azure subscription

- Azure Virtual Desktop host pool (Pooled)

- At least one session host VM

- Global Admin / Owner permissions

- Outbound TCP **445** allowed from session hosts

  

---

  

## Step 1 — Create Entra ID security groups

  

### AVD users group

  

Used for:

- AVD Application Group assignments

- Azure Files RBAC

  

Create in Entra ID:

- **Name**: `AVDusers`

- **Type**: Security

- Add all AVD users

  

---

  

## Step 2 — Create Azure Storage Account

  

Create a storage account with:

- Performance: Standard

- Redundancy: LRS (lab)

- Public endpoint: Enabled

  

### Enable key-based access

  

Storage account → **Configuration**

- **Allow storage account key access** = Enabled

  

---

  

## Step 3 — Create Azure File Share

  

Storage account → **File shares**

- Create share (example: `fslogix`)

  

This share will store user profile VHDX files.

  

---

  

## Step 4 — Disable identity-based access

  

Storage account → **Azure Files → Identity-based access**

  

Ensure **all are disabled**:

- Active Directory Domain Services

- Microsoft Entra Domain Services

- Microsoft Entra Kerberos

  

This configuration **does not use Kerberos**.

  

---

  

## Step 5 — Assign Azure RBAC permissions

  

Even with key-based auth, RBAC is required.

  

### Scope

- Storage account (or specific file share)

  

### Role

- **Storage File Data SMB Share Contributor**

  

### Assign to

- `AVDusers` (security group)

- Session host VM **system-assigned managed identity**

  

---

  

## Step 6 — Enable managed identity on session host VM

  

For each session host:

  

VM → **Identity**

- System-assigned managed identity = On

- Save

  

---

  

## Step 7 — Install FSLogix on session hosts

  

Download **FSLogix Apps** from Microsoft.

  

Install (run as Administrator):

  

```powershell

FSLogixAppsSetup.exe /install /quiet

```

  

Reboot the VM.

  

---

  

## Step 8 — Configure FSLogix registry settings

  

Run the following **PowerShell as Administrator** on each session host.

  

```powershell

$storageAccount = "<storageaccount>" # e.g. mikeavdstore

$shareName = "<share>" # e.g. fslogix

  

$regPath = "HKLM:\SOFTWARE\FSLogix\Profiles"

$uncPath = "\\${storageAccount}.file.core.windows.net\${shareName}"

  

if (-not (Test-Path $regPath)) {

New-Item -Path $regPath -Force | Out-Null

}

  

New-ItemProperty -Path $regPath -Name "Enabled" -PropertyType DWord -Value 1 -Force

New-ItemProperty -Path $regPath -Name "VHDLocations" -PropertyType MultiString -Value @($uncPath) -Force

New-ItemProperty -Path $regPath -Name "DeleteLocalProfileWhenVHDShouldApply" -PropertyType DWord -Value 1 -Force

New-ItemProperty -Path $regPath -Name "FlipFlopProfileDirectoryName" -PropertyType DWord -Value 1 -Force

```

  

---

  

## Step 9 — Enable key-based access for FSLogix

  

This is **critical** for Entra-only environments.

  

```powershell

$regPath = "HKLM:\SOFTWARE\FSLogix\Profiles"

  

if (-not (Test-Path $regPath)) {

New-Item -Path $regPath -Force | Out-Null

}

  

New-ItemProperty `

-Path $regPath `

-Name "AccessNetworkAsComputerObject" `

-PropertyType DWord `

-Value 1 `

-Force

```

  

---

  

## Step 10 — Reboot session host

  

Mandatory after registry changes.

  

---

  

## Step 11 — Validate storage account key access

  

On the session host:

  

```cmd

net use \\<storageaccount>.file.core.windows.net\<share> /user:Azure\<storageaccount> <storage-account-key>

```

  

Expected result:

  

```

The command completed successfully.

```

  

---

  

## Step 12 — Assign users to Azure Virtual Desktop

  

- Add users to `AVDusers`

- Assign users to the AVD Application Group

- Do **not** assign users to conflicting Desktop + RemoteApp groups

  

---

  

## Step 13 — First login test

  

- Sign in as an AVD user

- First login will be slower

  

### Expected result in file share

  

```

fslogix/

└── <username>_<SID>/

└── Profile_<username>.vhdx

```

  

FSLogix creates this automatically.

  

---

  

## Step 14 — Verify FSLogix logs

  

On the session host:

  

```

C:\ProgramData\FSLogix\Logs\Profile

```

  

Look for:

- `Attach VHD succeeded`

- `Profile container created`

- No TEMP profile messages

  

---

  

## Validation Tests

  

### Persistence test

- Create file on Desktop

- Sign out

- Sign back in

- File persists

  

### File lock test

- While logged in, attempt to delete VHDX

- Deletion fails

  

### Autoscale-safe

- Sign out

- No `.lock` file remains

  

---

  

## Common Failure Causes

  

| Symptom | Cause |

|------|------|

| Error 1326 | Kerberos enabled with Entra-only users |

| TEMP profile | FSLogix not enabled |

| Cannot find VHD | Wrong UNC path |

| Access denied | Missing RBAC or key access disabled |

| Login hang | TCP 445 blocked |

  

---

  

## Final confirmation

  

If the VHDX is created automatically and reused across logins, **FSLogix is working correctly**.