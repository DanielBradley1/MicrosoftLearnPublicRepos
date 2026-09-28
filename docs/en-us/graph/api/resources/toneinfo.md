<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/toneinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# toneInfo resource type

Namespace: microsoft.graph

A single DTMF event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sequenceId | Int64 | An incremental identifier used for ordering DTMF events. |
| tone | tone | The possible values are: `tone0`, `tone1`, `tone2`, `tone3`, `tone4`, `tone5`, `tone6`, `tone7`, `tone8`, `tone9`, `star`, `pound`, `a`, `b`, `c`, `d`, `flash`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "sequenceId": 1024,
  "tone": "tone0 | tone1 | tone2 | tone3 | tone4 | tone5 | tone6 | tone7 | tone8 | tone9 | star | pound | a | b | c | d | flash"
}
```
