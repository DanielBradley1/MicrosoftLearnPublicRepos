<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/open-old-legacy-formats-protected-view-disallow-editing?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Open legacy formats in Protected View and save as modern format

As a Microsoft 365 admin, you want to protect and secure your business environment. **Baseline security mode** helps you protect and secure your organization.

Many legacy file formats in Microsoft 365 apps, such as older Word, Excel, and PowerPoint files, are prone to memory corruption vulnerabilities. By opening legacy formats in **Protected View**, you can minimize the risk of malicious code execution, while allowing users to edit their content safely.

## Expected user impact

When this setting is turned on, legacy file formats open in Protected View, even if saved in a trusted location. Users can choose to edit the files and save them to a modern file format, but they are blocked from saving in old legacy formats. In Excel, new external workbook links referencing old legacy formats return a #BLOCKED error, and existing links display the last successfully refreshed values but won't refresh.

When a user opens an affected file, the file opens in Protected View, and **Enable Editing** is available. After the user selects **Enable Editing**, they can edit the file, but they can't save their changes in the original legacy format. To keep their changes, they must save the file in a current format. For Excel 97-2003 add-in files, saving in the legacy format is blocked. Business processes, apps, or workflows that save or update files in their original legacy format might also be disrupted.

Note

The message that users see when they open or try to save an affected file can vary depending on the Microsoft 365 app and version.

## Remediation

To continue working with an affected file, users can save a copy of the file in a current format:

1. Open the file. The file opens in Protected View.
2. If you want to make changes before you convert the file, select **Enable Editing**.
3. Select **File** > **Save As**, and then choose a location.
4. In the file type list, select a current format:

   - Word: For documents, select Word Document \(*.docx\). For templates, select Word Template \(*.dotx\). If the file contains macros you need to keep, select Word Macro-Enabled Document \(*.docm\) or Word Macro-Enabled Template \(*.dotm\).
   - Excel: For workbooks that don't contain macros, select Excel Workbook \(*.xlsx\). For templates, select Excel Template \(*.xltx\). If the file contains macros you need to keep, select Excel Macro-Enabled Workbook \(*.xlsm\) or Excel Macro-Enabled Template \(*.xltm\). For add-in files, select Excel Add-in \(\*.xlam\).
   - PowerPoint: For presentations, select PowerPoint Presentation \(*.pptx\). For shows, select PowerPoint Show \(*.ppsx\). For templates, select PowerPoint Template \(*.potx\). If the file contains macros you need to keep, select PowerPoint Macro-Enabled Presentation \(*.pptm\). For add-in files, select PowerPoint Add-in \(\*.ppam\).

5. To keep the original file unchanged, enter a new file name, and then select **Save**.
6. Close the original file and continue working in the converted copy.

## Conversion considerations

After converting a file, review the converted copy before replacing or archiving the original. Depending on the file, verify that macros, add-ins, formulas, named ranges, external links, embedded or linked objects, charts, formatting, animations, and other app-specific functionality work as expected. Files that were opened through a legacy converter might need extra review, because content might not convert exactly.

A converted file has a new file name extension. Update anything that refers to the original file by name, such as hyperlinks, shortcuts, macros, scripts, scheduled tasks, and other apps or processes that open the file.

If an Excel workbook has external links to an affected file, convert the source file to a current Excel format, verify the converted workbook, and then update the link to reference the converted file.

## Format scope

The following legacy file formats open in Protected View:

- Word 2007 and later Binary Documents and Templates
- Word 2003 Binary Documents and Templates
- Word 2003 and Plain XML Documents
- Word XP Binary Documents and Templates
- Word 2000 Binary Documents and Templates
- Word 97 Binary Documents and Templates
- Legacy Converters for Word
- PowerPoint 97-2003 Presentations, Shows, Templates, and Add-in Files
- Legacy Converters for PowerPoint
- Excel 97-2003 Add-in Files
- Excel 97-2003 Workbooks and Templates
- Excel 95-97 Workbooks and Templates
- Excel 95 Workbooks
- Legacy Converters for Excel

These formats are defined by the underlying Office file-format generation, not by the file name extension. Different generations of Word, Excel, and PowerPoint binary formats can use the same file name extension, so don't rely only on the extension to identify affected files.

Older Word and Excel formats, such as Word 95 and earlier and Excel 4 and earlier, aren't covered by this setting. Those formats are covered by a separate setting that opens files in Protected View and doesn't allow editing. For more information, see [Open ancient legacy formats in Protected View and disallow editing](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/open-ancient-legacy-formats-protected-view-disallow-editing?view=o365-worldwide).

## Deployment readiness

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

Important

An impact report that shows zero impact for this setting doesn't guarantee that turning on the setting won't affect users or business processes. Use the impact report as one input to your deployment decision, not as confirmation that the setting is safe to turn on across your organization.

The impact report might not identify every dependency on legacy file formats. This setting applies to more formats than the setting for ancient legacy formats, including PowerPoint files, so review its impact carefully. Before you turn on this setting broadly, validate it with a representative group of users and business workflows. Include workflows that use older Word, Excel, or PowerPoint files, shared or archived files, Excel workbooks with external links, and apps or processes that open, save, or generate legacy files. Consider a phased rollout and monitor for unexpected impact before you expand the rollout. You can use Office Cloud Policy service to scope the setting to specific groups of users, or to allow specific legacy formats to bypass Protected View while dependencies are addressed.

### Turn off setting in the Microsoft 365 admin center

If you have turned this setting on but need to revert to the default behaviors \(not opening files in Protected View, allowing files to be saved in these formats, and allowing external workbook links to reference files\), you can turn off the Baseline Security Mode setting directly in the Microsoft 365 admin center.

1. Go to the Microsoft 365 admin center at [https://admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339) and select Org settings.
2. Select Baseline Security Mode, find the **Open old legacy formats in Protected View and save as modern format**, and switch the toggle to **Off**.

### Use Office Cloud Policy service

You can make changes to the policy settings directly using the [Office Cloud Policy service](https://config.office.com/) if you need to modify the behavior- for example, allowing files in a certain old legacy format to bypass Protected View while continuing to open all other old legacy format files in **Protected View** or if you need to scope the setting to specific groups of users.

The following table contains the settings in Office Cloud Policy service that support this Baseline Security Mode setting. To revert to the default behavior, set these policies as not configured.

| Policy | Configuration Setting |
| --- | --- |
| File Block includes trusted files | Enabled  <br>  <br>This policy is enabled for Word, PowerPoint, Excel, and Visio. |
| File Block includes external link files | Enabled |
| Word 2007 and later binary documents and templates | Allow editing and open in Protected View |
| Word 2003 and plain xml documents | Allow editing and open in Protected View |
| Word XP binary documents and templates | Allow editing and open in Protected View |
| Word 2000 binary documents and templates | Allow editing and open in Protected View |
| Word 97 binary documents and templates | Allow editing and open in Protected View |
| Legacy converters for Word | Allow editing and open in Protected View |
| PowerPoint 97-2003 presentations, shows, templates and add-in files | Allow editing and open in Protected View |
| Legacy converters for PowerPoint\*\* | Allow editing and open in Protected View |
| Excel 97-2003 add-in files | Save blocked |
| Excel 97-2003 workbooks and templates | Allow editing and open in Protected View |
| Excel 95-97 workbooks and templates | Allow editing and open in Protected View |
| Excel 95 workbooks | Allow editing and open in Protected View |
| Legacy converters for Excel | Allow editing and open in Protected View |
