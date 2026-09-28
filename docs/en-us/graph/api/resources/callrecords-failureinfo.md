<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-failureinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# failureInfo resource type

Namespace: microsoft.graph.callRecords

Represents information about why a call or portion of a call failed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reason | String | Classification of why a call or portion of a call failed. |
| stage | microsoft.graph.callRecords.failureStage | The stage when the failure occurred. The possible values are: `unknown`, `callSetup`, `midcall`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "reason": "String",
  "stage": "String"
}
```
