<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcPoolAssignment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a base assignment of a principal to a [Cloud PC pool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

Base type of [cloudPcAgentPoolUserAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpooluserassignment?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-list-assignments?view=graph-rest-beta) | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) collection | List the assignments of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| [Create](https://learn.microsoft.com/en-us/graph/api/cloudpcpool-post-assignments?view=graph-rest-beta) | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) | Create a new [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcpoolassignment-get?view=graph-rest-beta) | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) | Read the properties of a [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudpcpoolassignment-delete?view=graph-rest-beta) | None | Delete a [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the assignment. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcPoolAssignment",
  "id": "String (identifier)"
}
```
