<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# provisioningFlow resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A flow that provisions relevant records of a given entity type in the Microsoft 365 tenant. This is an abstract type.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-list-provisioningflows?view=graph-rest-beta) | [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) collection | Get a list of the provisioning flow objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-outboundprovisioningflowset-post-provisioningflows?view=graph-rest-beta) | [microsoft.graph.industryData.provisioningFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-provisioningflow?view=graph-rest-beta) | Create a new provisioning flow object. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/industrydata-provisioningflow-reset?view=graph-rest-beta) | None | Resets a provisioning flow object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the provisioning flow was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier for the provisioning flow. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the provisioning flow was most recently changed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| readinessStatus | microsoft.graph.industryData.readinessStatus | The state of the activity from creation through to ready to do work. The possible values are: `notReady`, `ready`, `failed`, `disabled`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.provisioningFlow",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "readinessStatus": "String",
  "id": "String (identifier)"
}
```
