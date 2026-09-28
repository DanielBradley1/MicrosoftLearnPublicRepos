<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domainstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# domainState resource type

Namespace: microsoft.graph

Represents the status of asynchronous operations scheduled on a domain.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastActionDateTime | DateTimeOffset | Timestamp for when the last activity occurred. The value is updated when an operation is scheduled, the asynchronous task starts, and when the operation completes. |
| operation | String | Type of asynchronous operation. The values can be `ForceDelete` or `Verification`. |
| status | String | Current status of the operation.  <br>`Scheduled` - Operation is scheduled but hasn't started.  <br>`InProgress` - Task is in progress.  <br>`Failed` - The operation failed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "lastActionDateTime": "String (timestamp)",
  "operation": "String",
  "status": "String"
}
```
