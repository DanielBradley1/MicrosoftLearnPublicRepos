<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# industryDataRunActivity resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract base type for all activity types. This resource represents the current or file state of the activity within a single [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta). Possible statuses for a run are:

- `inProgress`: The current [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) is running the activity.
- `completed`: The activity was successfully run.
- `completedWithErrors`: The activity ran to completion but encountered one or more error conditions during the run.
- `completedWithWarnings`: The activity ran to completion but encountered one or more warning conditions during the run.
- `skipped`: The [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta) didn't run the activity.
- `failed`: The activity encountered an unrecoverable error during the run.

Base type of [inboundFlowActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflowactivity?view=graph-rest-beta) and [outboundFlowActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundflowactivity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockingError | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | An error object to diagnose critical failures in an activity. |
| displayName | String | The name of the running flow. |
| status | microsoft.graph.industryData.industryDataActivityStatus | The current status of the activity. The possible values are: `inProgress`, `skipped`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activity | [microsoft.graph.industryData.industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta) | The flow that was run by this activity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataRunActivity",
  "blockingError": { "@odata.type": "microsoft.graph.publicError" },
  "displayName": "String",
  "status": "String"
}
```
