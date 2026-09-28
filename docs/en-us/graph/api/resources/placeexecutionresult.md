<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/placeexecutionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# placeExecutionResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the upsert result of a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| children | [placeExecutionResult](https://learn.microsoft.com/en-us/graph/api/resources/placeexecutionresult?view=graph-rest-beta) collection | The upsert results of children places of the place. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error that occurred during the upsert of the place. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| succeededPlace | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta) | The created or updated place if the upsert is succeeded. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.placeExecutionResult",
  "children": [{"@odata.type": "microsoft.graph.placeExecutionResult"}],
  "error": {"@odata.type": "microsoft.graph.publicError"}
}
```
