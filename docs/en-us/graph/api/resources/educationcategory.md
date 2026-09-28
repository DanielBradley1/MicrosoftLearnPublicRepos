<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# educationCategory resource type

Namespace: microsoft.graph

A category that can be applied to assignments.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationclass-post-category?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) | Create a new **educationCategory**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationcategory-get?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) | Get an existing **educationCategory**. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationcategory-delete?view=graph-rest-1.0) | None | Remove an **educationCategory**. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/educationcategory-delta?view=graph-rest-1.0) | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) collection | Get a list of newly created or updated **educationCategory** objects without having to perform a full read of the collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique identifier for the category. |
| id | String | Unique identifier for the category. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)"
}
```
