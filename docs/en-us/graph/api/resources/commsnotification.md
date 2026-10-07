<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/commsnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# commsNotification resource type

Namespace: microsoft.graph

Communications notification base type that is published by Communications servers to notify changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeType | [changeType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#changetype-values) | The possible values are: `created`, `updated`, `deleted`, `unknownFutureValue`. `unknownFutureValue` is an evolvable enumeration sentinel reserved for future extensibility. Its addition does not introduce a new notification change type or change existing notification delivery. |
| resourceUrl | String | URI of the resource that was changed. |

> **Note:** `resourceData` is available as additional data. It is either an entity or a collection of entities depending on the number of changes packaged in the notification.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.commsNotification",
  "changeType": "String",
  "resourceUrl": "String"
}
```
