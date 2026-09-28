<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/lookupcolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# LookupColumn resource type

Namespace: microsoft.graph

The **lookupColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the column's values are looked up from another source in the site.

## JSON representation

Here is a JSON representation of a **lookupColumn** resource.

```json
{
  "allowMultipleValues": true,
  "allowUnlimitedLength": false,
  "columnName": "string",
  "listId": "string",
  "primaryLookupColumnId": "string"
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **allowMultipleValues** | Boolean | Indicates whether multiple values can be selected from the source. |
| **allowUnlimitedLength** | Boolean | Indicates whether values in the column should be able to exceed the standard limit of 255 characters. |
| **columnName** | string | The name of the lookup source column. |
| **listId** | string | The unique identifier of the lookup source list. |
| **primaryLookupColumnId** | string | If specified, this column is a *secondary lookup*, pulling an additional field from the list item looked up by the *primary lookup*. Use the list item looked up by the *primary* as the source for the column named here. |
