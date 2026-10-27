<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/manage-inactive-files?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-21 -->

# Manage inactive files policy with SharePoint Advanced Management \(preview\)

Inactive files policies in SharePoint Advanced Management help administrators automatically archive eligible SharePoint files based on when they were last accessed. Use these policies to manage inactive files within sites that remain in use.

Microsoft 365 Archive provides the archive storage tier and file reactivation experience. SharePoint Advanced Management policies provide the rules and automation that select eligible files for archiving.

## Availability

Public preview is planned for October 2026. General availability is planned by the end of 2026. These dates are targets and may change.

The current preview is available only through PowerShell. Support through the SharePoint Admin Agent is planned before general availability.

This article describes a PowerShell-based workflow for SharePoint sites. It doesn't cover OneDrive policy configuration, inactive site policies, or Microsoft Purview retention policy configuration.

## Choose the right approach

| Approach | Use it when |
| --- | --- |
| Inactive files policy | You want to automatically archive eligible inactive files within SharePoint sites. |
| Inactive site policy | You want to identify and manage entire sites that are no longer active. |
| Manual file archiving | Users need to select and archive individual files or supported groups of files. |
| Microsoft Purview retention | You need to retain or delete content according to compliance requirements. |

Archiving changes the file's storage and access state; it doesn't replace retention requirements.

