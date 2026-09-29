<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityevents-table -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# IdentityEvents \(Preview\)

The `IdentityEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about identity events obtained from other cloud identity service providers. Use this reference to construct queries that return information from this table.

Important

Some information relates to prereleased product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

This advanced hunting table is populated by records from Microsoft Defender for Identity. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Identity in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

Note

This advanced hunting table is populated only when other identity services like Okta are connected to Defender for Identity.

For information on other tables in the advanced hunting schema, see the [advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp ` | `datetime` | Date and time when the record was generated |
| `ReportId ` | `string` | Unique identifier for the event |
| `AccountId ` | `string` | Unique identifier for the account in the source application |
| `AccountType` | `string` | Type of user account, indicating its general role like User, SystemPrincipal |
| `AccountDisplayName` | `string` | Name displayed in the address book entry for the account user. This is usually a combination of the given name, middle initial, and surname of the user. |
| `AccountUpn` | `string` | Alternate ID, email, or name for the account in the source application |
| `ActionType` | `string` | Type of activity that triggered the event in the raw format received from the source application |
| `ActionResult` | `string` | Result of the action |
| `ActionFailureReason` | `string` | Information explaining why the recorded action failed |
| `IPAddress` | `string` | IP address assigned to the device and used during related network communications |
| `UserAgent` | `string` | User agent information from the web browser or other client application |
| `TargetObjects` | `dynamic` | List of the target objects of this activity. Target object can be user, group, role, domain, application, and more. |
| `Application` | `string` | The source application where this event was received from |
| `ApplicationInstanceId` | `string` | Domain of the source application |
| `ApplicationEventId` | `string` | Raw event ID provided by the source application |
| `ApplicationSessionId` | `string` | Raw session ID provided by the source application |
| `RawEventData` | `dynamic` | Full raw event information from the source application in JSON format |
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
