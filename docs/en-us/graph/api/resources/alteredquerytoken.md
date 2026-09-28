<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/alteredquerytoken?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# alteredQueryToken resource type

Namespace: microsoft.graph

Represents changed segments related to an original user query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| length | Int32 | Defines the length of a changed segment. |
| offset | Int32 | Defines the offset of a changed segment. |
| suggestion | String | Represents the corrected segment string. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "length": "Int32",
  "offset": "Int32",
  "suggestion": "String"
}
```
