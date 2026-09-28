<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-20 -->

# engagementAsyncOperation resource type

Namespace: microsoft.graph

Represents the status of a Viva Engage async operation that is an operation that transcends the lifetime of a single API request. These operations are long-running or too expensive to complete within the time frame of their original request.

When an async operation is initiated, the method returns a `202 Accepted` response code and an `Operation-Location` header that contains the location of the **engagementAsyncOperation**. Periodically check the status of the operation by making a GET request to this location; wait >30 seconds between checks. When the request completes successfully, the operation **status** indicates `succeeded` and the **resourceLocation** points to the created or modified resource.

Inherits from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/engagementasyncoperation-get?view=graph-rest-1.0) | [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0) | Get an [engagementAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0) to track a long-running operation request. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time when the operation was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| id | String | The unique identifier for the operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| lastActionDateTime | DateTimeOffset | Date and time when the async operation was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| operationType | [engagementAsyncOperationType](https://learn.microsoft.com/en-us/graph/api/resources/engagementasyncoperation?view=graph-rest-1.0#engagementasyncoperationtype-values) | The type of the long-running operation. The possible values are: `createCommunity`, `unknownFutureValue`. |
| resourceId | String | The ID of the object created or modified as a result of this async operation. |
| resourceLocation | String | The location of the object created or modified as a result of this async operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| status | longRunningOperationStatus | The status of the operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `skipped`, `unknownFutureValue`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| statusDetail | String | Details about the status of the operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |

### engagementAsyncOperationType values

| Member | Description |
| :--- | :--- |
| createCommunity | Operation to create a Viva Engage community. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementAsyncOperation",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "operationType": "String",
  "resourceId": "String",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String"
}
```
