<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# personCertification resource type

Namespace: microsoft.graph

Represents a certification or designation which has been associated with a user's [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-certifications?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) collection | Get the personCertification resources from the certifications navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-certifications?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) | Create a new personCertification object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/personcertification-get?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) | Read the properties and relationships of an [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/personcertification-update?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) | Update the properties of an [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/personcertification-delete?view=graph-rest-beta) | None | Deletes an [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| certificationId | String | The referenceable identifier for the certification. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| description | String | Description of the certification. |
| displayName | String | Title of the certification. |
| endDate | Date | The date that the certification expires. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| issuedDate | Date | The date that the certification was issued. |
| issuingAuthority | String | Authority which granted the certification. |
| issuingCompany | String | Company which granted the certification. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| startDate | Date | The date that the certification became valid. |
| thumbnailUrl | String | URL referencing a thumbnail of the certification. |
| webUrl | String | URL referencing the certification. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.personCertification",
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
  "certificationId": "String",
  "description": "String",
  "displayName": "String",
  "endDate": "Date",
  "issuedDate": "Date",
  "issuingAuthority": "String",
  "issuingCompany": "String",
  "startDate": "Date",
  "thumbnailUrl": "String",
  "webUrl": "String"
}
```
