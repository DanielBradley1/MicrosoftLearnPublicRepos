<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# itemPublication resource type

Namespace: microsoft.graph

Represents a publication or article that has been associated with a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-publications?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) collection | Get the itemPublication resources from the publications navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-publications?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) | Create a new itemPublication object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/itempublication-get?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) | Read the properties and relationships of an [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/itempublication-update?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) | Update the properties of an [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/itempublication-delete?view=graph-rest-beta) | None | Deletes an [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| description | String | Description of the publication. |
| displayName | String | Title of the publication. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| publishedDate | Date | The date that the publication was published. |
| publisher | String | Publication or publisher for the publication. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| thumbnailUrl | String | URL referencing a thumbnail of the publication. |
| webUrl | String | URL referencing the publication. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemPublication",
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
  "publishedDate": "Date",
  "publisher": "String",
  "thumbnailUrl": "String",
  "webUrl": "String"
}
```
