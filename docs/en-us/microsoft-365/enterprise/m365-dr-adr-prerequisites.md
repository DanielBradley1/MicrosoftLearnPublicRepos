<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-prerequisites?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Advanced Data Residency: Prerequisites

This article describes the prerequisites and eligibility requirements for implementing [*Microsoft 365 Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\).

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Prerequisites checklist

Before implementing *ADR*, verify the following prerequisites are met:

| Requirement | Description |
| :--- | :--- |
| **Eligibility** | Confirm your [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) meets *ADR* eligibility requirements |
| **Licenses** | Purchase *ADR* licenses for 100% of paid licenses in the *Tenant* |
| **Admin access** | Ensure a *Tenant* Global Administrator is available to complete the opt-in process |

## Eligibility requirements

To be eligible for *ADR*, your *Tenant* must meet the requirements described in [ADR overview and requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements).

Key eligibility criteria include:

- *Tenant* **must** have a [*Default Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) that is a [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)
- *Tenant* must have qualifying Microsoft 365 subscriptions
- *ADR* licenses must be purchased for 100% of paid licenses

## Determine if Microsoft 365 migration is needed

To determine if your *Tenant* requires data migration after purchasing *ADR* licenses:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.
3. Review the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to see the current location of your [*Data at Rest*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).

If any services show data stored outside your *Local Region Geography*, migration is needed after purchasing *ADR* licenses.

[![Screenshot of Microsoft 365 Admin Center Data Location view.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-mac-view-1125.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-mac-view-1125.png?view=o365-worldwide#lightbox)

## Next steps

After verifying prerequisites:

1. Purchase *ADR* licenses for your *Tenant*
2. [Initiate migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide) to begin the data move process
3. Review [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide) to understand ongoing compliance requirements
