<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment-group-policy-network-share -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# Microsoft Defender Antivirus production ring deployment using Group Policy and network share

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats.

Tip

A new Microsoft Defender Vulnerability Management add-on is now available for Microsoft Defender for Endpoint Plan 2.

This article describes how to deploy Microsoft Defender Antivirus in rings using Group Policy and Network share \(also known as UNC path, SMB, CIFS\).

## Prerequisites

Review the *read me* article at [Readme](https://github.com/microsoft/defender-updatecontrols/blob/main/README.md)

### Supported operating systems

- Windows
- Windows Server

1. Download the latest Windows Defender .admx and .adml.

   - [WindowsDefender.admx](https://github.com/microsoft/defender-updatecontrols/blob/main/WindowsDefender.admx)
   - [WindowsDefender.adml](https://github.com/microsoft/defender-updatecontrols/blob/main/WindowsDefender.adml)

2. Copy the latest .admx and .adml to the [Domain Controller Central Store](https://learn.microsoft.com/en-us/troubleshoot/windows-client/group-policy/create-and-manage-central-store#the-central-store).
3. [Create a UNC share for security intelligence and platform updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-updates-microsoft-defender-antivirus#create-a-unc-share-for-security-intelligence)

## Setting up the pilot environment

This section describes the process for setting up the pilot UAT / Test / QA environment. On about 10-500\* Windows and/or Windows Server systems, depending on how many total systems that you all have.

[![Screenshot that shows an example Microsoft Defender Antivirus ring deployment schedule for Group Policy and network share environments.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-gp-network-schedule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-gp-network-schedule.png#lightbox)

Note

Security intelligence update \(SIU\) is equivalent to signature updates, which is the same as definition updates.

### Create a UNC share for security intelligence

Set up a network file share \(UNC/mapped drive\) to download security intelligence from the MMPC site by using a scheduled task.

1. On the system on which you want to provision the share and download the updates, create a folder to which you will save the script.

   ```console
   Start, CMD (Run as admin)
   MD C:\Tool\PS-Scripts\
   ```

2. Create the folder to which you will save the signature updates.

   ```console
   MD C:\Temp\TempSigs\x64
   MD C:\Temp\TempSigs\x86
   ```

3. Set up a PowerShell script, `CopySignatures.ps1`

   Copy-Item -Path "\\SourceServer\\Sourcefolder" -Destination "\\TargetServer\\Targetfolder"
4. Use the command line to set up the scheduled task.

   Note

   There are two types of updates: full and delta.

   - For x64 delta:

     ```powershell
     Powershell (Run as admin)

     C:\Tool\PS-Scripts\

     ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
     ```

   - For x64 full:

     ```powershell
     Powershell (Run as admin)

     C:\Tool\PS-Scripts\

     ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
     ```

   - For x86 delta:

     ```powershell
     Powershell (Run as admin)

     C:\Tool\PS-Scripts\

     ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
     ```

   - For x86 full:

     ```powershell
     Powershell (Run as admin)

     C:\Tool\PS-Scripts\

     ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
     ```


   Note


   When the scheduled tasks are created, you can find these in the Task Scheduler under `Microsoft\Windows\Windows Defender`.

5. Run each task manually and verify that you have data \(`mpam-d.exe`, `mpam-fe.exe`, and `nis_full.exe`\) in the following folders \(you might have chosen different locations\):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`


   If the scheduled task fails, run the following commands:


   ```console
   C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

   C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

   C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

   C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
   ```


   Note


   Issues could also be due to execution policy.

6. Create a share pointing to `C:\Temp\TempSigs` \(e.g., `\\server\updates`\).

   Note

   At a minimum, authenticated users must have "Read" access. This requirement also applies to domain computers, the share, and NTFS \(security\).
7. Set the share location in the policy to the share.

   Note

   Do not add the x64 \(or x86\) folder in the path. The MpCmdRun.exe process adds it automatically.

## Setting up the Pilot \(UAT/Test/QA\) environment

This section describes the process for setting up the pilot UAT / Test / QA environment, on about 10-500 Windows and/or Windows Server systems, depending on how many total systems that you all have.

Note

If you have a Citrix environment, include at least 1 Citrix VM \(non-persistent\) and/or \(persistent\)

In [Group Policy Management Console](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265969\(v=ws.11\)) \(GPMC, GPMC.msc\), create or append to your Microsoft Defender Antivirus policy.

1. Edit your Microsoft Defender Antivirus policy. For example, edit *MDAV\_Settings\_Pilot*. Go to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus**. There are three related options:
   | Feature | Recommendation for the pilot systems |
   | --- | --- |
   | Select the channel for Microsoft Defender daily **Security Intelligence updates** | Current Channel \(Staged\) |
   | Select the channel for Microsoft Defender monthly **Engine updates** | Beta Channel |
   | Select the channel for Microsoft Defender monthly **Platform updates** | Beta Channel |


   The three options are shown in the following figure.


   [![Screenshot that shows a screen capture of the pilot Computer Configuration > Policies > Administrative Templates > Windows Components > Microsoft Defender Antivirus update channels.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channels.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channels.png#lightbox)


   For more information, see [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout)

2. Go to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus**.
3. For *intelligence* updates, double-click **Select the channel for Microsoft Defender monthly intelligence updates**.

   [![Screenshot that shows a screen capture of the Select the channel for Microsoft Defender monthly intelligence updates page with Enabled and Current Channel \(Staged\) selected.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channel-staged.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channel-staged.png#lightbox)
4. On the **Select the channel for Microsoft Defender monthly intelligence updates** page, select **Enabled**, and in **Options**, select **Current Channel \(Staged\)**.
5. Select **Apply**, and then select **OK**.
6. Go to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus**.
7. For *engine* updates, double-click **Select the channel for Microsoft Defender monthly engine updates**.
8. On the **Select the channel for Microsoft Defender monthly Platform updates** page, select **Enabled**, and in **Options**, select **Beta Channel**.
9. Select **Apply**, and then select **OK**.
10. For *platform* updates, double-click **Select the channel for Microsoft Defender monthly Platform updates**.
11. On the **Select the channel for Microsoft Defender monthly Platform updates** page, select **Enabled**, and in **Options**, select **Beta Channel**. These two settings are shown in the following figure:
12. Select **Apply**, and then select **OK**.

### Related articles

- [Antivirus profiles - Devices managed by Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-antivirus-policy#antivirus-profiles)
- [Use Endpoint security Antivirus policy to manage Microsoft Defender update behavior \(Preview\)](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/whats-new#use-endpoint-security-antivirus-policy-to-manage-microsoft-defender-update-behavior-preview)
- [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout)

## Setting up the production environment

1. In [Group Policy Management Console](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265969\(v=ws.11\)) \(GPMC, GPMC.msc\), go to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus**.

   [![Screenshot that shows a screen capture of the production Computer Configuration > Policies > Administrative Templates > Windows Components > Microsoft Defender Antivirus update channels.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channels.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channels.png#lightbox)
2. Set the three policies as follows:
   | Feature | Recommendation for the production systems | Remarks |
   | --- | --- | --- |
   | Select the channel for Microsoft Defender daily **Security Intelligence updates** | Current Channel \(Broad\) | This setting provides you with 3 hours of time to find an FP and prevent the production systems from getting an incompatible signature update. |
   | Select the channel for Microsoft Defender monthly **Engine updates** | Critical – Time delay | Updates are delayed by two days. |
   | Select the channel for Microsoft Defender monthly **Platform updates** | Critical – Time delay | Updates are delayed by two days. |
3. For *intelligence* updates, double-click **Select the channel for Microsoft Defender monthly intelligence updates**.
4. On the **Select the channel for Microsoft Defender monthly intelligence updates** page, select **Enabled**, and in **Options**, select **Current Channel \(Broad\)**.

   [![Screenshot that shows a screen capture of the Select the channel for Microsoft Defender monthly intelligence updates page with Enabled and Current Channel \(Staged\) selected.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channel-staged.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-gp-microsoft-defender-antivirus-channel-staged.png#lightbox)
5. Select **Apply**, and then select **OK**.
6. For *engine* updates, double-click **Select the channel for Microsoft Defender monthly engine updates**.
7. On the **Select the channel for Microsoft Defender monthly Platform updates** page, select **Enabled**, and in **Options**, select **Critical – Time delay**.
8. Select **Apply**, and then select **OK**.
9. For *platform* updates, double-click **Select the channel for Microsoft Defender monthly Platform updates**.
10. On the **Select the channel for Microsoft Defender monthly Platform updates** page, select **Enabled**, and in **Options**, select **Critical – Time delay**.
11. Select **Apply**, and then select **OK**.

## If you encounter problems

If you encounter problems with your deployment, create or append your Microsoft Defender Antivirus policy:

1. In [Group Policy Management Console](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265969\(v=ws.11\)) \(GPMC, GPMC.msc\), create or append to your Microsoft Defender Antivirus policy using the following setting:

   Go to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Microsoft Defender Antivirus** > \(administrator-defined\) *PolicySettingName*. For example, *MDAV\_Settings\_Production*, right-click, and then select **Edit**. **Edit** for **MDAV\_Settings\_Production** is shown in the following figure:

   [![Screenshot that shows a screen capture of the administrator-defined Microsoft Defender Antivirus policy Edit option.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-edit.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-edit.png#lightbox)
2. Select **Define the order of sources for downloading security intelligence updates**.
3. Select the radio button named **Enabled**.
4. Under **Options:**, change the entry to *FileShares*, select **Apply**, and then select **OK**. This change is shown in the following figure:

   [![Screenshot that shows a screen capture of the Define the order of sources for downloading security intelligence updates page.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-define-order.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-define-order.png#lightbox)
5. Select **Define the order of sources for downloading security intelligence updates**.
6. Select the radio button named **Disabled**, select **Apply**, and then select **OK**. The disabled option is shown in the following figure:

   [![Screenshot that shows a screen capture of the Define the order of sources for downloading security intelligence updates page with Security Intelligence updates disabled.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-disabled.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-policy-disabled.png#lightbox)
7. The change is active when Group Policy updates. There are two methods to refresh Group Policy:

   - From the command line, run the Group Policy update command. For example, run `gpupdate / force`. For more information, see [gpupdate](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpupdate)
   - Wait for Group Policy to automatically refresh. Group Policy refreshes every 90 minutes +/- 30 minutes.


   If you have multiple forests/domains, force replication or wait 10-15 minutes. Then force a Group Policy Update from the Group Policy Management Console.


   - Right-click on an organizational unit \(OU\) that contains the machines \(for example, Desktops\), select **Group Policy Update**. This UI command is the equivalent of doing a gpupdate.exe /force on every machine in that OU. The feature to force Group Policy to refresh is shown in the following figure:

     [![Screenshot that shows a screen capture of the Group Policy Management console, initiating a forced update.](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-management-console.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/microsoft-defender-antivirus-deploy-ring-group-policy-wsus-gp-management-console.png#lightbox)

8. After the issue is resolved, set the **Signature Update Fallback Order** back to the original setting. `InternalDefinitionUpdateServder|MicrosoftUpdateServer|MMPC|FileShare`.

## See also

[Microsoft Defender Antivirus ring deployment overview](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-ring-deployment)
