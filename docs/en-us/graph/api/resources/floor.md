<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# floor resource type

Namespace: microsoft.graph

Represents a floor within a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). A [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) is always the parent of a [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0).

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **floor**, including the street, city, state, country or region, and postal code. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| displayName | String | The name that is associated with the floor. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **floor** location in latitude, longitude, and \(optionally\) altitude coordinates. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| id | String | The unique identifier for the **floor**. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Indicates whether **floor** is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | User-defined description of the **floor**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| parentId | String | The ID of a parent [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the **floor**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| sortOrder | Int32 | Specifies the sort order of the **floor**. For example, a floor might be named "Lobby" with a sort order of `0` to show this floor first in ordered lists. |
| tags | String collection | Custom tags that are associated with the **floor** for categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.floor",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "displayName": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "id": "String (identifier)",
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "parentId": "String",
  "phone": "String",
  "sortOrder": "Int32",
  "tags": ["String"]
}
```
