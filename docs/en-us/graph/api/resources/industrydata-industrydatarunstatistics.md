<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunstatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# industryDataRunStatistics resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents statistics for a single run.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityStatistics | [microsoft.graph.industryData.industryDataActivityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta) collection | The collection of statistics for each activity included in this run. |
| inboundTotals | [microsoft.graph.industryData.aggregatedInboundStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-aggregatedinboundstatistics?view=graph-rest-beta) | The aggregate statistics for all inbound flows. |
| runId | String | The ID of the underlying run for the statistics. |
| status | microsoft.graph.industryData.industryDataRunStatus | The latest status of the run. The possible values are: `running`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataRunStatistics",
  "activityStatistics": [
    {
      "@odata.type": "microsoft.graph.industryData.inboundActivityResults"
    }
  ],
  "inboundTotals": {
    "@odata.type": "microsoft.graph.industryData.aggregatedInboundStatistics"
  },
  "runId": "String",
  "status": "String"
}
```
