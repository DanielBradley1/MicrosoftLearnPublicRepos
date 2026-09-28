<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# industryDataActivity resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base type for all activities that are run by the underlying scheduler.

Base type of [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the activity. Maximum supported length is 100 characters. |
| readinessStatus | microsoft.graph.industryData.readinessStatus | The state of the activity from creation through to ready to do work. The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataActivity",
  "displayName": "String",
  "readinessStatus": "String"
}
```
