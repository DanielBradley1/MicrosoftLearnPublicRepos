<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetracedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# exchangeMessageTraceDetail resource type

Namespace: microsoft.graph

Represents a detailed trace event for an email message as it passes through the Exchange Online organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | String | The action taken on the message during the event. |
| data | String | Additional data associated with the event, containing supplementary information specific to the event. |
| dateTime | DateTimeOffset | The date and time when the event occurred. The timestamp is in UTC format. |
| description | String | A detailed description that provides context about what happened during message processing. |
| event | String | The event that occurred during message processing. |
| id | String | The unique identifier for the message trace detail record. |
| messageId | String | The Message-ID header field of the message. The format depends on the messaging server that sent the message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeMessageTraceDetail",
  "action": "String",
  "data": "String",
  "dateTime": "String (timestamp)",
  "description": "String",
  "event": "String",
  "id": "String (identifier)",
  "messageId": "String"
}
```
