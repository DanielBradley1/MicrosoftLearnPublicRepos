<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreportsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# taskReportSummary resource type

Namespace: microsoft.graph.identityGovernance

A summary of task processing results for a specified time period. This summary allows the administrator to get a quick overview based on counts \(successful, failed, unprocessed, and total tasks\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedTasks | Int32 | The number of failed tasks in a report. |
| successfulTasks | Int32 | The total number of successful tasks in a report. |
| totalTasks | Int32 | The total number of tasks in a report. |
| unprocessedTasks | Int32 | The number of unprocessed tasks in a report. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.taskReportSummary",
  "successfulTasks": "Integer",
  "failedTasks": "Integer",
  "unprocessedTasks": "Integer",
  "totalTasks": "Integer"
}
```
