<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calltranscriptioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# callTranscriptionInfo resource type

Namespace: microsoft.graph

Represents a single DTMF event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastModifiedDateTime | DateTime | The state modified time in UTC. |
| state | String | The possible values are: `notStarted`, `active`, `inactive`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "lastModifiedDateTime": "String (timestamp)",
  "state": "notStarted | active | inactive"
}
```
