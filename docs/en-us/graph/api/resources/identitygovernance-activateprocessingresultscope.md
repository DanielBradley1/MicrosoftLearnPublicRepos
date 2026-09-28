<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activateprocessingresultscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# activateProcessingResultScope resource type

Namespace: microsoft.graph.identityGovernance

Represents the processing results scope for a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) of a workflow.

Inherits from [microsoft.graph.identityGovernance.activationScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activationscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| taskScope | microsoft.graph.identityGovernance.activationTaskScopeType | The specific tasks in the processing result scope. The possible values are: `allTasks`, `failedTasks`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| processingResults | [microsoft.graph.identityGovernance.userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) collection | The specific processing results for a run of a workflow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.activateProcessingResultScope",
  "taskScope": "String"
}
```
