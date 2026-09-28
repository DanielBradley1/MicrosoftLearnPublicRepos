<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvaloperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status and details for an operation performed on an [approvalItem](https://learn.microsoft.com/en-us/graph/api/resources/approvalitem?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/approvaloperation-get?view=graph-rest-beta) | [approvalOperation](https://learn.microsoft.com/en-us/graph/api/resources/approvaloperation?view=graph-rest-beta) | Read the properties and relationships of an [approvalOperation](https://learn.microsoft.com/en-us/graph/api/resources/approvaloperation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the operation was created. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error if the operation failed. |
| lastActionDateTime | DateTimeOffset | The date and time when this operation was most recently updated. |
| resourceLocation | String | The URL for the resource that was newly created or acted upon. |
| status | approvalOperationStatus | The status of the operation. The possible values are: `scheduled`, `inProgress`, `succeeded`, `failed`, `timeout`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalOperation",
  "createdDateTime": "String (timestamp)",
  "lastActionDateTime": "String (timestamp)",
  "status": "String",
  "resourceLocation": "String",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```
