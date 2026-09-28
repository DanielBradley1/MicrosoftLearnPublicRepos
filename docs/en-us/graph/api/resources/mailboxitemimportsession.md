<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxitemimportsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# mailboxItemImportSession resource type

Namespace: microsoft.graph

Provides information about how to import items into a user's mailbox.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time in UTC when the import session expires. The date and time information uses ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. |
| importUrl | String | The URL endpoint that accepts POST requests for uploading a mailbox item exported using [exportItems](https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxItemImportSession",
  "expirationDateTime": "String (timestamp)",  
  "importUrl": "String"
}
```
