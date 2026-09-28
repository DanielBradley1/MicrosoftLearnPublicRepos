<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# skillProficiency resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about skills associated with a user in various services.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-skills?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) collection | Get the skillProficiency resources from the skills navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-skills?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) | Create a new skillProficiency object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/skillproficiency-get?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) | Read the properties and relationships of a [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/skillproficiency-update?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) | Update the properties of a [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/skillproficiency-delete?view=graph-rest-beta) | None | Deletes a [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| categories | String collection | Contains categories a user has associated with the skill \(for example, personal, professional, hobby\). |
| collaborationTags | String collection | Contains experience scenario tags a user has associated with the interest. Allowed values in the collection are: `askMeAbout`, `ableToMentor`, `wantsToLearn`, `wantsToImprove`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| displayName | String | Contains a friendly name for the skill. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| proficiency | skillProficiencyLevel | Detail of the users proficiency with this skill. The possible values are: `elementary`, `limitedWorking`, `generalProfessional`, `advancedProfessional`, `expert`, `unknownFutureValue`. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| webUrl | String | Contains a link to an information source about the skill. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.skillProficiency",
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
  "displayName": "String",
  "proficiency": "String",
  "webUrl": "String",
  "collaborationTags": [
    "String"
  ]
}
```
