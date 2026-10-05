<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/commsnotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# commsNotification resource type

Namespace: microsoft.graph

Communications notification base type that is published by Communications servers to notify changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeType | String | The possible values are: `created`, `updated`, `deleted`. |
| resourceUrl | String | URI of the resource that was changed. |

> **Note:** `resourceData` is available as additional data. It is either an entity or a collection of entities depending on the number of changes packaged in the notification.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.commsNotification",
  "changeType": "created | updated | deleted",
  "resourceUrl": "String"
}
```
