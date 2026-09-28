<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationalActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents data that a user has supplied related to undergraduate, graduate, postgraduate or other educational activities.

Inherits metadata properties from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-educationalactivities?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) collection | Get the educationalActivity resources from the educationalActivities navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-educationalactivities?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) | Create a new educationalActivity object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationalactivity-get?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) | Read the properties and relationships of an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationalactivity-update?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) | Update the properties of an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationalactivity-delete?view=graph-rest-beta) | None | Deletes an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | String | The audiences that are able to see the values contained within the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| completionMonthYear | Date | The month and year the user graduated or completed the activity. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| endMonthYear | Date | The month and year the user completed the educational activity referenced. |
| id | String | Identifier used for individually addressing the entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| institution | [institutionData](https://learn.microsoft.com/en-us/graph/api/resources/institutiondata?view=graph-rest-beta) | Contains details of the institution studied at. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| program | [educationalActivityDetail](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivitydetail?view=graph-rest-beta) | Contains extended information about the program or course. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values originated if synced from another service. Inherited from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta). |
| startMonthYear | Date | The month and year the user commenced the activity referenced. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationalActivity",
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
  "completionMonthYear": "Date",
  "endMonthYear": "Date",
  "institution": {
    "@odata.type": "microsoft.graph.institutionData"
  },
  "program": {
    "@odata.type": "microsoft.graph.educationalActivityDetail"
  },
  "startMonthYear": "Date"
}
```
