<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/challengingword?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# challengingWord resource type

Namespace: microsoft.graph

Represents a word a student found challenging in a reading assignment submission.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int64 | Number of times the word was found challenging by the student during the reading session. |
| word | String | The specific word that the student found challenging during the reading session. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.challengingWord",
  "count": "Int64",
  "word": "String" 
}
```
