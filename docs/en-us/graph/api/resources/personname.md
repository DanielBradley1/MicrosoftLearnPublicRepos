<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# personName resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents extended name information provided by the user or which they have associated within their [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-names?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) collection | Get the personName resources from the names navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-names?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) | Create a new [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) object from the names navigation property. |
| [Get](https://learn.microsoft.com/en-us/graph/api/personname-get?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) | Read the properties and relationships of a [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/personname-update?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) | Update the properties of a [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/personname-delete?view=graph-rest-beta) | None | Deletes a [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| displayName | String | Provides an ordered rendering of firstName and lastName depending on the locale of the user or their device. |
| first | String | First name of the user. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| initials | String | Initials of the user. |
| languageTag | String | Contains the name for the language \(en-US, no-NB, en-AU\) following IETF BCP47 format. |
| last | String | Last name of the user. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| maiden | String | Maiden name of the user. |
| middle | String | Middle name of the user. |
| nickname | String | Nickname of the user. |
| pronunciation | [yomiPersonName](https://learn.microsoft.com/en-us/graph/api/resources/yomipersonname?view=graph-rest-beta) | Guidance on how to pronounce the users name. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| suffix | String | Designators used after the users name \(eg: PhD.\) |
| title | String | Honorifics used to prefix a users name \(eg: Dr, Sir, Madam, Mrs.\) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.personName",
  "id": "e13f7a4d-303c-464f-a6af-80ea18eb74f3",
  "allowedAudiences": "organization",
  "inference": {
    "@odata.type": "microsoft.graph.inferenceData"
  },
  "createdDateTime": "2020-07-06T06:34:12.2294868Z",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "2020-07-06T06:34:12.2294868Z",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "source": {
    "@odata.type": "microsoft.graph.personDataSource"
  },
  "displayName": "Innocenty Popov",
  "first": "Innocenty",
  "initials": "IP",
  "last": "Popov",
  "languageTag": "en-US",
  "maiden": null,
  "middle": null,
  "nickname": "Kesha",
  "suffix": null,
  "title": null,
  "pronunciation": {
    "@odata.type": "microsoft.graph.yomiPersonName"
  }
}
```
