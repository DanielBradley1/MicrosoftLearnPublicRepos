<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# inboundFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for all flows that bring data into the canonical store in the Azure Data Lake. An **inboundFlow** represents an activity that a service runs. This is an abstract type.

By default, the inbound flow activates twice \(2x\) daily. For more details, see [industryDataRun](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarun?view=graph-rest-beta).

Inherits from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta).

Base type of [inboundFileFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundfileflow?view=graph-rest-beta) and [inboundApiFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundapiflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-inboundflow-list?view=graph-rest-beta) | [microsoft.graph.industryData.inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) collection | Get a list of the [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-inboundflow-get?view=graph-rest-beta) | [microsoft.graph.industryData.inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) | Read the properties and relationships of an [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-inboundflow-delete?view=graph-rest-beta) | None | Delete an [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataDomain | microsoft.graph.industryData.inboundDomain | The category of data that this flow imports. The possible values are: `educationRostering`, `unknownFutureValue`. |
| displayName | String | The name of the activity. Inherited from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta). |
| effectiveDateTime | DateTimeOffset | The start of the time window when the flow is allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| expirationDateTime | DateTimeOffset | The end of the time window when the flow is allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| readinessStatus | microsoft.graph.industryData.readinessStatus | The state of the activity from its creation through when it is ready to do work. Inherited from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta). The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dataConnector | [microsoft.graph.industryData.industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) | The data connector to the source system from where this flow gets its data. |
| year | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | The year associated to the data that this flow brings in. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.inboundFlow",
  "dataDomain": "String",
  "displayName": "String",
  "effectiveDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "readinessStatus": "String"
}
```
