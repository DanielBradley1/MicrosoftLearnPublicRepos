<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-retentioneventstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# retentionEventStatus resource type

Namespace: microsoft.graph.security

For event-based retention, this attribute provides the status of event propagation to the targeted locations after the event has been created.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | The error if the status isn't successful. |
| status | microsoft.graph.security.eventStatusType | The status of the distribution. The possible values are: `pending`, `error`, `success`, `notAvaliable`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.retentionEventStatus",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "status": "String"
}
```
