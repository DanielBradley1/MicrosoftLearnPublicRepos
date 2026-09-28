<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-topworkflowsinsightssummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# topWorkflowsInsightsSummary resource type

Namespace: microsoft.graph.identityGovernance

Represents a summary of the workflows that are processed the most, or the *top workflows*, within a tenant, including workflow details and the total, failed, and successful run and processing history for the workflow.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedRuns | Int32 | Count of failed runs for workflow. |
| failedUsers | Int32 | Count of failed users who were processed. |
| successfulRuns | Int32 | Count of successful runs of the workflow. |
| successfulUsers | Int32 | Count of successful users processed by the workflow. |
| totalRuns | Int32 | Count of total runs of workflow. |
| totalUsers | Int32 | Total number of users processed by the workflow. |
| workflowCategory | microsoft.graph.identityGovernance.lifecycleWorkflowCategory | The category of the workflow. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`. |
| workflowDisplayName | String | The name of the workflow. |
| workflowId | String | The workflow ID. |
| workflowVersion | Int32 | The version of the workflow that was a top workflow ran. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.topWorkflowsInsightsSummary",
  "workflowId": "String",
  "workflowDisplayName": "String",
  "workflowCategory": "String",
  "totalRuns": "Integer",
  "successfulRuns": "Integer",
  "failedRuns": "Integer",
  "totalUsers": "Integer",
  "successfulUsers": "Integer",
  "failedUsers": "Integer",
  "workflowVersion": "Integer"
}
```
