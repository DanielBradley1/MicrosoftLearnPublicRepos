<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-messagecontents-table -->
<!-- Sitemap-Last-Modified: 2026-09-26 -->

# MessageContents table in Microsoft Defender XDR

The `MessageContents` table is an advanced hunting table in Microsoft Defender XDR. The table gives authorized security operations center \(SOC\) analysts access to Microsoft Teams message snippets and associated message metadata. Analysts can use the table to add message context to Teams threat investigations and correlate message information with security signals in other advanced hunting tables. Access requires advanced hunting and the Preview role.

Note

Custom detection rules and streaming aren't available for the `MessageContents` table.

## Prerequisites

- Access to advanced hunting.
- The Preview role, which includes the required message preview `Read` permission.

## Review MessageContents table data

The table contains supported Teams messages available through the underlying Teams message metadata source, including messages with URLs and federated messages.

| Column name | Data type | Description |
| --- | --- | --- |
| **`Timestamp`** | `datetime` | Date and time when the message was delivered |
| **`TeamsMessageId`** | `string` | Unique identifier for the message |
| **`ThreadId`** | `string` | Unique identifier for the channel or chat thread |
| **`ThreadName`** | `string` | Name of the channel or chat thread |
| **`MessageSnippet`** | `string` | Snippet of the message |
| **`ThreadType`** | `string` | Type of thread |
| **`SenderEmailAddress`** | `string` | Email address of the message sender |
| **`SenderObjectId`** | `string` | Object ID of the message sender |

## Correlate message data

You can join `MessageContents` with other advanced hunting tables to correlate Teams message information with other security signals during an investigation.

## Control access to MessageContents

Access to `MessageContents` is permission-controlled because the table can contain Teams message content. Users without the required advanced hunting and message preview permissions can't access or query the table.

Review which security administrators and SOC analysts in your organization need access to Teams message content for threat investigations. Use your organization's role-based access controls to limit access to the appropriate users.

When **Email & collaboration** > **Defender for Office 365** permissions are active in Microsoft Defender XDR Unified role-based access control \(RBAC\), assign the Preview role through **Security operations/Raw data \(email & collaboration\)/Email & collaboration content \(read\)**. This assignment affects the Defender portal only, not PowerShell. For other role configurations, see [Actions on the Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page#actions-on-the-email-entity-page).

No action is required if you don't want analysts to use this capability.

## Related content

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Advanced hunting schema tables](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [MessageEvents table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-messageevents-table)
