<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# personAward resource type

Namespace: microsoft.graph

Represents an award that has been associated with a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-awards?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) collection | Get the personAward resources from the awards navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-awards?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) | Create a new personAward object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/personaward-get?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) | Read the properties and relationships of an [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/personaward-update?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) | Update the properties of an [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/personaward-delete?view=graph-rest-beta) | None | Delete an [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| description | String | Descpription of the award or honor. |
| displayName | String | Name of the award or honor. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| issuedDate | Date | The date that the award or honor was granted. |
| issuingAuthority | String | Authority which granted the award or honor. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| thumbnailUrl | String | URL referencing a thumbnail of the award or honor. |
| webUrl | String | URL referencing the award or honor. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.personAward",
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
  "description": "String",
  "displayName": "String",
  "issuedDate": "Date",
  "issuingAuthority": "String",
  "thumbnailUrl": "String",
  "webUrl": "String"
}
```
