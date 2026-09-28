<!-- Source: https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-restore -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Bulk restore deleted users in Microsoft Entra ID

## Overview

Microsoft Entra ID supports bulk user restore operations and downloading lists of users, groups, and group members.

## Understand the CSV template

Download and fill in the CSV template to help you successfully restore Microsoft Entra users in bulk. The CSV template you download might look like this example:

![Screenshot of spreadsheet for uploading and call-outs explaining the purpose and values for each row and column.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-restore/understand-template.png)

### CSV template structure

The rows in a downloaded CSV template are as follows:

- **Version number**: The first row containing the version number \(for example, `version:v1.0`\) must be included in the upload CSV. If your downloaded template includes this row, don't remove or modify it.
- **Column headings**: The format of the column headings is <*Item name*> \[PropertyName\] <*Required or blank*>. For example, `Object ID [objectId] Required`. Some older versions of the template might have slight variations.
- **Examples row**: The template might include a row of example values for each column. You must remove the examples row and replace it with your own entries.

Note

CSV template formats vary by operation. Some templates, such as bulk create or delete users, include `version:v1.0` as the first row. Other templates, such as group member operations, start with column headers. Download the template for your specific operation from the portal. Don't add a version row or any other row that isn't in the downloaded template. Keep any version row and column header row unchanged.

### Example CSV file

Here's an example of a completed CSV file ready for upload:

```csv
version:v1.0
Object ID [objectId] Required
00aa00aa-bb11-cc22-dd33-44ee44ee44ee
11bb11bb-cc22-dd33-ee44-55ff55ff55ff
22cc22cc-dd33-ee44-ff55-66aa66aa66aa
```

### Additional guidance

- Keep any version row and column header row in the upload template exactly as downloaded, or the upload can't be processed.
- The required columns are listed first.
- We don't recommend adding new columns to the template. Any additional columns you add are ignored and not processed.
- We recommend that you download the latest version of the CSV template as often as possible.

## To bulk restore users

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Select Microsoft Entra ID.
3. Select **Users** > **All users** > **Deleted**.
4. On the **Deleted users** page, select **Bulk restore** to upload a valid CSV file of properties of the users to restore.

   ![Screenshot of selecting the bulk restore command on the Deleted users page.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-restore/bulk-restore.png)
5. Open the CSV template and add a line for each user you want to restore. The only required value is **ObjectID**. Then save the file.

   ![Screenshot of selecting a local CSV file in which you list the users you want to add](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-restore/upload-button.png)
6. On the **Bulk restore** page, under **Upload your csv file**, browse to the file. When you select the file and select **Submit**, validation of the CSV file starts.
7. When the file contents are validated, you see **File uploaded successfully**. If there are errors, you must fix them before you can submit the job.
8. When your file passes validation, select **Submit** to start the bulk operation that restores the users.
9. When the restore operation completes, you see a notification that the bulk operation succeeded.

If you experience errors, you can download and view the results file on the **Bulk operation results** page. The file contains the reason for each error. The file submission must match the provided template and include the exact column names.

For more information about bulk operations limitations, see [Bulk restore service limits](#bulk-restore-service-limits).

## Check status

You can see the status of all of your pending bulk requests in the **Bulk operation results** page.

[![Screenshot of checking the status in the Bulk Operations Results page.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-restore/bulk-center.png)](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-restore/bulk-center.png#lightbox)

Next, you can check to see that the users you restored exist in the Microsoft Entra organization via either Microsoft Entra ID or PowerShell.

## View restored users in the Microsoft Entra admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Select Microsoft Entra ID.
3. Under **Manage**, select **Users** > **All users**.
4. Under **Show**, select **All users** and verify that the users you restored are listed.

### View users with PowerShell

Run the following command:

```PowerShell
Get-MgUser -Filter "UserType eq 'Member'"
```

You should see that the users that you restored are listed.

Note

Azure AD and MSOnline PowerShell modules are deprecated as of March 30, 2024. To learn more, read the [deprecation update](https://techcommunity.microsoft.com/t5/microsoft-entra-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270). After this date, support for these modules are limited to migration assistance to Microsoft Graph PowerShell SDK and security fixes. The deprecated modules will continue to function through March, 30 2025.

We recommend migrating to [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview) to interact with Microsoft Entra ID \(formerly Azure AD\). For common migration questions, refer to the [Migration FAQ](https://learn.microsoft.com/en-us/powershell/azure/active-directory/migration-faq). *Note:* Versions 1.0.x of MSOnline may experience disruption after June 30, 2024.

## Bulk restore service limits

Note

When performing bulk operations, such as import or create, you can encounter a problem if the bulk operation doesn't complete within the hour. To work around this issue, we recommend splitting the number of records processed per batch. For example, before starting an export you could limit the result set by filtering on a group type or user name to reduce the size of the results. By refining your filters, essentially you limit the data returned by the bulk operation. For more information, see [Bulk operations service limitations](https://learn.microsoft.com/en-us/entra/fundamentals/bulk-operations-service-limitations).

## Next steps

- [Bulk import users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-add)
- [Bulk delete users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-delete)
- [Download list of users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-download)
