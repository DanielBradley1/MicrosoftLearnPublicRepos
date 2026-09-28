<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-25 -->

# restorePointSearchResult resource type

Namespace: microsoft.graph

Contains a list of [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) objects associated with a [protectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| artifactHitCount | Int32 | Total number of mailbox items that can be restored for a granular restore session. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| restorePoint | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) | Represents the date and time when an [artifact](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0) is protected by a [protectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) and can be restored. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restorePointSearchResult",
  "artifactHitCount": "Int32"
}
```
