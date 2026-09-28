<!-- Source: https://learn.microsoft.com/en-us/graph/backup-restore-granular-search -->
<!-- Sitemap-Last-Modified: 2026-02-10 -->

# Granular search queries for backup and restore APIs

Use granular search queries to filter and search for specific mailbox artifacts when using the Microsoft Graph backup and restore APIs. Granular search enables you to construct precise query expressions to find emails, calendar events, contacts, tasks, and notes based on various criteria such as sender, subject, participants, and attachments.

## Overview

The [artifactQuery](https://learn.microsoft.com/en-us/api-reference/beta/resources/artifactquery.md) resource contains a `queryExpression` property that allows you to specify search criteria for mailbox artifacts. You can combine multiple properties using logical operators to create complex search expressions that filter restore points based on your specific requirements.

## Supported properties

The following table describes the properties you can use in query expressions.

| Property | Description | Value type | Supported operators | Wildcard support |
| --- | --- | --- | --- | --- |
| Subject | The subject of the message or primary searchable string for other item types | String | -like, -and \(up to 3\) | \* \(after string\) |
| Sender | Messages from the specified sender | Display name, Alias, SMTP address, or LegacyDN | -like | \* \(after string\) |
| Participants | Messages with specified recipient in To, Bcc, or Cc fields | Display name, Alias, SMTP address, or LegacyDN | -like, -and \(up to 3\) | \* \(after string\) |
| HasAttachment | Whether the message has an attachment | Boolean \(true or false\) | -eq | No |
| MessageKind | The mailbox item type for which to search | Enum: Email, Note, Task, Contact, Calendar | -eq | No |

#### Examples

Search for emails from a specific sender with attachments

```
(Sender -like 'abc@contoso.com') -and (HasAttachment -eq 'true')
```

Search for emails with specific subject keywords and multiple participants

```
(Subject -like 'Project Alpha*') -and (Participants -like 'john@contoso.com' -and Participants -like 'sarah@contoso.com')
```

Search for calendar events organized by a specific user

```
(MessageKind -eq 'Calendar') -and (Sender -like 'admin@contoso.com')
```

Search for contacts by name pattern

```
(MessageKind -eq 'Contact') -and (Subject -like 'Smith*')
```

Search for emails combining multiple criteria including message type, subject, sender, and attachments

```
(MessageKind -eq 'Email') -and (Subject -like 'Invoice*') -and (Sender -like 'vendor*') -and (HasAttachment -eq 'true')
```
