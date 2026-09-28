<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# webAccount resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents web accounts the user has indicated they use or have added to their user [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

This resource type inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-webaccounts?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) collection | Get the webAccount resources from the webAccounts navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-webaccounts?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) | Create a new webAccount object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/webaccount-get?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) | Read the properties and relationships of a [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/webaccount-update?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) | Update the properties of a [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/webaccount-delete?view=graph-rest-beta) | None | Deletes a [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| description | String | Contains the description the user has provided for the account on the service being referenced. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| service | [serviceInformation](https://learn.microsoft.com/en-us/graph/api/resources/serviceinformation?view=graph-rest-beta) | Contains basic detail about the service that is being associated. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| statusMessage | String | Contains a status message from the cloud service if provided or synchronized. |
| userId | String | The user name displayed for the webaccount. |
| webUrl | String | Contains a link to the user's profile on the cloud service if one exists. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webAccount",
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
  "userId": "String",
  "service": {
    "@odata.type": "microsoft.graph.serviceInformation"
  },
  "statusMessage": "String",
  "webUrl": "String"
}
```
