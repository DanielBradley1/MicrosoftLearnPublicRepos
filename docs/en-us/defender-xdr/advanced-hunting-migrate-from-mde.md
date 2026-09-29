<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Migrate advanced hunting queries from Microsoft Defender for Endpoint

Move your advanced hunting workflows from Microsoft Defender for Endpoint to proactively hunt for threats using a broader set of data. In Microsoft Defender, you get access to data from other Microsoft 365 security solutions, including:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

Note

Most Microsoft Defender for Endpoint customers can [use Microsoft Defender XDR without additional licenses](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements). To start transitioning your advanced hunting workflows from Defender for Endpoint, [turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable).

You can transition without affecting your existing Defender for Endpoint workflows. Saved queries remain intact, and custom detection rules continue to run and generate alerts. Saved queries and custom detection rules will, however, be visible in Microsoft Defender.

## Schema tables in Microsoft Defender only

The [Microsoft Defender advanced hunting schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables) provides additional tables containing data from various Microsoft 365 security solutions. The following tables are available only in Microsoft Defender:

| Table name | Description |
| --- | --- |
| [AlertEvidence](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertevidence-table) | Files, IP addresses, URLs, users, or devices associated with alerts |
| [AlertInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertinfo-table) | Alerts from Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps, and Microsoft Defender for Identity, including severity information and threat categories |
| [EmailAttachmentInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailattachmentinfo-table) | Information about files attached to emails |
| [EmailEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailevents-table) | Microsoft 365 email events, including email delivery and blocking events |
| [EmailPostDeliveryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailpostdeliveryevents-table) | Security events that occur post-delivery, after Microsoft 365 has delivered the emails to the recipient mailbox |
| [EmailUrlInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailurlinfo-table) | Information about URLs on emails |
| [IdentityDirectoryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identitydirectoryevents-table) | Events involving an on-premises domain controller running Active Directory \(AD\). This table covers a range of identity-related events and system events on the domain controller. |
| [IdentityInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityinfo-table) | Account information from various sources, including Microsoft Entra ID |
| [IdentityLogonEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identitylogonevents-table) | Authentication events on Active Directory and Microsoft online services |
| [IdentityQueryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityqueryevents-table) | Queries for Active Directory objects, such as users, groups, devices, and domains |

Important

Queries and custom detections which use schema tables that are only available in Microsoft Defender can only be viewed in Microsoft Defender.

## Map DeviceAlertEvents table

The `AlertInfo` and `AlertEvidence` tables replace the `DeviceAlertEvents` table in the Microsoft Defender for Endpoint schema. In addition to data about device alerts, these two tables include data about alerts for identities, apps, and emails.

Use the following table to check how `DeviceAlertEvents` columns map to columns in the `AlertInfo` and `AlertEvidence` tables.

Tip

In addition to the columns in the following table, the `AlertEvidence` table includes many other columns that provide a more holistic picture of alerts from various sources. [See all AlertEvidence columns](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertevidence-table)

| DeviceAlertEvents column | Where to find the same data in Microsoft Defender XDR |
| --- | --- |
| `AlertId` | `AlertInfo` and `AlertEvidence` tables |
| `Timestamp` | `AlertInfo` and `AlertEvidence` tables |
| `DeviceId` | `AlertEvidence` table |
| `DeviceName` | `AlertEvidence` table |
| `Severity` | `AlertInfo` table |
| `Category` | `AlertInfo` table |
| `Title` | `AlertInfo` table |
| `FileName` | `AlertEvidence` table |
| `SHA1` | `AlertEvidence` table |
| `RemoteUrl` | `AlertEvidence` table |
| `RemoteIP` | `AlertEvidence` table |
| `AttackTechniques` | `AlertInfo` table |
| `ReportId` | This column is typically used in Microsoft Defender for Endpoint to locate related records in other tables. In Microsoft Defender XDR, you can get related data directly from the `AlertEvidence` table. |
| `Table` | This column is typically used in Microsoft Defender for Endpoint for additional event information in other tables. In Microsoft Defender XDR, you can get related data directly from the `AlertEvidence` table. |

## Adjust existing Microsoft Defender for Endpoint queries

