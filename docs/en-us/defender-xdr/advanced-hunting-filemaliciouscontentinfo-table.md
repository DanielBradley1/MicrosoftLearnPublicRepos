<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-filemaliciouscontentinfo-table -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# FileMaliciousContentInfo \(Preview\)

Important

Some information relates to prereleased product which might be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

The `FileMaliciousContentInfo` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about files that were processed by Microsoft Defender for Office 365 in SharePoint Online, OneDrive, and Microsoft Teams. Use this reference to construct queries that return information from this table.

Tip

For detailed information about the events types \(`ActionType` values\) supported by a table, use the built-in schema reference available in the Defender portal.

This advanced hunting table is populated by records from Defender for Office 365. If your organization didn't deploy the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Office 365 in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was generated |
| `Workload` | `string` | Information about the workload from which the URL originated from |
| `FileName` | `string` | Name of the file that the recorded action was applied to |
| `FolderPath` | `string` | Path of the folder containing the file that the recorded action was applied to |
| `FileSize` | `long` | Size of the file in bytes |
| `SHA256` | `string` | SHA-256 of the file that the recorded action was applied to |
| `FileOwnerDisplayName` | `string` | Account recorded as owner of the file |
| `FileOwnerUpn` | `string` | Account recorded as owner of the file |
| `DocumentId` | `string` | Unique identifier of the file |
| `ThreatTypes` | `dynamic` | Verdict from the email filtering stack on whether the email contains malware, phishing, or other threats |
| `ThreatNames` | `string` | Detection name for malware or other threats found |
| `DetectionMethods` | `string` | Methods used to detect malware, phishing, or other threats found in the email |
| `LastModifyingAccountUpn` | `string` | Account that last modified this file |
| `LastModifiedTime` | `datetime` | Date and time the item or related metadata was last modified |
| `FileCreationTime	` | `datetime` | Timestamp of the file creation |
| `ReportId` | `string` | Unique identifier for the event |

## Read more

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
