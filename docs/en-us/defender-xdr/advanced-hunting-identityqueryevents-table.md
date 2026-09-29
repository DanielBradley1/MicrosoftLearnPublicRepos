<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityqueryevents-table -->
<!-- Sitemap-Last-Modified: 2025-06-20 -->

# IdentityQueryEvents

The `IdentityQueryEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about queries performed against Active Directory objects, such as users, groups, devices, and domains. Use this reference to construct queries that return information from this table.

Tip

For detailed information about the events types \(`ActionType` values\) supported by a table, use the built-in schema reference available in Microsoft Defender XDR.

This advanced hunting table is populated by records from Microsoft Defender for Identity or Microsoft Sentinel and Mirosoft Entra ID. If your organization hasn’t deployed the service in Microsoft Defender XDR, queries that use the table aren’t going to work or return any results. For more information about how to deploy Defender for Identity in Defender XDR, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services). For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `ActionType` | `string` | Type of activity that triggered the event. See the [in-portal schema reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables?#get-schema-information-in-the-security-center) for details |
| `Application` | `string` | Application that performed the recorded action |
| `QueryType` | `string` | Type of query, such as QueryGroup, QueryUser, or EnumerateUsers |
| `QueryTarget` | `string` | Name of user, group, device, domain, or any other entity type being queried |
| `Query` | `string` | String used to run the query |
| `Protocol` | `string` | Protocol used during the communication |
| `AccountName` | `string` | User name of the account |
| `AccountDomain` | `string` | Domain of the account |
| `AccountUpn` | `string` | User principal name \(UPN\) of the account |
| `AccountSid` | `string` | Security Identifier \(SID\) of the account |
| `AccountObjectId` | `string` | Unique identifier for the account in Microsoft Entra ID |
| `AccountDisplayName` | `string` | Name of the account user displayed in the address book. Typically a combination of a given or first name, a middle initial, and a last name or surname. |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `IPAddress` | `string` | IP address assigned to the endpoint and used during related network communications |
| `Port` | `int` | TCP port used during communication |
| `DestinationDeviceName` | `string` | Name of the device running the server application that processed the recorded action |
| `DestinationIPAddress` | `string` | IP address of the device running the server application that processed the recorded action |
| `DestinationPort` | `int` | Destination port of related network communications |
| `TargetDeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device that the recorded action was applied to |
| `TargetAccountUpn` | `string` | User principal name \(UPN\) of the account that the recorded action was applied to |
| `TargetAccountDisplayName` | `string` | Display name of the account that the recorded action was applied to |
| `Location` | `string` | City, country/region, or other geographic location associated with the event |
| `ReportId` | `string` | Unique identifier for the event |
| `AdditionalFields` | `dynamic` | Additional information about the entity or event |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