Microsoft Defender for Endpoint queries will work as-is unless they reference the `DeviceAlertEvents` table. To use these queries in Microsoft Defender, apply these changes:

- Replace `DeviceAlertEvents` with `AlertInfo`.
- Join the `AlertInfo` and the `AlertEvidence` tables on `AlertId` to get equivalent data.

### Original Defender for Endpoint query

The following query finds recent `DeviceAlertEvents` records in Microsoft Defender for Endpoint that are associated with PowerShell technique T1086 and involve *powershell.exe*:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### Modified query for Microsoft Defender XDR

The following query migrates the original Defender for Endpoint query for use in Microsoft Defender XDR. Instead of querying `DeviceAlertEvents` directly, it uses `AlertInfo` to filter by attack technique and joins `AlertEvidence` to check for the file name.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## Migrate custom detection rules

When Microsoft Defender for Endpoint rules are edited on Microsoft Defender, they continue to function as before if the resulting query looks at device tables only.

For example, alerts generated by custom detection rules that query only device tables will continue to be delivered to your SIEM and generate email notifications, depending on how you've configured SIEM delivery and email notifications in Microsoft Defender for Endpoint. Any existing suppression rules in Defender for Endpoint will also continue to apply.

Once you edit a Defender for Endpoint rule so that it queries identity and email tables, which are only available in Microsoft Defender, the rule is automatically moved to Microsoft Defender.

Alerts generated by the migrated rule:

- Are no longer visible in the Defender for Endpoint portal \(Microsoft Defender Security Center\)
- Stop being delivered to your SIEM or generate email notifications. To work around the loss of SIEM delivery and email notifications, configure notifications through Microsoft Defender to get the alerts. You can use the [Microsoft Defender API](https://learn.microsoft.com/en-us/defender-xdr/api-incident) to receive notifications for customer detection alerts or related incidents.
- Won't be suppressed by Microsoft Defender for Endpoint suppression rules. To prevent alerts from being generated for certain users, devices, or mailboxes, modify the corresponding queries to exclude those entities explicitly.

If you edit a Defender for Endpoint rule to query identity or email tables, you will be prompted for confirmation before the rule is moved to Microsoft Defender XDR.

New alerts generated by custom detection rules in Microsoft Defender are displayed in an alert page that provides the following information:

- Alert title and description
- Impacted assets
- Actions taken in response to the alert
- Query results that triggered the alert
- Information on the custom detection rule

[![An example of an alert page that displays new alerts generated by custom detection rules in Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-migrate-from-mde/new-alert-page.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-migrate-from-mde/new-alert-page.png#lightbox)

## Write queries without DeviceAlertEvents

In the Microsoft Defender XDR schema, the `AlertInfo` and `AlertEvidence` tables are provided to accommodate the diverse set of information that accompany alerts from various sources.

To get the same alert information that you used to get from the `DeviceAlertEvents` table in the Microsoft Defender for Endpoint schema, filter the `AlertInfo` table by the `ServiceSource` column. The `ServiceSource` column identifies which Microsoft 365 security product generated the alert, such as `Microsoft Defender for Endpoint`, `Microsoft Defender for Office 365`, or `Microsoft Defender for Identity`. After filtering by `ServiceSource`, join each unique ID with the `AlertEvidence` table, which provides detailed event and entity information.

The following query narrows `AlertInfo` to alerts generated by Microsoft Defender for Endpoint and joins `AlertEvidence` on `AlertId` to retrieve the associated evidence:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

The previous query yields many more columns than `DeviceAlertEvents` in the Microsoft Defender for Endpoint schema. To keep results manageable, use `project` to get only the columns you are interested in. The following query builds on the previous example by adding a PowerShell filter and using `project` to return only the columns that are useful when investigating PowerShell activity:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

You can also filter for specific entities involved in the alerts. Building on the previous examples, the following query looks up a specific alert by title, joins `AlertInfo` with `AlertEvidence` to retrieve the related evidence records, and then narrows the results to a specific IP address by filtering on `EntityType` and `RemoteIP`:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## Related articles

For more information about advanced hunting and Microsoft Defender XDR, see the following articles:

- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Advanced hunting in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
