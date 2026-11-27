<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/open-ancient-legacy-formats-protected-view-disallow-editing?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-16 -->

# Open ancient legacy formats in Protected View and disallow editing

As a Microsoft 365 admin, you want to protect and secure your business environment. Baseline security mode helps you protect and secure your organization.

Ancient legacy file formats in Microsoft 365 apps are vulnerable to memory corruption-related security issues. To mitigate these risks, administrators can configure settings to open these outdated formats in **Protected View** with editing disabled. This approach prevents potential exploits while still allowing users to view the content without risk.

When this setting is turned on, affected legacy files open in Protected View with editing disabled. Users can view the contents of the file, but they can't edit the file in its original format or save changes back to the legacy format, even if the file is stored in a trusted location.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

Existing business processes, applications, or workflows that depend on editing affected files in their original format might also be disrupted.

In Excel, new external workbook links referencing ancient legacy formats will return a #BLOCKED error, and existing links will display the last successfully refreshed values but will no longer refresh.

## What users experience when opening an ancient legacy file

When a user opens an affected file:

- The file opens in **Protected View**.
- Office indicates that editing isn't allowed for the file.
- The option to enable editing isn't available.
- The user can't modify the file while it remains in the affected legacy format.
- The user can't save changes back to the original legacy format.
- These restrictions also apply when the file is stored in a trusted location.

To continue working with the content, save the file in a current Office file format and work with the converted copy.

Note

The notification displayed to users can vary depending on the Microsoft 365 app and version.

## Convert an ancient legacy file to a current format

If you need to edit an affected file, create a copy in a current Office file format.

1. Open the legacy file.
2. Review the file while it is open in **Protected View**.
3. Go to **File** > **Save As**.
4. Select a location for the converted file.
5. Choose an appropriate current file format. For example:

   - For Word documents, select Word Document \(\*.docx\).
   - For Excel workbooks without macros, select Excel Workbook \(\*.xlsx\).
   - For Excel workbooks that contain VBA macros that must be retained, use an appropriate macro-enabled format, such as Excel Macro-Enabled Workbook \(\*.xlsm\).

6. Save the file with a new name to preserve the original legacy file if it's still required.
7. Close the legacy file and continue working with the converted copy.

After conversion, review the new file to verify that its content and functionality have been preserved.

## Considerations when converting legacy files

Older Office file formats can contain features or content that aren't supported by current file formats. After converting a file, verify that the converted copy works as expected before replacing or archiving the original.

Depending on the file, review:

- Macros and add-ins.
- Formulas and named ranges.
- External workbook links and data connections.
- Embedded or linked objects.
- Charts, drawing objects, fonts, and formatting.
- Other application-specific features that might not be supported by the destination format.

When converting Excel files that contain VBA macros, don't save the file as *.xlsx* if the macros need to be retained. Use an appropriate macro-enabled format instead.

## Excel external workbook links

When this setting is enabled, Excel also restricts external workbook links that reference affected legacy file formats.

- New external links to affected file formats return a #BLOCKED error.
- Existing links retain the value from the last successful refresh but no longer refresh from the blocked file.
- Users can review affected links in the Workbook Links pane.

Convert the source workbook to a current Excel format and update the external link to reference the converted file.

## Ancient legacy file formats affected by this setting

The setting applies to the following file-format generations.

| Application | File-format generation |
| --- | --- |
| Word | Word 2 and earlier binary documents and templates |
| Word | Word 6.0 binary documents and templates |
| Word | Word 95 binary documents and templates |
| Excel | Excel 2 macrosheets and add-in files |
| Excel | Excel 3 macrosheets and add-in files |
| Excel | Excel 4 macrosheets and add-in files |
| Excel | Excel 2 worksheets |
| Excel | Excel 3 worksheets |
| Excel | Excel 4 worksheets |
| Excel | Excel 4 workbooks |

This setting doesn't currently include a corresponding ancient PowerPoint file-format category. PowerPoint 97-2003 formats are covered by the separate policy for [old legacy formats](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/open-old-legacy-formats-protected-view-disallow-editing?view=o365-worldwide).

Important

Don't rely only on a file name extension to determine whether a file is affected by this setting. Multiple generations of Word and Excel binary formats can use the same file name extension. The underlying file format determines which File Block policy applies.

### Assess impact before broad deployment

Important

A BSM impact report that shows no detected impact doesn't guarantee that enabling this setting won't affect users or business processes. Use the impact report as one input when assessing deployment readiness rather than as confirmation that the setting can be enabled broadly without impact.

The report might not identify every use of or dependency on legacy file formats. Before broad deployment, validate the setting with a representative group of users and business workflows, including workflows that rely on older Office files, shared or archived files, and applications or processes that depend on legacy Office file formats. Consider a phased deployment and monitor for unexpected impact before expanding the setting across your organization.

## Turn off setting in the Microsoft 365 admin center

If you have turned this setting on but need to revert to the default behaviors \(allowing trusted files to bypass Protected View and allowing users to override the editing block using Trust Center\), you can turn off the setting directly in the Microsoft 365 admin center.

1. Go to the Microsoft 365 admin center at [https://admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339) and select **Org settings**.
2. Select Baseline Security Mode, find the **Open ancient legacy formats in Protected View and disallow editing** setting, and switch the toggle to **Off**.

## Use Office Cloud Policy service

You can also make changes to the policy settings directly using the [Office Cloud Policy service](https://config.office.com/) if you need to modify the behavior or if you need to scope the setting to specific groups of users.

The following table contains the settings in Office Cloud Policy service that support this Baseline Security Mode setting. To revert to the default behavior, set these policies as not configured.

| Policy | Configuration Setting |
| --- | --- |
| File Block includes trusted files | Enabled  <br>  <br>This policy is enabled for Word, PowerPoint, Excel, and Visio. |
| File Block includes external link files | Enabled |
| Word 2 and earlier binary documents and templates | Open in Protected View |
| Word 6.0 binary documents and templates | Open in Protected View |
| Word 95 binary documents and templates | Open in Protected View |
| Excel 2 macrosheets and add-in files | Open in Protected View |
| Excel 3 macrosheets and add-in files | Open in Protected View |
| Excel 4 macrosheets and add-in files | Open in Protected View |
| Excel 2 worksheets | Open in Protected View |
| Excel 3 worksheets | Open in Protected View |
| Excel 4 worksheets | Open in Protected View |
| Excel 4 workbooks | Open in Protected View |
