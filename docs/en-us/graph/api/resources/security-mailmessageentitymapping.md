<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mailmessageentitymapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# mailMessageEntityMapping resource type

Namespace: microsoft.graph.security

Represents a mapping from columns in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) query result to a mail message entity that is attached to the resulting alert.

Base type: [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| networkMessageIdColumn | String | Name of the detection query column that maps to the network message ID of the alert entity. |
| recipientColumn | String | Name of the detection query column that maps to the recipient of the alert entity. |
| senderColumn | String | Name of the detection query column that maps to the sender of the alert entity. |
| subjectColumn | String | Name of the detection query column that maps to the subject of the alert entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mailMessageEntityMapping",
  "networkMessageIdColumn": "String",
  "recipientColumn": "String",
  "senderColumn": "String",
  "subjectColumn": "String"
}
```
