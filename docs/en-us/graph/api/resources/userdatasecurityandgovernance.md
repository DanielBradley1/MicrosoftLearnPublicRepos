<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userdatasecurityandgovernance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# userDataSecurityAndGovernance resource type

Namespace: microsoft.graph

Provides access to data security and governance functionalities specifically scoped to the context of a single user.

Inherits from [dataSecurityAndGovernance](https://learn.microsoft.com/en-us/graph/api/resources/datasecurityandgovernance?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Process content](https://learn.microsoft.com/en-us/graph/api/userdatasecurityandgovernance-processcontent?view=graph-rest-1.0) | [processContentResponse](https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponse?view=graph-rest-1.0) | Process content against data security and governance policies in the context of this user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique ID of the data security and governance stream. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/datasecurityandgovernance?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.activitiesContainer](https://learn.microsoft.com/en-us/graph/api/resources/activitiescontainer?view=graph-rest-1.0) | Container for activity logs \(content processing and audit\) related to this user. ContainsTarget: true. |
| [Compute protection scopes](https://learn.microsoft.com/en-us/graph/api/userprotectionscopecontainer-compute?view=graph-rest-1.0) | [policyUserScope](https://learn.microsoft.com/en-us/graph/api/resources/policyuserscope?view=graph-rest-1.0) collection | Compute the protection scopes for this user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userDataSecurityAndGovernance",
  "activities": { "@odata.type": "microsoft.graph.activitiesContainer" },
  "id": "String (identifier)"
}
```
