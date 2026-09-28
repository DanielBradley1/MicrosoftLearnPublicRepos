<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-rundetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# runDetails resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **runDetails** resource type is deprecated and will be removed on 2026-10-01. Run history is no longer surfaced through the custom detection rules API.

Represents an instance of a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) run.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorCode | [microsoft.graph.security.huntingRuleErrorCode](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#huntingruleerrorcode-values) | Error code of the most recent run that encountered an error. The possible values are: `queryExecutionFailed`, `queryExecutionThrottling`, `queryExceededResultSize`, `queryLimitsExceeded`, `queryTimeout`, `alertCreationFailed`, `alertReportNotFound`, `partialRowsFailed`, `unknownFutureValue`. |
| failureReason | String | Reason for failure when the custom detection last ran and failed. See the table below. |
| lastRunDateTime | DateTimeOffset | Timestamp when the custom detection was last run. |
| status | [microsoft.graph.security.huntingRuleRunStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#huntingrulerunstatus-values) | Status of custom detection when it was last run. The possible values are: `running`, `completed`, `failed`, `partiallyFailed`, `unknownFutureValue`. |

#### Failure Reasons table

| errorCode | Reason |
| --- | --- |
| queryExecutionFailed | An unexpected error occurred during query execution. Contact support if this failure reoccurs. |
| queryExecutionThrottling | Query execution was throttled due to exceeded tenant resources. |
| queryExceededResultSize | Result size limit exceeded. Only the first 100 query results were processed. |
| queryLimitsExceeded | Query execution was preempted. This failure can be due to high CPU and/or memory resource consumption. Optimize your query by following best practices and try again. |
| queryTimeout | Query execution took longer than the assigned timeout and was aborted. |
| alertCreationFailed | An unexpected error occurred while generating alerts from query results. Contact support if this failure reoccurs. |
| alertReportNotFound | An event couldn't be matched to the given Timestamp, DeviceId, or ReportId. Check the query for aggregation expressions on those columns. |
| partialRowsFailed | Only a subset of query results could be processed to alerts. Contact support if this failure reoccurs. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.runDetails",
  "lastRunDateTime": "String (timestamp)",
  "status": "String",
  "failureReason": "String",
  "errorCode": "String"
}
```
