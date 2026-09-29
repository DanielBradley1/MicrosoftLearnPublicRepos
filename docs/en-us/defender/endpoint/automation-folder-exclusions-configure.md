<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/automation-folder-exclusions-configure -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Configure automation folder exclusions

Automation folder exclusions let you specify folders that [automated investigation and remediation](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations) skips in Microsoft Defender for Endpoint Plan 2. When an alert triggers an automated investigation, the investigation examines the evidence, reaches a verdict for each item, and then takes or recommends remediation actions based on your [automation level](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels). Excluding a folder tells these investigations to leave its contents alone, which is useful for directories that hold known-good files that would otherwise slow down or complicate an investigation.

An automation folder exclusion entry consists of the following elements:

| Element | Required? | Description |
| --- | --- | --- |
| Folder | Yes | Includes all subfolders. Supports a trailing wildcard, such as `c:\\old viruses*`, which matches `c:\\old viruses 20_6_2016`. |
| Extensions | No | One or more file extensions in the specified folder, separated by commas. |
| File names | No | One or more file names in the specified folder, separated by commas. Explicitly defining file names helps prevent an attacker from using an excluded folder to hide an exploit. |
| Description | Yes | A description of the exclusion. |

After you create an exclusion, attempts to collect or examine excluded files with live response fail with the error `File is excluded`. Automated investigations also ignore the excluded items.

You manage all automation folder exclusion settings on the **Automation folder exclusions** page in the [Microsoft Defender portal](https://security.microsoft.com) at [https://security.microsoft.com/securitysettings/endpoints/folder\_exclusions](https://security.microsoft.com/securitysettings/endpoints/folder_exclusions).

Automation folder exclusions apply to all devices onboarded to Defender for Endpoint. They affect only automated investigation and remediation. Excluded files are still subject to antivirus scans.

Note

In Microsoft Defender for Business, automated investigation and remediation is preconfigured and can't be customized, so automation folder exclusions aren't available.

For an overview of how automation folder exclusions fit alongside the other exclusion types in Defender for Endpoint, see [Automation folder exclusions](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview#automation-folder-exclusions).

## Prerequisites

You need to be assigned permissions before you can do the procedures in this article. You have the following options to assign the required permissions:

- [Microsoft Defender XDR Unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac):

  - *Create and manage exclusions*: **Authorization and settings/Security settings/Core Security settings \(manage\)**
  - *Read-only access to exclusions*: **Authorization and settings/Security settings/Core Security settings \(read\)**

- [Microsoft Defender for Endpoint role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-endpoint/assign-portal-access): The **Manage security settings in Security Center** permission. This model is available only to organizations created before February 2025.
- [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Security Administrator** or **Global Administrator**<sup>\*</sup> roles gives users the required permissions *and* permissions for other features in Microsoft 365.

  Important

  \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Add an automation folder exclusion

Do the following steps to add an automation folder exclusion:

1. On the **Automation folder exclusions** pane in the Defender portal at [https://security.microsoft.com/securitysettings/endpoints/folder\_exclusions](https://security.microsoft.com/securitysettings/endpoints/folder_exclusions), select **+ New folder exclusion**.
2. Configure the following settings that appear:

   - **Folder** \(required\): Enter the folder path, such as `c:\old viruses` or `c:\old viruses*`.
   - **Extensions**: Leave blank or enter one or more file extensions, such as `dll,exe,sys`.
   - **File names**: Leave blank or enter one or more file names, such as `app1.exe,app2.exe`.
   - **Description** \(required\): Enter descriptive text for the exclusion.


   When you're finished, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-add-internal.png) **Save**.

The **Automation folder exclusions** pane shows all details about the exclusion, including who created it and when.

## Edit an automation folder exclusion

On the **Automation folder exclusions** pane in the Defender portal at [https://security.microsoft.com/securitysettings/endpoints/folder\_exclusions](https://security.microsoft.com/securitysettings/endpoints/folder_exclusions), select **Edit** in the exclusion entry.

The same settings appear as when you created the exclusion, populated with the current values.

Update the settings, and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-add-internal.png) **Save**.

## Remove an automation folder exclusion

On the **Automation folder exclusions** pane in the Defender portal at [https://security.microsoft.com/securitysettings/endpoints/folder\_exclusions](https://security.microsoft.com/securitysettings/endpoints/folder_exclusions), select **Remove exclusion** in the exclusion entry.

In the confirmation dialog that opens, select **Delete**.

The **Automation folder exclusions** pane no longer lists the removed exclusion.

## Related content

- [Manage automation allowed/blocked lists](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview)
- [Manage automation file uploads](https://learn.microsoft.com/en-us/defender-endpoint/manage-automation-file-uploads)
- [Exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
