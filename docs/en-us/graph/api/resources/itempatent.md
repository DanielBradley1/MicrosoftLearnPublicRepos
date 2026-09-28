<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# itemPatent resource type

Namespace: microsoft.graph

Represents a granted or filed patent that has been added to a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-patents?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) collection | Get the itemPatent resources from the patents navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-patents?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) | Create a new itemPatent object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/itempatent-get?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) | Read the properties and relationships of an [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/itempatent-update?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) | Update the properties of an [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/itempatent-delete?view=graph-rest-beta) | None | Delete an [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| description | String | Descpription of the patent or filing. |
| displayName | String | Title of the patent or filing. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| isPending | Boolean | Indicates the patent is pending. |
| issuedDate | Date | The date that the patent was granted. |
| issuingAuthority | String | Authority that granted the patent. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| number | String | The patent number. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| webUrl | String | URL referencing the patent or filing. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemPatent",
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
  "isPending": "Boolean",
  "issuedDate": "Date",
  "issuingAuthority": "String",
  "number": "String",
  "webUrl": "String"
}
```
