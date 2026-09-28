<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datapolicyoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# dataPolicyOperation resource type

Namespace: microsoft.graph

Represents a submitted data policy operation. It contains necessary information for tracking the status of an operation. For example, a company administrator can submit a data policy operation request to export an employee's company data, and then later track that request.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/datapolicyoperation-get?view=graph-rest-1.0) | [dataPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/datapolicyoperation?view=graph-rest-1.0) | Retrieve properties of the **dataPolicyOperation** object. |
| [Export personal data](https://learn.microsoft.com/en-us/graph/api/user-exportpersonaldata?view=graph-rest-1.0) | None | Submit a data policy operation request to export organizational user's data which can later be read using [Get dataPolicyOperation](https://learn.microsoft.com/en-us/graph/api/datapolicyoperation-get?view=graph-rest-1.0) |

## Properties

> **Note:** All properties of this resource are read-only.

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | Represents when the request for this data policy operation was completed, in UTC time, using the ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Null until the operation completes. |
| id | String | Unique key for this operation. |
| status | dataPolicyOperationStatus | The possible values are: `notStarted`, `running`, `complete`, `failed`, `unknownFutureValue`. |
| storageLocation | String | The URL location to where data is being exported for export requests. |
| userId | String | The id for the user on whom the operation is performed. |
| submittedDateTime | DateTimeOffset | Represents when the request for this data operation was submitted, in UTC time, using the ISO 8601 format. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| progress | String | Specifies the progress of an operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "completedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "progress": "String (double)",
  "status": "string",
  "storageLocation": "String",
  "userId": "String",
  "submittedDateTime": "String (timestamp)"
}
```
