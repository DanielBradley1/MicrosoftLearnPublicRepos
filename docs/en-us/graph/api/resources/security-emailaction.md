<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# emailAction resource type

Namespace: microsoft.graph.security

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0) that targets an email message returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) hunting query. The action uses message and recipient columns from the query output to identify the email message.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| networkMessageIdColumn | String | Name of the hunting-query result column that contains the network message ID of the targeted email message. |
| recipientColumn | String | Name of the hunting-query result column that contains the recipient of the targeted email message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.emailAction",
  "networkMessageIdColumn": "String",
  "recipientColumn": "String"
}
```
