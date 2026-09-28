<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termcolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# termColumn resource type

Namespace: microsoft.graph

Represents a managed metadata column in SharePoint.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowMultipleValues | Boolean | Specifies whether the column allows more than one value. |
| showFullyQualifiedName | Boolean | Specifies whether to display the entire term path or only the term label. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| parentTerm | microsoft.graph.termStore.term | Specifies the parent term for which the child terms can be selected as the column value. |
| termSet | microsoft.graph.termStore.set | Term set whose children can be selected as column's value. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "allowMultipleValues": true,
    "showFullyQualifiedName": false,
}
```
