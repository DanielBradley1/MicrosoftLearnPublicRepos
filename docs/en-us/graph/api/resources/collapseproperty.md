<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/collapseproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# collapseProperty resource type

Namespace: microsoft.graph

Specifies the criteria used for collapsing search results. Applies only to sortable/refinable properties.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fields | String Collection | Defines the collapse group to trim results. The properties in this collection must be sortable/refinable properties. Required. |
| limit | Int16 | Defines a maximum limit count for this field. This numeric value must be a positive integer. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fields": ["String"],
  "limit": 1024
}
```
