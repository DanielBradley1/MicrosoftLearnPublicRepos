<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# projectParticipation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about projects associated with a user.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-projects?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) collection | Get the projectParticipation resources from the projects navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-projects?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) | Create a new projectParticipation object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/projectparticipation-get?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) | Read the properties and relationships of a [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/projectparticipation-update?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) | Update the properties of a [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/projectparticipation-delete?view=graph-rest-beta) | None | Deletes a [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| categories | String collection | Contains categories a user has associated with the project \(for example, digital transformation, oil rig\). |
| client | [companyDetail](https://learn.microsoft.com/en-us/graph/api/resources/companydetail?view=graph-rest-beta) | Contains detailed information about the client the project was for. |
| collaborationTags | String collection | Contains experience scenario tags a user has associated with the interest. Allowed values in the collection are: `askMeAbout`, `ableToMentor`, `wantsToLearn`, `wantsToImprove`. |
| colleagues | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | Lists people that also worked on the project. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| detail | [positionDetail](https://learn.microsoft.com/en-us/graph/api/resources/positiondetail?view=graph-rest-beta) | Contains detail about the user's role on the project. |
| displayName | String | Contains a friendly name for the project. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| sponsors | [relatedPerson](https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta) collection | The Person or people who sponsored the project. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.projectParticipation",
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
  "client": {
    "@odata.type": "microsoft.graph.companyDetail"
  },
  "displayName": "String",
  "detail": {
    "@odata.type": "microsoft.graph.positionDetail"
  },
  "colleagues": [
    {
      "@odata.type": "microsoft.graph.relatedPerson"
    }
  ],
  "sponsors": [
    {
      "@odata.type": "microsoft.graph.relatedPerson"
    }
  ],
  "collaborationTags": [
    "String"
  ]
}
```
