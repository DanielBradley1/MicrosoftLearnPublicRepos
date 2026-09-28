<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mailboxDetails resource type

Namespace: microsoft.graph

Represents details about a mailbox, including its unique directory identifier and associated email address.

Mailboxes are associated with reservable or drop-in Places objects such as [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailAddress | String | The primary SMTP address associated with the mailbox. |
| externalDirectoryObjectId | String | The unique identifier of the mailbox in the external directory \(such as Microsoft Entra\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailboxDetails",
  "emailAddress": "String",
  "externalDirectoryObjectId": "String"
}
```
