<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-15 -->

# itemFacet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for all resource types in the [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta) entity set.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAudiences | allowedAudiences | The audiences that are able to see the values contained within the associated entity. The possible values are: `me`, `family`, `contacts`, `groupMembers`, `organization`, `federatedOrganizations`, `everyone`, `unknownFutureValue`. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that created the entity. |
| createdDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. |
| id | String | Identifier used for individually addressing an entity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inference | [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) | Contains inference detail if the entity is inferred by the creating or modifying application. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Provides the identifier of the user and/or application that last modified the entity. |
| lastModifiedDateTime | DateTimeOffset | Provides the dateTimeOffset for when the entity was created. |
| source | [personDataSource](https://learn.microsoft.com/en-us/graph/api/resources/persondatasource?view=graph-rest-beta) | Where the values within an entity originated if synced from another service. |
| sources | [profileSourceAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/profilesourceannotation?view=graph-rest-beta) collection | Where the values within an entity originated if synced from another source. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.itemFacet",
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
  "sources": [
    {
      "@odata.type": "microsoft.graph.profileSourceAnnotation"
    }
  ]
}
```
