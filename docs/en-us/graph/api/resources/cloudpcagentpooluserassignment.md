<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpooluserassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPoolUserAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an assignment of a user to a Cloud PC agent pool.

Inherits from [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta).

## Methods

For the list of supported methods, see [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the assignment. Read-only. Inherited from [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta). |
| userPrincipalId | String | The unique identifier of the user principal. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolUserAssignment",
  "id": "String (identifier)",
  "userPrincipalId": "String"
}
```
