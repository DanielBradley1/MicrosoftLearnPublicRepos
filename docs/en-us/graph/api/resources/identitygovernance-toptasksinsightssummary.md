<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-toptasksinsightssummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-20 -->

# topTasksInsightsSummary resource type

Namespace: microsoft.graph.identityGovernance

Represents a summary of the top tasks ran within a tenant, including total, failed, and successful tasks and user processing history.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedTasks | Int32 | Count of failed runs of the task. |
| failedUsers | Int32 | Count of failed users who were processed by the task. |
| successfulTasks | Int32 | Count of successful runs of the task. |
| successfulUsers | Int32 | Count of successful users processed by the task. |
| taskDefinitionDisplayName | String | The name of the task. |
| taskDefinitionId | String | The task ID. |
| totalTasks | Int32 | Count of total runs of the task. |
| totalUsers | Int32 | Count of total users processed by the task. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.topTasksInsightsSummary",
  "taskDefinitionId": "String",
  "taskDefinitionDisplayName": "String",
  "totalTasks": "Integer",
  "successfulTasks": "Integer",
  "failedTasks": "Integer",
  "totalUsers": "Integer",
  "successfulUsers": "Integer",
  "failedUsers": "Integer"
}
```
