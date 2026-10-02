<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/migrate-files-migration-manager?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-06-03 -->

# Migrate Google files to Microsoft 365 for business with Migration Manager

Note

When you move from Google Workspace to Microsoft 365 for business, use Migration Manager to copy files from personal and shared Google drives. This article provides an overview. For complete instructions, see [Migrate Google Workspace to Microsoft 365 with Migration Manager](https://learn.microsoft.com/en-us/sharepointmigration/mm-google-overview).

## Watch: Migrate Google files to Microsoft 365 for business

Watch this video and find more on the [Microsoft 365 small business YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198217).

<iframe src="https://learn-video.azurefd.net/vod/player?id=521941e5-33c4-402c-85c2-1abee2d3854b" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

The video uses a SharePoint admin center entry point. Follow the Microsoft 365 admin center steps in this article for this procedure.

Note

Migration Manager copies files to Microsoft 365 for business. The original files remain in Google Drive. Google-native files are exported to Microsoft Office or other supported formats. Review [unsupported files](https://learn.microsoft.com/en-us/sharepointmigration/mm-unsupported-files) and migration reports to identify content that wasn't copied.

## Before you start

For standard Migration Manager projects that use OneDrive destinations, make sure each user's OneDrive exists before assigning destinations. If it doesn't, [pre-provision OneDrive for users in your organization](https://learn.microsoft.com/en-us/sharepoint/pre-provision-accounts). Migration Manager Lite can provision OneDrive automatically for eligible projects. If automatic provisioning isn't available or doesn't succeed, use the linked procedure before migration.

Before starting a migration:

- Review [permission settings](https://learn.microsoft.com/en-us/sharepointmigration/mm-project-settings-permissions) and identity mappings. File-level permissions aren't migrated by default; files inherit destination-folder permissions. Choose the required settings and validate destination access with representative users.
- Review [version settings](https://learn.microsoft.com/en-us/sharepointmigration/file-versions). By default, only the most recent file version is copied. Select the supported version-history option you need before migrating, and verify the resulting history.
- Check Google Drive for unorganized or orphaned files and decide how to preserve any that you need. These files aren't scanned, migrated, or listed in migration reports. See [unsupported files](https://learn.microsoft.com/en-us/sharepointmigration/mm-unsupported-files).

Note

Google migration is supported in GCC, but not in GCC High or DoD. See [Specialty environments support](https://learn.microsoft.com/en-us/sharepointmigration/mm-specialty-environments-support).

## Install the Microsoft 365 Migration app

Use the following steps to install the Microsoft 365 Migration app in your Google Workspace environment.

1. In the Microsoft 365 admin center, go to **Setup** > **Migration resources**.
2. Under **Self-service migration and import tools**, select **Explore migration & imports tools**.
3. Select **Google Workspace** to open the Google Workspace migration page.
4. Select **Connect to Google Workspace**.
5. On the **Install the migration app** page, select **Install and authorize**.
6. On the **Google Workspace Marketplace** page, sign in with a Google Workspace super administrator account.
7. Select the organization-wide installation option shown by Google Workspace Marketplace, such as **Admin install** or **Domain install**.
8. Select **Continue**.
9. Select the checkbox, then select **Finish**.
10. When the installation completes, select **Done**.
11. Return to the **Install the migration app** page, and select **Next**.
12. Select **Sign in to Google Workspace**, and then enter your Google Workspace admin credentials.
13. Select **Finish**.

## Select and scan drives

In standard Migration Manager, select and scan the drives you want to migrate before copying them to the migrations list. Migration Manager Lite guides eligible tenants through task selection, destination assignment, identity mapping, settings, and migration without the separate scan and copy steps.

1. On the **Drives** tab, select the Google drives you want to copy to Microsoft 365.
2. Select **Scan**. When the scan completes, the drives show a scan status of **Ready to migrate**.
3. Select **Copy to Drive migrations**.

## Start the migration

After selecting and scanning the drives you want to migrate, use the following steps to migrate them.

1. On the **Drive migrations** tab, verify the destination paths of the drives you want to migrate. Edit them if needed.
2. Select the drives you want to migrate, and then select **Migrate**.
3. When migration completes successfully, each drive shows a **Migration status** of **Completed**.

   A task can show **Completed** when unsupported items weren't migrated. Download and review both the migration summary and detailed reports, and resolve or account for failures and exclusions.

After resolving migration errors and preserving excluded content, continue with [canceling Google Workspace](https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/cancel-google?view=o365-worldwide).
