<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step3?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Step 3: Verifying trust \(SharePoint\)

This article is Step 3 in a solution designed to complete a **Cross-tenant SharePoint migration.** To learn more, see [Cross-tenant SharePoint migration overview](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration?view=o365-worldwide).

- Step 1: [Connect to the source and the target tenants](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step1?view=o365-worldwide)
- Step 2: [Establish trust between the source and the target tenant](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step2?view=o365-worldwide)
- **Step 3: [Verify trust is established](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step3?view=o365-worldwide)**
- Step 4: [Precreate users and groups](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step4?view=o365-worldwide)
- Step 5: [Prepare identity mapping](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step5?view=o365-worldwide)
- Step 6: [Start a Cross-tenant SharePoint migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step6?view=o365-worldwide)
- Step 7: [Post migration steps](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step7?view=o365-worldwide)

Before proceeding with your migration, you need to verify the trust is complete. A status of *GoodToProceed* confirms that the trust is verified.

## To verify trust is established

1. On the **source tenant** run:

```powershell

Test-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>
```

2. On the **target tenant** run:

```powershell

Test-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Source -PartnerCrossTenantHostUrl <SOURCECrossTenantHostUrl>
```

## Troubleshooting trust issues

When you verify the trust, the possible values are:

| Value | Description |
| :--- | :--- |
| NotEstablished | Trust wasn't requested locally. |
| NotEstablishedByPartner | Partner didn't request the Trust. |
| DormantByPartner | Partner's requested trust is within the seven days waiting period after creation. |
| CouldNotContactPartner | Couldn't contact the partner to determine status. |
| GoodToProceed | Verified to proceed. |

## Step 4: [Precreate users and groups](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-sharepoint-migration-step4?view=o365-worldwide)
