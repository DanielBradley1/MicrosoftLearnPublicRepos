<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentrunfailureinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# agentRunFailureInfo resource type

Namespace: microsoft.graph

Describes a run-level failure in the **failureInfo** property of an [agentRun](https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta). This information is separate from the HTTP error response.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorType | String | The error classification, when available. |
| message | String | The human-readable failure detail, when available. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentRunFailureInfo",
  "message": "String",
  "errorType": "String"
}
```
