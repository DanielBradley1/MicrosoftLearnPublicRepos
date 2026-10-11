<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-migration-status?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Advanced Data Residency: Migration status and notifications

This article describes how to monitor migration progress and receive notifications for [*Microsoft 365 Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\).

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Overview

*Tenant Global Administrators* can monitor migration progress and receive notifications through multiple channels in the Microsoft 365 admin center.

## Monitor migration progress for Microsoft 365 services

### Data Location Card

The primary method for monitoring migration status:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.
3. Review the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to see current data locations for each service.

The *Data Location Card* shows:

- Current location of data for each service
- Migration status \(in progress, completed\)
- [*Committed Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) based on your *ADR* subscription

![Screenshot of Data Location Card showing migration in progress.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-in-progress-0725.png?view=o365-worldwide)

### Message center

For migration-related notifications:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Navigate to **Health** > **Message center**.
3. Review notifications for migration updates and service maintenance announcements.

## During migration

While Microsoft moves each *ADR* service and associated [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to the eligible [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions):

- No action is needed from the customer
- Microsoft notifies customers of any service maintenance through Message center
- Migration is performed as a back-end service operation

Note

Microsoft doesn't provide granular status to indicate progress toward migration completion for individual customer scenarios.

## Migration complete

When migration completes, the *Data Location Card* updates to show all services stored in your *Local Region Geography*.

![Screenshot of Data Location Card showing migration completed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-complete-0725.png?view=o365-worldwide)

After migration completes:

- All applicable *Customer Data* is stored in your *Local Region Geography*
- Your [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) has a [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) as long as *ADR* license coverage is maintained
- The *Data Location Card* displays your *Committed Geography*

## Troubleshooting

### Migration taking longer than expected

Large or complex *Tenants*, and situations outside of Microsoft's control, may require more time for migration to complete. Microsoft uses reasonable efforts to complete migration within 12 months.

If migration is taking longer than expected:

1. Check Message center for any relevant notifications
2. Verify *ADR* license coverage is maintained
3. Contact Microsoft Support if you have concerns

### Data Location Card not updating

License information and data location status may be delayed by 24-48 hours when changes are made. If the *Data Location Card* isn't reflecting expected changes after 48 hours, contact Microsoft Support.

## Next steps

- [User experience during migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-user-experience?view=o365-worldwide)
- [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide)
- [Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide)
