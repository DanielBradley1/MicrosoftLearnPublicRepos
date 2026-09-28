<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# longRunningOperation resource type

Namespace: microsoft.graph

Represents the status of a long-running Microsoft Graph API operation.

The following types derive from this object:

- [attackSimulationOperation](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationoperation?view=graph-rest-1.0)
- [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0)
- [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The start time of the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier of the operation. |
| lastActionDateTime | DateTimeOffset | The time of the last action in the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| resourceLocation | String | URI of the resource that the operation is performed on. |
| status | longRunningOperationStatus | The status of the operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |
| statusDetail | String | Details about the status of the operation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.longRunningOperation",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String"
}
```
