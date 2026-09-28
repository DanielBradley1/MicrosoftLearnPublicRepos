<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# resourceConnection resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents connections to external resources from which more specialized connections like [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) are derived.

This resource type is abstract.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-resourceconnections?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) collection | Get a list of the [resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-resourceconnection-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) | Read the properties and relationships of a [resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowsupdates-resourceconnection-delete?view=graph-rest-beta) | None | Delete a [resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | An identifier for the resource connection. Key. Not nullable. Read-only. Returned by default. |
| state | microsoft.graph.windowsUpdates.resourceConnectionState | The state of the connection. The possible values are: `connected`, `notAuthorized`, `notFound`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.resourceConnection",
  "id": "String (identifier)",
  "state": "String"
}
```
