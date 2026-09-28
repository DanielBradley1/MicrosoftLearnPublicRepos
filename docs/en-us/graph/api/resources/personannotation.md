<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# personAnnotation resource type

Namespace: microsoft.graph

Provides information within notes that the user has associated with themselves in various services and shared with others.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-notes?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) collection | Get the personAnnotation resources from the notes navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-notes?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) | Create a new personAnnotation object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/personannotation-get?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) | Read the properties and relationships of a [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/personannotation-update?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) | Update the properties of a [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/personannotation-delete?view=graph-rest-beta) | None | Deletes a [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| detail | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Contains the detail of the note itself. |
| displayName | String | Contains a friendly name for the note. |
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
  "@odata.type": "#microsoft.graph.personAnnotation",
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
  "detail": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "displayName": "String"
}
```
