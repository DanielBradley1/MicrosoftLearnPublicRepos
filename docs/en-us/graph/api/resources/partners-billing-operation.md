<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# operation resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents an operation to export the billing data of a partner.

Base type of [exportSuccessOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-exportsuccessoperation?view=graph-rest-1.0), [failedOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-failedoperation?view=graph-rest-1.0), and [runningOperation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-runningoperation?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/partners-billing-operation-get?view=graph-rest-1.0) | [microsoft.graph.partners.billing.operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0) | Read the properties and relationships of an [operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The start time of the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique identifier for the **operation**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0). |
| lastActionDateTime | DateTimeOffset | The time of the last action of the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| status | microsoft.graph.longRunningOperationStatus | The status of the operation. The possible values are: `notStarted`, `running`, `completed`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.operation",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "status": "String"
}
```
