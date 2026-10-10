<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-user-experience?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Advanced Data Residency: Migration user experience

This article describes what users experience during [*Microsoft 365 Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\) data migration.

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Overview

Data moves are a back-end service operation with minimal, if any, effect on end users. Microsoft notifies customers of any service maintenance through Message center in the Microsoft 365 admin center.

## General user experience

For most users, the migration process is transparent:

- Users continue to access their data normally during migration
- No action is required from end users
- Applications and services remain available

## Potential service effects

Given the complex nature of services included in Microsoft 365 licenses, migration could cause:

- Minor disruption to certain services
- Temporary unavailability of specific features
- Brief periods where data may be read-only

These effects are typically brief and occur during off-peak hours when possible.

## Microsoft 365 Service-specific migration information

For detailed information about what users may experience during migration for specific services, see the following resources:

| Service | Migration information |
| :--- | :--- |
| Exchange Online | [Exchange Online migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide#migration) |
| SharePoint and OneDrive | [SharePoint and OneDrive migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide#migration-with-advanced-data-residency) |
| Microsoft Teams | [Microsoft Teams migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide#migration) |
| Microsoft 365 Copilot | [Microsoft 365 Copilot migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide#migration-and-user-experience) |
| Microsoft Defender for Office P1 | [Microsoft Defender for Office P1 migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide#migration) |
| Office for the web | [Office for the web migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-m365-web-apps?view=o365-worldwide#migration) |
| Viva Connections | [Viva Connections migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-viva-connections?view=o365-worldwide#migration) |
| Microsoft Purview | [Microsoft Purview migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#migration) |

## Communication to end users

Consider the following communication best practices:

- **Before migration**: Inform users that a data migration will occur as part of your organization's [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) requirements
- **During migration**: Reassure users that brief service interruptions are expected and normal
- **After migration**: Confirm that migration is complete and services are operating normally

## Troubleshooting

If users report issues during migration:

1. Check Message center for any service maintenance notifications
2. Verify the issue is related to migration and not a separate service incident
3. For persistent issues, contact Microsoft Support

## Next steps

- [Monitor migration status and notifications](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-migration-status?view=o365-worldwide)
- [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide)
- [ADR data commitments](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide)
