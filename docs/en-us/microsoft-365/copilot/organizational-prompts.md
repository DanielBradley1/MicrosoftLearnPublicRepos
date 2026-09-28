<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/organizational-prompts -->
<!-- Sitemap-Last-Modified: 2026-09-21 -->

# Organizational prompts overview

**Organizational prompts** are Microsoft Copilot prompts that your organization creates and publishes for their end users. Administrators can create, view, update, delete, import, and publish prompts so they're shared with users in your organizations. When the prompts are published, they're displayed to users in [Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/overview?toc=/microsoft-365/copilot/toc.json&bc=/microsoft-365/copilot/context/breadcrumb/toc.json), [Microsoft Edge](https://learn.microsoft.com/en-us/deployedge/), and [Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/). As your users type in Copilot, organizational prompts are automatically suggested.

This article explains:

- How organizational prompts work.
- How to create, import, and manage organizational prompts.
- Where users can see organizational prompts.
- How to review analytics for organizational prompts.

## Prerequisites

To manage, create, update, edit, import, and delete organizational prompts, use one of the following roles, or a role with equivalent permissions:

- [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator)
- [Search Editor](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#search-editor)

For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## View and manage organizational prompts in the admin center

You can publish up to 1,000 organizational prompts in your tenant. It typically takes about 3 hours for prompts to display in the [prompt lab](#prompt-lab). To view and manage your organizational prompts:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts**.
3. View your list of organizational prompts.  
     
   Filter or update the list with the following options:

   - **Search:** Use the search box to find prompts by title or content.
   - **Sort:** Sort the list by any column header.
   - **Refresh list**: After you create, edit, or delete prompts, refresh to see the latest list.


   The following actions are available for prompts:


   - [Create prompt](#create-organizational-prompts)
   - [Edit](#edit-an-organizational-prompt)
   - [Delete](#delete-an-organizational-prompt)
   - [Export all prompts](#export-all-organizational-prompts)
   - [Import prompts](#import-prompts-in-bulk)
   - [Pin](#pin-an-organizational-prompt)

## Create organizational prompts

Create prompts manually or through [bulk import](#import-prompts-in-bulk). To manually create a prompt:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts** to display the list of organizational prompts.
3. Select **Create prompt**.
4. Fill in the [prompt fields](#prompt-fields-reference) for your organizational prompt.
5. Select **Publish** to save and publish the prompt to your tenant. It typically takes about 3 hours for prompts to display in the [prompt lab](#prompt-lab).

### Localization for organizational prompts

Admins can add prompts in any language by using the **Language** field on the prompt. Automatic translation or conversion to other languages isn't available currently. If your organization needs prompts in multiple languages, create a separate prompt for each language.

## Edit an organizational prompt

To edit an organizational prompt:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts** to display the list of organizational prompts.
3. Select the organizational prompt you want to change, then select **Edit**.
4. Change the [prompt fields](#prompt-fields-reference).
5. Select **Save** to publish the edited prompt to your tenant. It typically takes about 3 hours for changes to display in the [prompt lab](#prompt-lab).

[![Screenshot of the Microsoft 365 admin center organizational prompts list showing prompts list with one of the prompts pinned.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/organizational-prompts/11674258-organizational-prompts.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/organizational-prompts/11674258-organizational-prompts.png#lightbox)

## Pin an organizational prompt

Pin frequently used or priority prompts to the top of the list to display them to end users in Copilot. These prompts are displayed as [suggested prompts in Copilot Chat](#suggested-prompts-in-microsoft-copilot-chat). You can pin up to four prompts.

There are two ways to pin a prompt. In the organizational prompts list, select the prompt you want to pin, then either:

- Select the unpinned icon in the prompt's row to switch it to pinned.
- Select **Pin prompt** from the more options menu \(**...**\).

To unpin a prompt, select the prompt and choose **Unpin prompt** from the more options menu \(**...**\), or select the pinned icon to switch it to unpined.

## Delete an organizational prompt

To delete a single organizational prompt:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts** to display the list of organizational prompts.
3. To delete a prompt, select it, then choose **Delete**.

To delete multiple organizational prompts:

If you'd like to delete multiple prompts at once, select the checkboxes next to the prompts you want to delete, then choose **Delete**.

Warning

Deletion is permanent. Save a copy of the prompt fields before deleting if you might need to restore it, or [export all prompts](#export-all-organizational-prompts).

## Import prompts in bulk

When you have multiple prompts to publish, you can import prompts. The file size limit for import is 5 MB and you can import up to 100 prompts at a time. If you have more than 100 prompts, split them across multiple files. For example, you might use bulk import when migrating from a prompt library spreadsheet or for rolling out a department-wide catalog.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts** to display the list of organizational prompts.
3. Select **Import prompts**, which opens the flyout to import prompts.
4. Select **Download prompts template \(.csv\)** and save the `prompt-import-template.csv` file.
5. Fill in one row per prompt. Use the [prompt fields reference](#prompt-fields-reference) to understand the required fields and character limits.
6. Save the file as a UTF-8 encoded CSV. In Microsoft Excel, this file type is **CSV UTF-8 \(comma delimited\)\(\*.csv\)**.
7. Upload and review the validation preview.

## Export all organizational prompts

You can export all organizational prompts to a CSV file. Exporting is useful for backing up your prompts or for making bulk edits to prompts. To export all organizational prompts to a CSV file:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) if needed.
2. Expand **Copilot** and select **Prompts** to display the list of organizational prompts.
3. Select **Export all prompts**. If you're using the file to make bulk edits, the exported file includes columns that aren't used for import, such as `Last Updated`. Before importing, remove columns that aren't listed in [prompt-import-template.csv](#prompt-fields-reference).

## Validation errors

When you submit a prompt or batch of prompts, you might encounter the following errors:

| Error | Meaning |
| --- | --- |
| Prompt basic validation failed | The prompt is missing required fields or has an invalid structure. |
| Tenant prompts published items limit has been reached | The tenant has reached the 1,000-prompt limit. Delete unused prompts before publishing more. |
| Failed to batch insert prompt items to SDS collection | Server-side failure during a batch insert. Retry the request. If the issue persists, file a support ticket. |

## Where organizational prompts are displayed to users

Organizational prompts appear in three places inside Microsoft Copilot.

### Suggested prompts in Microsoft Copilot Chat

When users open Microsoft Copilot Chat, a button titled **Suggested** appears on the home page. Selecting **Suggested** opens the pinned prompts. At the bottom of the pinned prompts list, **Discover more prompts like these** takes users to suggested prompts in the prompt lab. If you'd like to change the logo that's displayed, edit the **Square logo** in **Company branding** from the [Microsoft Entra admin center](https://entra.microsoft.com/). For more information, see [Configure your company branding](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-customize-branding).

![Screenshot of the Copilot home interface showing the suggested button with a list of the four pinned organizational prompts.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/organizational-prompts/11674258-organizational-prompts-copilot-interface.png)

### Prompt lab

The prompt lab displays all organizational prompts available to the user. Users can:

- Search prompts by keyword.
- Filter by task type.
- Filter by department.

Selecting a prompt places the prompt into the Copilot Chat message box but doesn't submit it. Users can modify the prompt easily before they submit it.

[![Screenshot of the Suggested tab in the prompt lab with organizational prompts listed.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/organizational-prompts/11674258-prompt-lab.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/organizational-prompts/11674258-prompt-lab.png#lightbox)

### Autosuggest in the Copilot input box

When users start typing in the Copilot message box, matching organizational prompts appear as typeahead suggestions. For users who already know the prompt they want, using autosuggest is the quickest option.

## Review analytics for organizational prompts

Admins can view metrics for each prompt in the admin center to evaluate prompt performance and adoption. This data helps identify prompts that users aren't adopting so you can modify them. It also helps you find top-performing prompts to promote. You can review this data for the last 7, 14, or 28 days. The following analytics are available for organizational prompts:

- **Active users**: The number of distinct users who use this prompt.
- **Submissions**: The total number of times the prompt is submitted to Copilot.

## Prompt fields reference

Use the chart to understand the required fields and character limits when creating, importing, or editing organizational prompts.

| Field | Required | Character Limit | Notes | prompt-import-template.csv column |
| --- | --- | --- | --- | --- |
| Title | Yes | 35 | The label users see in the prompt lab cards. | `Title` |
| Display prompt | Yes | 132 | Short title shown on pill suggestions, on prompt lab cards, and in autosuggestions. | `Display Prompt` |
| Prompt | Yes | 8000 | The actual prompt sent to Copilot when the user selects this prompt. | `Prompt Text` |
| Language | Yes | - | The language the prompt is written in. Automatic translation isn't supported. For more information, see [Localization for organizational prompts](#localization-for-organizational-prompts).  <br>  <br>When [importing prompts](#import-prompts-in-bulk), use the values from the **View all supported locales** link in the import prompts flyout. Examples of values for `Locale` include `en-US`, `es-ES`, and `ja-JP`. | `Locale` |
| Task type | Yes | - | Used to organize prompts and to power task-type filters in the prompt lab.  <br>  <br>When [importing prompts](#import-prompts-in-bulk), verify the values from the **View all supported task types** link import prompts flyout. Examples of values for `Task Type` include `Analyze`, `Create`, and `Edit`. | `Task Type` |
| Department | No | 120 | Free-form text. Used to organize prompts and to power department filters in the prompt lab. | `Department` |
| Supported apps | Yes | - | The Copilot surfaces where the prompt should appear \(for example, Copilot web, Copilot work\). | `Products` |
| Description | No | 200 | Internal context for other admins; not shown to end users. | `Description` |
