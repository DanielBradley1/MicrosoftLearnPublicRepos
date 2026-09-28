<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-failedoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# failedOperation resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents an export operation that failed to complete.

Inherits from [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The start time of the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0). |
| id | String | The unique identifier for the **failedOperation**. Inherited from [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0). |
| lastActionDateTime | DateTimeOffset | The time of the last action of the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0). |
| status | microsoft.graph.longRunningOperationStatus | The status of the operation. Supports a subset of the values for **longRunningOperationStatus**. Possible value is: `failed`. Inherited from [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| error | [microsoft.graph.publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Information about the error that caused the failure. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.failedOperation",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "status": "String"
}
```
