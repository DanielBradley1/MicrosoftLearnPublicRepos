<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unavailableplacemode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-27 -->

# unavailablePlaceMode resource type

Namespace: microsoft.graph

Describes why a desk or a workspace is marked as unavailable for booking.

This mode is supported for [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0) and [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0) objects.

Inherits from [placeMode](https://learn.microsoft.com/en-us/graph/api/resources/placemode?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reason | String | The reason a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) is marked unavailable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unavailablePlaceMode",
  "reason": "String"
}
```
