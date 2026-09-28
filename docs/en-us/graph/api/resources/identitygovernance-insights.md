<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-insights?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-20 -->

# insights resource type

Namespace: microsoft.graph.identityGovernance

Represents insights into the health and processing of lifecycle workflows across different workflows. The insights include the number of total, successful, and failed workflow executions, tasks processed, and users processed across all workflows for the tenant for a given period.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get top workflows summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-topworkflowsprocessedsummary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.topWorkflowsInsightsSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-topworkflowsinsightssummary?view=graph-rest-1.0) collection | Summarizes the top runs for workflows for a given data range. |
| [Get top tasks summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-toptasksprocessedsummary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.topTasksInsightsSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-toptasksinsightssummary?view=graph-rest-1.0) collection | Summarizes the top runs for tasks for a given data range. |
| [Get workflows processed summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-workflowsprocessedsummary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowsInsightsSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsinsightssummary?view=graph-rest-1.0) | Summarizes the workflows, users, and tasks processed for a given date range. |
| [Get workflows processed by category](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-workflowsprocessedbycategory?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowsInsightsByCategory](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsinsightsbycategory?view=graph-rest-1.0) | Summarizes workflow processing for each workflow category for a given date range. |

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.insights",
  "id": "String (identifier)"
}
```
