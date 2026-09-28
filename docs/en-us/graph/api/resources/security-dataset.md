<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-dataset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-12 -->

# dataSet resource type

Namespace: microsoft.graph.security

Represents an abstract base type for data sets used in eDiscovery.

Base type of [ediscoveryReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the data set. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the review set was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | The description of the data set. |
| displayName | String | The name of the data set. The name is unique with a maximum limit of 64 characters. |
| id | String | The unique identifier of the data set. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dataSet",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
