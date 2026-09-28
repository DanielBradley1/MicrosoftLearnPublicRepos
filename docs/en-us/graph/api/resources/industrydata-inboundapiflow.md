<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundapiflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# inboundApiFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a flow to import data via an external API into the canonical store.

Inherits from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-inboundapiflow-post?view=graph-rest-beta) | [microsoft.graph.industryData.inboundApiFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundapiflow?view=graph-rest-beta) | Create a new **inboundApiFlow** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-inboundapiflow-update?view=graph-rest-beta) | [microsoft.graph.industryData.inboundApiFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundapiflow?view=graph-rest-beta) | Update the properties of an **inboundApiFlow** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataDomain | microsoft.graph.industryData.inboundDomain | The category of data that this flow imports. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta).The possible values are: `educationRostering`, `unknownFutureValue`. |
| displayName | String | The name of the activity. Inherited from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta). |
| effectiveDateTime | DateTimeOffset | The time when the flow is first allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta). |
| expirationDateTime | DateTimeOffset | The time when the flow is no longer allowed to run. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta). |
| readinessStatus | microsoft.graph.industryData.readinessStatus | The state of the activity from its creation through when it is ready to do work. Inherited from [industryDataActivity](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataactivity?view=graph-rest-beta).The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dataConnector | [microsoft.graph.industryData.industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) | The data connector to the source system from where this flow gets its data. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) |
| year | [microsoft.graph.industryData.yearTimePeriodDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yeartimeperioddefinition?view=graph-rest-beta) | The year associated to the data that this flow brings in. Inherited from [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.inboundApiFlow",
  "displayName": "String",
  "readinessStatus": "String",
  "dataDomain": "String",
  "effectiveDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)"
}
```
