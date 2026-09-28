<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# languageProficiency resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about languages that a user has added to their [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta).

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-languages?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) collection | Get the languageProficiency resources from the languages navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-languages?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) | Create a new languageProficiency object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/languageproficiency-get?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) | Read the properties and relationships of a [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/languageproficiency-update?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) | Update the properties of a [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/languageproficiency-delete?view=graph-rest-beta) | None | Deletes a [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| displayName | String | Contains the long-form name for the language. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| reading | languageProficiencyLevel | Represents the users reading comprehension for the language represented by the object. The possible values are: `elementary`, `conversational`, `limitedWorking`, `professionalWorking`, `fullProfessional`, `nativeOrBilingual`, `unknownFutureValue`. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| spoken | languageProficiencyLevel | Represents the users spoken proficiency for the language represented by the object. The possible values are: `elementary`, `conversational`, `limitedWorking`, `professionalWorking`, `fullProfessional`, `nativeOrBilingual`, `unknownFutureValue`. |
| tag | String | Contains the four-character BCP47 name for the language \(en-US, no-NB, en-AU\). |
| written | languageProficiencyLevel | Represents the users written proficiency for the language represented by the object. The possible values are: `elementary`, `conversational`, `limitedWorking`, `professionalWorking`, `fullProfessional`, `nativeOrBilingual`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.languageProficiency",
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
  "tag": "String",
  "spoken": "String",
  "written": "String",
  "reading": "String"
}
```
