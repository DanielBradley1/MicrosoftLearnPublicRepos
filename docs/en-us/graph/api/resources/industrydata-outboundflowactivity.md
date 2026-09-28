<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-outboundflowactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# outboundFlowActivity resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about the run of an outbound flow.

Inherits from [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockingError | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | An error object to diagnose critical failures in an activity. Inherited from [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta). |
| displayName | String | The name of the running flow. Inherited from [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta). |
| status | microsoft.graph.industryData.industryDataActivityStatus | The current status of the activity. Inherited from [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta). The possible values are: `inProgress`, `skipped`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activity | [microsoft.graph.industryData.industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta) | The flow that was run by this activity. Inherited from [industryDataRunActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunactivity?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.outboundFlowActivity",
  "blockingError": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "displayName": "String",
  "status": "String"
}
```
