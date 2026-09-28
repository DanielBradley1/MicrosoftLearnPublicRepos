<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# itemPhone resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about phone numbers associated with a user in various services.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-phones?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) collection | Get the itemPhone resources from the phones navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-phones?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) | Create a new itemPhone object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/itemphone-get?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) | Read the properties and relationships of an [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/itemphone-update?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) | Update the properties of an [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/itemphone-delete?view=graph-rest-beta) | None | Deletes an [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| displayName | String | Friendly name the user has assigned this phone number. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| number | String | Phone number provided by the user. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| type | phoneType | The type of phone number within the object. The possible values are: `home`, `business`, `mobile`, `other`, `assistant`, `homeFax`, `businessFax`, `otherFax`, `pager`, `radio`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemPhone",
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
  "type": "String",
  "number": "String"
}
```
