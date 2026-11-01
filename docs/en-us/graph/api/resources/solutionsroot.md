<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/solutionsroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# solutionsRoot resource type

Namespace: microsoft.graph

The entry point for cross-tenant migration APIs.

All Microsoft Graph calls to resources under `/solutions` use the following service root URL:

```http
https://graph.microsoft.com/{version}/solutions/
```

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| migrations | [migrationsRoot](https://learn.microsoft.com/en-us/graph/api/resources/migrationsroot?view=graph-rest-1.0) | The entry point for cross-tenant migration operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.solutionsRoot"
}
```
