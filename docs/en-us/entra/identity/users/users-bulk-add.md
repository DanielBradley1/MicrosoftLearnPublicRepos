<!-- Source: https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-add -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# Bulk create users in Microsoft Entra ID

## Overview

Microsoft Entra ID, part of Microsoft Entra, supports bulk user create and delete operations and supports downloading lists of users. Just fill out the comma-separated values \(CSV\) template you can download from Microsoft Entra ID.

## Required permissions

In order to bulk create users in the administration portal, you must be signed in as at least a User Administrator.

## Understand the CSV template

Download and fill in the bulk upload CSV template to help you successfully create Microsoft Entra users in bulk. The CSV template you download might look like this example:

![Screenshot of spreadsheet for upload and call-outs explaining the purpose and values for each row and column.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-add/create-template-example.png)

Warning

If you're adding only one entry using the CSV template, you must preserve row 3 and add your new entry to row 4.

Ensure that you add the `.csv` file extension and remove any leading spaces before `userPrincipalName`, `passwordProfile`, and `accountEnabled`.

### CSV template structure

The rows in a downloaded CSV template are as follows:

- **Version number**: The first row containing the version number \(for example, `version:v1.0`\) must be included in the upload CSV. If your downloaded template includes this row, don't remove or modify it.
- **Column headings**: The format of the column headings is <*Item name*> \[PropertyName\] <*Required or blank*>. For example, `Name [displayName] Required`. Some older versions of the template might have slight variations.
- **Examples row**: The template might include a row of example values for each column. You must remove the examples row and replace it with your own entries.

Note

CSV template formats vary by operation. Some templates, such as bulk create or delete users, include `version:v1.0` as the first row. Other templates, such as group member operations, start with column headers. Download the template for your specific operation from the portal. Don't add a version row or any other row that isn't in the downloaded template. Keep any version row and column header row unchanged.

### Additional guidance

- Keep any version row and column header row in the upload template exactly as downloaded, or the upload can't be processed.
- The required columns are listed first.
- We don't recommend adding new columns to the template. Any additional columns you add are ignored and not processed.
- We recommend that you download the latest version of the CSV template as often as possible.

- Make sure to check there is no unintended whitespace before/after any field. For **User principal name**, having such whitespace would cause import failure.
- Ensure that values in **Initial password** comply with the currently active [password policy](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-policy#username-policies).
- Enter one user per row.

### Example CSV file

Here's an example of a completed CSV file ready for upload:

```csv
version:v1.0
Name [displayName] Required,User name [userPrincipalName] Required,Initial password [passwordProfile] Required,Block sign in (Yes/No) [accountEnabled] Required,First name [givenName],Last name [surname],Job title [jobTitle],Department [department],Usage location [usageLocation],Street address [streetAddress],State or province [state],Country or region [country],Office [physicalDeliveryOfficeName],City [city],ZIP or postal code [postalCode],Office phone [telephoneNumber],Mobile phone [mobile]
Alain Charon,alain@contoso.com,Password1!,No,Alain,Charon,Software Engineer,Engineering,US,,,,,,,
Isabella Simonsen,isabella@contoso.com,Password1!,No,Isabella,Simonsen,Product Manager,Product,US,,,,,,,
Joseph Price,joseph@contoso.com,Password1!,No,Joseph,Price,Sales Representative,Sales,US,,,,,,,
```

Important

Only the first four columns are required: **Name**, **User name**, **Initial password**, and **Block sign in**. All other columns are optional and can be left empty.

## To create users in bulk

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users** > **Bulk create**.
3. On the **Bulk create user** page, select **Download** to receive a valid comma-separated values \(CSV\) file of user properties, and then add users you want to create.

   ![Screenshot showing how to select a local CSV file in which you list the users you want to add.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-add/upload-button.png)
4. Open the CSV file and add a line for each user you want to create. The only required values are **Name**, **User principal name**, **Initial password**, and **Block sign in \(Yes/No\)**. Then save the file.

   ![Screenshot showing an example of the CSV file containing the names and IDs of the users to create.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-add/add-csv-file.png)
5. On the **Bulk create user** page, under Upload your CSV file, browse to the file. When you select the file and select **Submit**, validation of the CSV file starts.
6. After the file contents are validated, you’ll see **File uploaded successfully**. If there are errors, you must fix them before you can submit the job.
7. When your file passes validation, select **Submit** to start the bulk operation that imports the new users.
8. When the import operation completes, you see a notification of the bulk operation job status.

Note

The bulk create operation creates internal member accounts with the passwords specified in the CSV file. No invitation emails are sent to the new users. You must communicate the sign-in credentials to the users through your own process. To bulk invite external guest users and send invitation emails, see [Bulk invite B2B users](https://learn.microsoft.com/en-us/entra/external-id/tutorial-bulk-invite).

If you experience errors, you can download and view the results file on the **Bulk operation results** page. The file contains the reason for each error. The file submission must match the provided template and include the exact column names.

For more information about bulk operations limitations, see [Bulk import service limits](#bulk-import-service-limits).

## Check status

You can see the status of all of your pending bulk requests in the **Bulk operation results** page.

![Screenshot showing how to check the status of the operation in the bulk operations results page.](https://learn.microsoft.com/en-us/entra/identity/users/media/users-bulk-add/bulk-center.png)

Next, you can check to see that the users you created exist in the Microsoft Entra organization either in the Microsoft Entra admin center or by using PowerShell.

## Verify users

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Select Microsoft Entra ID.
3. Select **Users** > **All users**.
4. Under **Show**, select **All users** and verify that the users you created are listed.

### Verify users with PowerShell

Run the following command:

```PowerShell
Get-MgUser -Filter "UserType eq 'Member'"
```

You should see that the users that you created are listed.

## Bulk import service limits

Note

When performing bulk operations, such as import or create, you can encounter a problem if the bulk operation doesn't complete within the hour. To work around this issue, we recommend splitting the number of records processed per batch. For example, before starting an export you could limit the result set by filtering on a group type or user name to reduce the size of the results. By refining your filters, essentially you limit the data returned by the bulk operation. For more information, see [Bulk operations service limitations](https://learn.microsoft.com/en-us/entra/fundamentals/bulk-operations-service-limitations).

## Next steps

- [Bulk delete users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-delete)
- [Download list of users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-download)
- [Bulk restore users](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-restore)
