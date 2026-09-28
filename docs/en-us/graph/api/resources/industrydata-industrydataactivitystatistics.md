<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# industryDataActivityStatistics resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base type for statistics for a single activity within a run.

Base type of [inboundActivityResults](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundactivityresults?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityId | String | The identifier for the activity that is being reported on. |
| displayName | String | The display name of the underlying flow. |
| status | microsoft.graph.industryData.industryDataActivityStatus | The latest status of the activity in the run. The possible values are: `inProgress`, `skipped`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataActivityStatistics",
  "activityId": "String",
  "displayName": "String",
  "status": "String"
}
```
