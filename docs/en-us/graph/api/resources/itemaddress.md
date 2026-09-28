<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# itemAddress resource type

Namespace: microsoft.graph

Represents a physical address and details of the location where the address is found.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-addresses?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) collection | Get the itemAddress resources from the addresses navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-addresses?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) | Create a new itemAddress object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/itemaddress-get?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) | Read the properties and relationships of an [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/itemaddress-update?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) | Update the properties of an [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/itemaddress-delete?view=graph-rest-beta) | None | Deletes an [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| detail | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-beta) | Details about the address itself. |
| displayName | String | Friendly name the user has assigned to this address. |
| geoCoordinates | [geoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/geocoordinates?view=graph-rest-beta) | The geocoordinates of the address. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemAddress",
  "id": "String (identifier)",
  "allowedAudiences": "String",
  "inference": {
    "@odata.type": "microsoft.graph.inferenceData"
  },
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "source": {
    "@odata.type": "microsoft.graph.personDataSource"
  },
  "displayName": "String",
  "detail": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "geoCoordinates": {
    "@odata.type": "microsoft.graph.geoCoordinates"
  }
}
```
