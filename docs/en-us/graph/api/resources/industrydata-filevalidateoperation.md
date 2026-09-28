<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# fileValidateOperation resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the asynchronous operation that results from any operation that validates file data.

Loop through the list to upload the latest CSV files in preparation for basic file validation. Once the files have been uploaded, call the [industryDataConnector: validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) endpoint to validate the uploaded files and finalize the upload session. After the files have been validated, they are moved to an internal container for processing by an [inboundFlow](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-inboundflow?view=graph-rest-beta).

The [industryDataConnector: validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) action is a long-running operation. The link to the operation is returned in the `Location` header. After the validation is complete, you can obtain the results through the `Location` URI.

We recommend polling no less than every 5 seconds while the status is `in progress`.

Inherits from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-filevalidateoperation-list?view=graph-rest-beta) | [microsoft.graph.industryData.fileValidateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta) collection | Get a list of the [fileValidateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-filevalidateoperation-get?view=graph-rest-beta) | [microsoft.graph.industryData.fileValidateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta) | Read the properties and relationships of an [fileValidateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filevalidateoperation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this operation was created. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| errors | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) collection | Set of errors discovered through validation. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| id | String | The unique identifier for the operation. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| lastActionDateTime | DateTimeOffset | The date and time when the last action was run on this operation. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| resourceLocation | String | The canonical URL of the resource. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| status | longRunningOperationStatus | The status of the long-running operation. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |
| statusDetail | String | The detail about the status value. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |
| validatedFiles | String collection | Set of files validated by the validate operation. |
| warnings | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) collection | Set of warnings discovered through validation. Inherited from [validateOperation](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-validateoperation?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.fileValidateOperation",
  "createdDateTime": "String (timestamp)",
  "errors": [{ "@odata.type": "microsoft.graph.publicError" }],
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String",
  "validatedFiles": ["String"],
  "warnings": [{ "@odata.type": "microsoft.graph.publicError" }]
}
```
