<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# workPosition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about work positions associated with a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

This resource type inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-positions?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) collection | Get the workPosition resources from the positions navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-positions?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) | Create a new workPosition object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/workposition-get?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) | Read the properties and relationships of a [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workposition-update?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) | Update the properties of a [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/workposition-delete?view=graph-rest-beta) | None | Deletes a [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| categories | String collection | Categories that the user has associated with this position. |
| colleagues | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | Colleagues that are associated with this position. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| detail | [positionDetail](https://learn.microsoft.com/en-us/graph/api/resources/positiondetail?view=graph-rest-beta) | Contains detailed information about the position. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| isCurrent | Boolean | Denotes whether or not the position is current. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| manager | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) | Contains detail of the user's manager in this position. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workPosition",
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
  "categories": [
    "String"
  ],
  "detail": {
    "@odata.type": "microsoft.graph.positionDetail"
  },
  "manager": {
    "@odata.type": "microsoft.graph.relatedPerson"
  },
  "colleagues": [
    {
      "@odata.type": "microsoft.graph.relatedPerson"
    }
  ],
  "isCurrent": "Boolean"
}
```
