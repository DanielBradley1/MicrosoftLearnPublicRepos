<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# itemEmail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about email addresses associated with the user.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-emails?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) collection | Get the itemEmail resources from the emails navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-emails?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) | Create a new itemEmail object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/itememail-get?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) | Read the properties and relationships of an [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/itememail-update?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) | Update the properties of an [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/itememail-delete?view=graph-rest-beta) | None | Deletes an [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | String | The email address itself. |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| displayName | String | The name or label a user has associated with a particular email address. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| type | emailType | The type of email address. The possible values are: `unknown`, `work`, `personal`, `main`, `other`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemEmail",
  "id": "0f30bf5d-bf5d-0f30-5dbf-300f5dbf300f",
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
  "address": "String",
  "displayName": "String",
  "type": "String"
}
```
