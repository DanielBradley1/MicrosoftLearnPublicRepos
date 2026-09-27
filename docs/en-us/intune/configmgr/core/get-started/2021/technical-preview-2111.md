<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2111 -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Features in Configuration Manager technical preview version 2111

*Applies to: Configuration Manager \(technical preview branch\)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2111. Install this version to update and add new features to your technical preview site.

Review the [technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Improvements to the Windows servicing dashboard

We now display a **Windows 11 Latest Feature Updates** chart in the **Windows Servicing** dashboard. The new chart makes it easier to determine how many of your Windows 11 clients are on the latest feature update. To display the dashboard, go to **Software Library** > **Overview** > **Windows Servicing**.

![Screenshot of the Windows servicing dashboard. The Windows 11 Latest Feature Updates chart is displayed in the dashboard](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/media/10579996-windows-servicing-dashboard.png)

## Co-management Eligible Devices collection

There's a new built-in device collection for **Co-management Eligible Devices**. The **Co-management Eligible Devices** collection uses incremental updates and a daily full update to keep the collection up to date.

## Improvement to app groups

This release resolves one of the [known issues for app groups from version 2110](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2110#bkmk_appgroups). View and managing app groups in the Microsoft Intune admin center doesn't require an elevated role. It honors permissions and scopes as defined in Configuration Manager. For example, your user account requires the **Approve** permission on an app group to approve it for installation from the admin center. This behavior is consistent with applications.

## Improvement to task sequence deployment type

Consider the following scenario:

- An application has a [task sequence deployment type](https://learn.microsoft.com/en-us/intune/configmgr/apps/get-started/creating-windows-applications#bkmk_tsdt).
- It's deployed as available.
- A device has maintenance windows defined.
- A user on the device runs the deployment in Software Center outside of a maintenance window.

Configuration Manager honors the user's intent to install the application, even though there's no available maintenance window. Previously, when the task sequence ran, the **Restart Computer** step would fail because of the maintenance window.

Based on your feedback, this step now ignores maintenance windows only when the task sequence is run as an app deployment type.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](https://learn.microsoft.com/en-us/powershell/sccm/overview).

### New cmdlets for orchestration groups

For more general information about this feature, see [Orchestration groups in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/orchestration-groups).

#### Get-CMOrchestrationGroup

Use this cmdlet to get an orchestration group object by name or ID. You can use this object with [Invoke-CMOrchestrationGroup](#invoke-cmorchestrationgroup), [Remove-CMOrchestrationGroup](#remove-cmorchestrationgroup), or [Set-CMOrchestrationGroup](#set-cmorchestrationgroup).

#### Invoke-CMOrchestrationGroup

Use this cmdlet to [start orchestration](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/create-orchestration-groups#start-orchestration).

```powershell
Get-CMOrchestrationGroup -Name $OGName | Invoke-CMOrchestrationGroup -IgnoreServiceWindow $true
```

#### New-CMOrchestrationGroup

Use this cmdlet to create a new orchestration group.

```powershell
New-CMOrchestrationGroup -Name $Script:OGName -SiteCode $SiteCode -Description "Desc" -OrchestrationType Percentage -OrchestrationValue 10 -OrchestrationTimeOutMin 300 -MaxLockTimeOutMin 55 -PreScript "PreScript" -PreScriptTimeoutSec 30 -PostScript "PostScript" -PostScriptTimeoutSec 55 -MemberResourceIds $Script:device.ResourceID
```

#### Remove-CMOrchestrationGroup

Use this cmdlet to remove the specified orchestration group.

#### Set-CMOrchestrationGroup

Use this cmdlet to configure an orchestration group.

### Deprecated cmdlets

The **Remove-CMDeploymentTypeSupersedence** cmdlet for deployment type supersedence is deprecated and may be removed in a future release. Instead, use the new [Set-CMApplicationSupersedence](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2109#set-cmapplicationsupersedence) cmdlet.

### Modified cmdlets

#### Add-CMDeviceCollectionDirectMembershipRule

For more information, see [Add-CMDeviceCollectionDirectMembershipRule](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Add-CMDeviceCollectionDirectMembershipRule).

**Bugs that were fixed**

Fixed an issue when adding a rule by resource object.

#### Get-CMClientSetting

For more information, see [Get-CMClientSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Get-CMClientSetting).

**Non-breaking changes**

Added support to return the value for the [Disable Deadline Randomization](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-settings#disable-deadline-randomization) setting in the Computer Agent group.

#### New-CMBoundary

For more information, see [New-CMBoundary](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/New-CMBoundary).

**Non-breaking changes**

Added new parameter **ValueStartsWith** to support [Improvements to VPN boundary types](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2109#bkmk_vpn).

#### New-CMTSStepApplyWindowsSetting

For more information, see [New-CMTSStepApplyWindowsSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/New-CMTSStepApplyWindowsSetting).

**Breaking changes**

Removed the following unsupported parameters:

- **MaximumConnection**
- **ServerLicensing**

#### New-CMTSPartitionSetting

For more information, see [New-CMTSPartitionSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/New-CMTSPartitionSetting).

**Non-breaking changes**

Set default value for AssignVolumeLetter.

#### New-CMTSStepPrestartCheck

For more information, see [New-CMTSStepPrestartCheck](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/New-CMTSStepPrestartCheck).

**Non-breaking changes**

Added new parameters for [TPM existence check](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2110#bkmk_tpm):

- **CheckTpmEnabled**
- **CheckTpmActivated**

#### New-CMWdacSetting

For more information, see [New-CMWdacSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/New-CMWdacSetting).

**Non-breaking changes**

Added support for new platform rules for Windows 10 ARM64 and Windows 10 multi-session.

#### Remove-CMPersistentUserSettingsGroup

For more information, see [Remove-CMPersistentUserSettingsGroup](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Remove-CMPersistentUserSettingsGroup).

**Bugs that were fixed**

Fixed a query issue when remove settings group by name.

#### Set-CMTSStepPrestartCheck

For more information, see [Set-CMTSStepPrestartCheck](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Set-CMTSStepPrestartCheck).

**Non-breaking changes**

Added new parameters for [TPM existence check](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2110#bkmk_tpm):

- **CheckTpmEnabled**
- **CheckTpmActivated**

#### Set-CMBoundary

For more information, see [Set-CMBoundary](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Set-CMBoundary).

**Non-breaking changes**

Added new parameter **ValueStartsWith** to support [Improvements to VPN boundary types](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2109#bkmk_vpn).

#### Set-CMDistributionPoint

For more information, see [Set-CMDistributionPoint](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Set-CMDistributionPoint).

**Non-breaking changes**

Added new parameter **EnableMaintenanceMode** to support to manage [maintenance mode](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_maint).

#### Set-CMSoftwareUpdatePoint

For more information, see [Set-CMSoftwareUpdatePoint](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdatePoint).

**Bugs that were fixed**

Fixed an issue with regular expression processing when trying to clear the WSUS access account from a software update point.

#### Set-CMTSStepApplyWindowsSetting

For more information, see [Set-CMTSStepApplyWindowsSetting](https://learn.microsoft.com/en-us/powershell/module/configurationmanager/Set-CMTSStepApplyWindowsSetting).

**Breaking changes**

Removed the following unsupported parameters:

- **MaximumConnection**
- **ServerLicensing**

## Next steps

For more information about installing or updating the technical preview branch, see [Technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview).

For more information about the different branches of Configuration Manager, see [Which branch of Configuration Manager should I use?](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/which-branch-should-i-use).
