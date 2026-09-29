<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertinfo-table -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# AlertInfo

## Get access

To use advanced hunting or other [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender) capabilities, you need an appropriate role in Microsoft Entra ID. [Read about required roles and permissions for advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/custom-roles).

The `AlertInfo` table contains records from Microsoft Defender services. When Microsoft Sentinel is onboarded to the Defender portal, the table also contains Microsoft Sentinel alerts associated with incidents. Data availability depends on the services deployed and the Sentinel workspaces you can access. For more information, see [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services) and [Transition your Microsoft Sentinel environment to the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/move-to-defender).

Also, your access to endpoint data is determined by role-based access control \(RBAC\) settings in Microsoft Defender for Endpoint. [Read about managing access to Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions).

## AlertInfo

The `AlertInfo` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains alert information from Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, Microsoft Defender for Identity, and onboarded Microsoft Sentinel workspaces. Use this reference to construct queries that return information from this table. Join `AlertInfo` with [`AlertEvidence`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertevidence-table) on the `AlertId` column to retrieve the entities and evidence associated with each alert.

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `AlertId` | `string` | Unique identifier for the alert |
| `Title` | `string` | Title of the alert |
| `Category` | `string` | Type of threat indicator or breach activity identified by the alert |
| `Severity` | `string` | Indicates the potential impact \(high, medium, or low\) of the threat indicator or breach activity identified by the alert |
| `ServiceSource` | `string` | Product or service that provided the alert information |
| `DetectionSource` | `string` | Detection technology or sensor that identified the notable component or activity |
| `AttackTechniques` | `string` | MITRE ATT&CK techniques associated with the activity that triggered the alert |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
