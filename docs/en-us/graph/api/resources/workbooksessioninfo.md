<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooksessioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# workbookSessionInfo resource type

Namespace: microsoft.graph

Provides information about workbook session.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "persistChanges": true
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | ID of the workbook session. |
| persistChanges | Boolean | `true` for persistent session. `false` for non-persistent session \(view mode\) |
