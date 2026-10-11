<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Advanced Data Residency: Migration initiation

This article describes how to opt-in and initiate the data migration process for [*Microsoft 365 Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\).

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Overview

After receiving *ADR* licenses, a [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) Global Administrator must opt-in to initiate the data migration process.

Important

The data migration process doesn't begin until the *Tenant* Global Administrator completes the opt-in step.

## Prerequisites

Before initiating migration, ensure:

- Your *Tenant* meets [ADR eligibility requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements)
- *ADR* licenses have been purchased for 100% of paid licenses in the *Tenant*
- A *Tenant* Global Administrator is available to complete the opt-in process

For detailed prerequisites, see [Prerequisites and eligibility](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-prerequisites?view=o365-worldwide).

## Initiate migration

To initiate the *ADR* data migration:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) as a *Tenant* Global Administrator.
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.
3. Review the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to see current data locations.
4. Select the option to initiate migration for *ADR* services that don't currently reside in your [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).

![Screenshot of Data Location Card before migration opt-in.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-opt-in-0725.png?view=o365-worldwide)

## After opt-in

Once you initiate migration:

- You receive confirmation of your opt-in date and migration initiation
- The *Data Location Card* updates to show migration status
- Microsoft begins the process of moving [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to your *Local Region Geography*

![Screenshot of Data Location Card after migration opt-in.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-in-progress-cropped-0725.png?view=o365-worldwide)

## Migration timeline

Microsoft uses reasonable efforts to complete *ADR* *Customer Data* migration within **12 months** from the time the *Tenant* Global Administrator initiates migration.

Note

Large or complex *Tenants*, and situations outside of Microsoft's control, may require more time for migration to complete.

## What happens during migration

During the migration process:

- Microsoft moves *Customer Data* for each *ADR* service to your *Local Region Geography*
- No action is required from the customer while Microsoft moves data
- Microsoft notifies customers of any service maintenance through Message center

For information about what users may experience during migration, see [User experience during migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-user-experience?view=o365-worldwide).

## Next steps

- [Monitor migration status and notifications](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-migration-status?view=o365-worldwide)
- [User experience during migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-user-experience?view=o365-worldwide)
- [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide)
