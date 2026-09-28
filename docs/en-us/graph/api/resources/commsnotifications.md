<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/commsnotifications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# commsNotifications resource type

Namespace: microsoft.graph

List of notifications used by the Communications servers for sending multiple notifications in a single batch.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | [commsNotification](https://learn.microsoft.com/en-us/graph/api/resources/commsnotification?view=graph-rest-1.0) collection | The notification of a change in the resource. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "value": [ { "@odata.type": "#microsoft.graph.commsNotification" } ]
}
```
