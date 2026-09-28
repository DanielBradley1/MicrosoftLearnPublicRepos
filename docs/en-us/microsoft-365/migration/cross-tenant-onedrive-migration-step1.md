<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step1?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Step 1: Connect to the source and target tenants

This article details Step 1 in a solution designed to complete a Cross-tenant OneDrive migration. To learn more, see [Cross-tenant OneDrive migration overview](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration?view=o365-worldwide).

- **Step 1: [Connect to the source and the target tenants](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step1?view=o365-worldwide)**
- Step 2: [Establish trust between the source and the target tenant](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step2?view=o365-worldwide)
- Step 3: [Verify trust is established](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step3?view=o365-worldwide)
- Step 4: [Precreate users and groups](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step4?view=o365-worldwide)
- Step 5: [Prepare identity mapping](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step5?view=o365-worldwide)
- Step 6: [Start a Cross-tenant OneDrive migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step6?view=o365-worldwide)
- Step 7: [Post migration steps](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step7?view=o365-worldwide)

## Before you begin

- **Microsoft SharePoint Online Powershell**. Confirm you have the most recent version installed. If not, [Download SharePoint Online Management Shell from Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35588).
- Be a SharePoint in Microsoft 365 admin or Microsoft 365 Global admin on both the source and target tenants.

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

### Connect to both tenants

1. Sign in to the SharePoint Management Shell as a SharePoint in Microsoft 365 admin or Microsoft 365 Global admin.
2. Run the following entering the **source** tenant URL:

   ```powershell
   Connect-SPOService -url https://<TenantName>-admin.sharepoint.com
   ```

3. When prompted, sign in to the **source** tenant using your Admin username and password.
4. Run the following entering the **target** tenant URL:

   ```powershell
   Connect-SPOService -url https://<TenantName>-admin.sharepoint.com
   ```

5. When prompted, sign in to the **target** tenant using your Admin username and password.

Important

**Microsoft 365 Multi-Geo customers:** You must treat each geography as a separate tenant. Provide the correct geography-specific URLs throughout the migration process.

## Step 2: [Establish trust between the source and target tenants](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration-step2?view=o365-worldwide)
