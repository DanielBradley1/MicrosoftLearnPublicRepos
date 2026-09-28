<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step7?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Step 7: Post migration steps \(SharePoint\)

This article is Step 7 in a solution designed to complete a Cross-tenant SharePoint migration. To learn more, see [Cross-tenant SharePoint migration overview](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration?view=o365-worldwide).

- Step 1: [Connect to the source and the target tenants](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step1?view=o365-worldwide)
- Step 2: [Establish trust between the source and the target tenant](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step2?view=o365-worldwide)
- Step 3: [Verify trust is established](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step3?view=o365-worldwide)
- Step 4: [Precreate users and groups](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step4?view=o365-worldwide)
- Step 5: [Prepare identity mapping](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step5?view=o365-worldwide)
- Step 6: [Start a Cross-tenant SharePoint migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step6?view=o365-worldwide)
- **Step 7: [Post migration steps](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step7?view=o365-worldwide)**

## Removing trust relationship

Important

Make sure you remove the Trust Relationship on both source and target tenants before your source tenant licenses expire. Once the licenses expire, the trust removal command doesn't work on the source.

1. On the source tenant, run this command to remove the trust relationship between Source and Target tenant.

   ```powershell
   Remove-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>
   ```

2. On the target tenant, run this command to remove the trust relationship between the target and source tenant.

   ```powershell
   Remove-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>
   ```

### Parameter definitions

| Parameter | Definition |
| --- | --- |
| PartnerRole | Roles of the partner tenant you're establishing trust with. Use *source* if partner tenant is the source of the SharePoint migrations, and *target* if the partner tenant is the destination. |
| PartnerCrossTenantHostURL | The cross-tenant host URL of the partner tenant. The partner tenant can determine this URL by running: *Get-SPOCrossTenantHostURL* on each of the tenants. |

## Removing redirect links post migration

After the migration from Source to Target is complete, a redirect link is placed on the source. If users attempt to log back into their Source account or site, the link automatically redirects them to their new Target site. Remove the redirect links on the source after your full migration is completed.

![flow chart of how redirects are created.](https://learn.microsoft.com/en-us/microsoft-365/media/cross-tenant-migration/t2t-onedrive-redirect-workflow.png?view=o365-worldwide)

Occasionally, a user may need to be migrated back to the original source. Remove the redirect link on the Target if you migrate a user back to the source.

- To remove redirect links, use the **Remove-SPOSite** PowerShell command.
- To get a list of all redirect sites on a tenant, use the **Get-Sposite -Template RedirectSite#0** command.

Keep track of any user or site you migrate back to the source from the target. After successfully migrating these users or sites back to the source, confirm that the user/sites are accessible. Then you can remove the redirect link from Target using the **Remove-SPOSite command**.

Important

Site URL's must be unique. When migrating a user or site back to the source, the redirect site created on the initial move uses the original URL. This results in a conflict and causes the migration to fail if not removed. redirect link still being present on the tenant you are attempting to migrate to.

## Other post migration steps

Existing links and permissions should continue to work as expected once the migration is complete, based on the identity mapping files that were created.

### SharePoint sites

The source SharePoint site is set to read-only while a migration is in progress. Once the migration's complete, users are directed to the site in the new target tenant whenever they navigate to the source site. Users must sign in using their target tenant credentials.

### Permissions on SharePoint content

Users with permissions to SharePoint content continue to have access to the content during the migration and after it's complete, if those users or groups were included as part of the identity mapping step.

### Sharing Links

The existing shared links for the migrated files automatically redirect to the new target location.

Note

Customers need to manually add the labels that were removed before migration.
