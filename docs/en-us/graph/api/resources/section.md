<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# section resource type

Namespace: microsoft.graph

Represents a section within a [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0). A [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) is always the parent of a [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0).

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **section**, including the street, city, state, country or region, and postal code. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| displayName | String | The display name of the **section**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **section** location in latitude, longitude, and \(optionally\) altitude coordinates. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| id | String | The unique identifier for the section. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Indicates whether the **section** is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | User-defined description of the **section**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| parentId | String | The ID of a parent [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) or [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the **section**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| tags | String collection | Custom tags that are associated with the section for categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.section",
  "id": "String (identifier)",
  "displayName": "String",
  "geoCoordinates": {
    "@odata.type": "microsoft.graph.outlookGeoCoordinates"
  },
  "phone": "String",
  "address": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "parentId": "String",
  "tags": [
    "String"
  ],
  "isWheelChairAccessible": "Boolean",
  "label": "String"
}
```
