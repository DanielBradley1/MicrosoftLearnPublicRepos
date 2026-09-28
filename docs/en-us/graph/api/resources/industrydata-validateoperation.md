<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# validateOperation resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract type for the asynchronous operation that results from any operation that validates data.

Inherits from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta).

Base type of [fileValidateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this operation was created. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| errors | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) collection | Set of errors discovered through validation. |
| id | String | The unique identifier for the operation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastActionDateTime | DateTimeOffset | The date and time when the last action was run on this operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| resourceLocation | String | The canonical URL of the resource. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| status | longRunningOperationStatus | The status of the long-running operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |
| statusDetail | String | The detail about the status value. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| warnings | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) collection | Set of warnings discovered through validation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.validateOperation",
  "createdDateTime": "String (timestamp)",
  "errors": [
    {
      "@odata.type": "microsoft.graph.publicError"
    }
  ],
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String",
  "warnings": [
    {
      "@odata.type": "microsoft.graph.publicError"
    }
  ]
}
```
