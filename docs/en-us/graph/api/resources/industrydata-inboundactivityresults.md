<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundactivityresults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# inboundActivityResults resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents results of a single run of an inbound flow.

Inherits from [industryDataActivityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityId | String | The identifier for the activity that is being reported on. Inherited from [industryDataActivityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta). |
| displayName | String | The display name of the underlying flow. Inherited from [industryDataActivityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta). |
| errors | Int32 | Number of errors encountered while processing the inbound flow. |
| groups | [microsoft.graph.industryData.industryDataRunEntityCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunentitycountmetric?view=graph-rest-beta) | Counts of active and inactive groups processed by the inbound flow. |
| matchedPeopleByRole | [microsoft.graph.industryData.industryDataRunRoleCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunrolecountmetric?view=graph-rest-beta) collection | Number of people matched to a Microsoft Entra user, by role. |
| memberships | [microsoft.graph.industryData.industryDataRunEntityCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunentitycountmetric?view=graph-rest-beta) | Counts of active and inactive memberships processed by the inbound flow. |
| organizations | [microsoft.graph.industryData.industryDataRunEntityCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunentitycountmetric?view=graph-rest-beta) | Counts of active and inactive organizations processed by the inbound flow. |
| people | [microsoft.graph.industryData.industryDataRunEntityCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunentitycountmetric?view=graph-rest-beta) | Counts of active and inactive people processed by the inbound flow. |
| status | microsoft.graph.industryData.industryDataActivityStatus | The latest status of the activity in the run group. Inherited from [industryDataActivityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivitystatistics?view=graph-rest-beta). The possible values are: `inProgress`, `skipped`, `failed`, `completed`, `completedWithErrors`, `completedWithWarnings`, `unknownFutureValue`. |
| unmatchedPeopleByRole | [microsoft.graph.industryData.industryDataRunRoleCountMetric](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunrolecountmetric?view=graph-rest-beta) collection | Number of people not matched to a Microsoft Entra user, by role. |
| warnings | Int32 | Number of warnings encountered while processing the inbound flow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.inboundActivityResults",
  "activityId": "String",
  "displayName": "String",
  "errors": "Int32",
  "groups": {
    "@odata.type": "microsoft.graph.industryData.industryDataRunEntityCountMetric"
  },
  "matchedPeopleByRole": [
    {
      "@odata.type": "microsoft.graph.industryData.industryDataRunRoleCountMetric"
    }
  ],
  "memberships": {
    "@odata.type": "microsoft.graph.industryData.industryDataRunEntityCountMetric"
  },
  "organizations": {
    "@odata.type": "microsoft.graph.industryData.industryDataRunEntityCountMetric"
  },
  "people": {
    "@odata.type": "microsoft.graph.industryData.industryDataRunEntityCountMetric"
  },
  "status": "String",
  "unmatchedPeopleByRole": [
    {
      "@odata.type": "microsoft.graph.industryData.industryDataRunRoleCountMetric"
    }
  ],
  "warnings": "Int32"
}
```
