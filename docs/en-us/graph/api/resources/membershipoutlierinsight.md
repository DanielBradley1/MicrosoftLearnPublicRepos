<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/membershipoutlierinsight?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# membershipoutlierinsight resource type

Namespace: microsoft.graph

Represents an insight provided to reviewers based on whether a user has low affiliation with other users within the group.

Inherits from [governanceInsight](https://learn.microsoft.com/en-us/graph/api/resources/governanceinsight?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containerId | String | Indicates the identifier of the container, for example, a group ID. |
| memberId | String | Indicates the identifier of the user. |
| outlierContainerType | outlierContainerType | Indicates the type of container. The possible values are: `group`, `unknownFutureValue`. |
| outlierMemberType | outlierMemberType | Indicates the type of outlier member. The possible values are: `user`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| container | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Navigation link to the container directory object. For example, to a group. |
| lastModifiedBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | Navigation link to a member object who modified the record. For example, to a user. |
| member | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Navigation link to a member object. For example, to a user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.membershipOutlierInsight",
  "id": "String (identifier)",
  "insightCreatedDateTime": "String (timestamp)",
  "memberId": "String",
  "containerId": "String",
  "outlierContainerType": "String",
  "outlierMemberType": "String"
}
```
