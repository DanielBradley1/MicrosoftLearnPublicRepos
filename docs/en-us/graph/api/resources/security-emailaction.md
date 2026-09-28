<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-emailaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# emailAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) that targets an email message returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) hunting query. The action uses message and recipient columns from the query output to identify the email message.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta).

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
