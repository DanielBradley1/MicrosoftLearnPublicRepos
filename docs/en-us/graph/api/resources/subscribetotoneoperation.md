<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subscribetotoneoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# SubscribeToToneOperation resource type

Namespace: microsoft.graph

Describes the response format of creation of subscription to receive DTMF tones.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | The client context. |
| id | String | The server operation ID. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "status": "notStarted | running | completed | failed"
}
```