To archive retained SharePoint files by using Microsoft Purview retention policies or labels, see [Archiving retained SharePoint files](https://learn.microsoft.com/en-us/purview/retention-settings#archiving-retained-sharepoint-files).

For site-level governance, see [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management).

## Before you begin

Use PowerShell to configure and manage policies during the current preview. SharePoint Admin Agent support is planned before general availability.

Before deploying a policy, confirm:

- The public preview is available for your tenant.
- Your tenant has the required SharePoint Advanced Management entitlement.
- Your administrator account has the SharePoint Administrator or Global Administrator role.
- You're using Microsoft.Online.SharePoint.PowerShell version 16.0.27709.12000 or later.
- Your tenant meets the applicable Microsoft 365 Archive service and billing prerequisites.

For more information, see:

- [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management)
- [Connect to SharePoint Online PowerShell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
- [Set up Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-setup?view=o365-worldwide)

Manual file archiving and automatic policy archiving are separate controls. Disabling the user-facing Archive action doesn't prevent automatic policies from archiving files.

## Select an inactivity threshold

**Last access date \(LAD\)** is the recorded date a human last accessed a file. AI agent, application, script, and system access don't update it.

**How the policy uses LAD:** A file can qualify for archiving when its recorded LAD is earlier than the policy's inactivity cutoff. Other eligibility rules still apply.

A file can remain important even if it hasn't been edited recently. Select a threshold that reflects your organization's access patterns and business requirements.

The policy commands accept an inactivity threshold from 6 through 48 months. The default is 24 months.

Important

**July 2025 is a data-quality boundary, not an archiving restriction.** Older LADs still exist, and policies use them.

Human access before July 2025 might not have been captured, so a recorded LAD can make a file look inactive longer than it really was.

**Example:** Recorded LAD: 2022. Unrecorded human access: 2024. Policy cutoff: 2023. **The file can qualify for archiving** because the policy uses 2022.

For critical content, choose an inactivity period that falls entirely after July 2025. This provides a more complete observation period; it doesn't exclude files with older LADs. Review simulation results with site owners—simulation doesn't recover missing access history.

The examples below use 12 months to illustrate configuration. That value isn't a universal deployment recommendation.

## Configure scope and exclusions

Inactive files policies support these SharePoint scope types:

| Policy type | Scope |
| --- | --- |
| SelectedSites | Applies only to the SharePoint sites that you explicitly add. |
| AllSites | Applies broadly to eligible SharePoint sites, except sites that you explicitly exclude. |

A SelectedSites policy must have at least one included site before it can be activated.

Use inclusions only with SelectedSites policies. Use exclusions only with AllSites policies. Adding an inclusion to AllSites, or adding an exclusion to SelectedSites, returns an error.

A site must exist and be eligible for archiving before it can be associated with a policy. A single policy can contain a maximum of 1,000 associated sites. For SelectedSites policies, those associations are inclusions. For AllSites policies, those associations are exclusions.

A site exclusion affects future processing by that policy. It doesn't reactivate files already archived, reverse previous policy actions, or exempt the site from another archive policy or manual archiving method.

## Understand scale and throughput limits

Inactive files policies process at service-managed scale. Processing might span multiple runs depending on scope, file volume, service load, and eligibility results.

The following limits and guidance apply during preview:

| Measure | Value | Type |
| --- | ---: | --- |
| Sites scanned per policy | 100,000 sites | Hard limit |
| Files archived per day | 1-2 million files at current scale | Throughput guidance |
| Site associations per policy | 1,000 sites | Hard limit |

The files-archived value reflects current service scale and is throughput guidance, not a guarantee. Microsoft continues to invest in increasing throughput. Actual archive volume depends on how many scanned files are eligible, file state, built-in exclusions, site availability, throttling, service health, and policy configuration.

Note

Running multiple AllSites policies at the same time slows overall processing, because the policies compete for system resources.

## Configure file type filters

File type filters let you include specified extensions or exclude specified extensions. Built-in exclusions still apply regardless of those filters.

For example, create a selected-sites simulation policy that considers only Word documents and PDFs:

```powershell
New-SPOFileArchivePolicy -Name "FilteredFilesPreview" -PolicyType "SelectedSites" -FileTypeCriteria @(".docx", ".pdf") -IsWhatIfMode $true
```

To exclude extensions instead, use `-FileTypeExclusionCriteria`.

## Understand state and simulation mode

A policy's state and simulation setting are separate.

| State | IsWhatIfMode | Behavior |
| --- | --- | --- |
| Inactive | `$true` | Simulation is configured, but the policy isn't active. |
| Active | `$true` | Evaluate and report without archiving files. |
| Inactive | `$false` | Enforcement is configured, but the policy isn't active. |
| Active | `$false` | Archive files that qualify when the policy processes them. |

Creating a policy doesn't activate it. Likewise, activating a policy in simulation mode doesn't enable enforcement.

Simulation results are estimates, not a guarantee of the files or storage that will ultimately be archived. File activity, eligibility, policy configuration, and processing coverage can affect the outcome.

## Create a selected-sites simulation

The following steps use PowerShell, the only supported management experience in the current preview. SharePoint Admin Agent support is planned before general availability.

Start with a limited pilot. Inform the relevant site owners and agree on how results are reviewed before enabling enforcement.

Connect to your SharePoint admin endpoint:

```powershell
Connect-SPOService -Url "https://contoso-admin.sharepoint.com"
```

Create an inactive policy with simulation explicitly enabled:

```powershell
New-SPOFileArchivePolicy -Name "MarketingInactiveFilesPreview" -PolicyType "SelectedSites" -LastAccessDateCriteria 12 -FileTypeCriteria @(".docx", ".pdf") -IsWhatIfMode $true
```

List policies and identify the new policy's ID:

```powershell
Get-SPOFileArchivePolicy
```

Enter that ID, add the pilot site, and inspect the configuration:

```powershell
$policyId = [Guid](Read-Host "Enter the new policy ID")
Add-SPOSiteToFileArchivePolicy -PolicyId $policyId -Site "https://contoso.sharepoint.com/sites/marketing"
Get-SPOFileArchivePolicySites -PolicyId $policyId
Get-SPOFileArchivePolicy -PolicyId $policyId
```

Activate simulation:

```powershell
Set-SPOFileArchivePolicy -PolicyId $policyId -State "Active"
```

Activation allows the policy to process. It doesn't guarantee immediate completion or an immediately available report.

## Create an all-sites simulation with exclusions

Use AllSites only when broad tenant scope is intentional. Start in simulation mode and identify sites that must be exempt before activation.

Create the policy:

```powershell
New-SPOFileArchivePolicy -Name "TenantInactiveFilesPreview" -PolicyType "AllSites" -LastAccessDateCriteria 24 -IsWhatIfMode $true
```

List policies and enter the new policy's ID:

```powershell
Get-SPOFileArchivePolicy
$policyId = [Guid](Read-Host "Enter the new policy ID")
```

Add a site exclusion by using `-Exclude`:

```powershell
Add-SPOSiteToFileArchivePolicy -PolicyId $policyId -Site "https://contoso.sharepoint.com/sites/legal" -Exclude
```

Review the policy and its exclusions before activation:

```powershell
Get-SPOFileArchivePolicySites -PolicyId $policyId
Get-SPOFileArchivePolicy -PolicyId $policyId
```

Activate simulation only after confirming the intended broad scope and exclusions:

```powershell
Set-SPOFileArchivePolicy -PolicyId $policyId -State "Active"
```

For an AllSites policy, `Get-SPOFileArchivePolicySites` returns the excluded sites that are exempt from that policy.

## Review simulation results

Retrieve the policy's run reports:

```powershell
Get-SPOFileArchivePolicyReport -PolicyId $policyId
```

The report command returns run history for the preceding 12 months. Simulation reports describe files and storage that would have been archived.

Before enabling enforcement, review:

- Policy configuration
- Processing coverage
- Projected impact
- Outcome reasons
- Business requirements
- Whether processing spans multiple runs

Don't interpret an empty report or a zero count as proof that the entire intended scope was evaluated.

Don't assume that an enforcement policy archives precisely the same set of files that the simulation evaluated.

Important

If your policy covers more than 100,000 sites, create a new policy with the same criteria, scope, and site inclusions or exclusions when you're ready to archive files. Set `IsWhatIfMode` to `$false` on the new policy. Switching the existing simulation policy to archiving resumes from its previous processing position instead of starting over, so sites already evaluated in simulation might be skipped.

## Monitor policy activity

Use policy reports to review processing outcomes. Use the Microsoft 365 audit log to investigate file archive activity.

The Archived file \(FileArchived\) activity distinguishes user and system actions. Automatic policy archive events include the policy ID, policy version, and file's last access date.

For details, see [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities).

Keep the configuration used for a historical run separate from the policy's current settings when interpreting results.

## Change policy scope or stop a policy

Use `Set-SPOFileArchivePolicy` to update supported settings. Parameters you omit retain their existing values.

To make a policy inactive:

```powershell
Set-SPOFileArchivePolicy -PolicyId $policyId -State "Inactive"
```

To remove a site association:

```powershell
Remove-SPOSiteToFileArchivePolicy -PolicyId $policyId -Site "https://contoso.sharepoint.com/sites/marketing"
```

The effect depends on the policy type:

- For SelectedSites, removing an inclusion reduces future policy coverage.
- For AllSites, removing an exclusion expands future policy coverage to that site.

You can't remove the final included site from an active SelectedSites policy. Make the policy inactive first or add another included site.

To preview policy removal, then remove it intentionally:

```powershell
Remove-SPOFileArchivePolicy -PolicyId $policyId -WhatIf
Remove-SPOFileArchivePolicy -PolicyId $policyId
```

Here, `-WhatIf` previews the removal command. It's different from the policy's persistent `IsWhatIfMode` setting.

Removing a policy soft-deletes the policy; it doesn't delete or reactivate the files it archived. Accessing archived files still requires reactivation.

## Troubleshoot unexpected results

| If you notice... | Try this |
| --- | --- |
| The policy hasn't started processing. | Check that the policy is active and includes the sites you expect. A `SelectedSites` policy needs at least one included site; an `AllSites` policy skips excluded sites. Also confirm preview availability, your SharePoint Advanced Management entitlement, and the Archive prerequisites. |
| The policy runs, but no files are archived. | Check `IsWhatIfMode` first. If it's `$true`, the policy reports results without archiving files. Otherwise, review the inactivity threshold, file type filters, and report outcome reasons to see why files were skipped. Built-in restrictions still apply. |
| A file you expected to stay active qualifies for archiving. | Compare the file's last human access date with the policy's inactivity threshold. AI agent and system access don't update LAD. If the recorded LAD is before July 2025, missing human access history can make the file appear inactive for longer than it was. See [Select an inactivity threshold](#select-an-inactivity-threshold) before enabling archiving. |
| Archive results don't match the simulation. | Compare the settings and sites processed in each run. Files might have been accessed or become ineligible since the simulation. Review the outcome reasons for differences. |
| A report lists files that weren't archived. | Check what the count represents: files evaluated, skipped, failed, or successfully archived. The outcome reasons help explain what happened. |
| Files on an excluded site are still archived. | Confirm that you added the exclusion to the correct `AllSites` policy. Check whether another policy or a user archived the files, or whether they were archived before you added the exclusion. Excluding a site doesn't reactivate files. |
| Files are still archived after you stop the policy. | Stopping a policy doesn't reactivate files it already archived. Reactivate those files when you need to access them. |
| The site's storage usage hasn't gone down. | File archiving changes tenant storage accounting, not the site's quota usage. The site storage figure won't decrease because files were archived. |
| A OneDrive site isn't processed. | OneDrive sites aren't supported in this preview. Use a SharePoint site for your pilot. |

## Related commands

- [New-SPOFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/new-spofilearchivepolicy)
- [Set-SPOFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spofilearchivepolicy)
- [Get-SPOFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spofilearchivepolicy)
- [Remove-SPOFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/remove-spofilearchivepolicy)
- [Add-SPOSiteToFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/add-spositetofilearchivepolicy)
- [Remove-SPOSiteToFileArchivePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/remove-spositetofilearchivepolicy)
- [Get-SPOFileArchivePolicySites](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spofilearchivepolicysites)
- [Get-SPOFileArchivePolicyReport](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spofilearchivepolicyreport)
