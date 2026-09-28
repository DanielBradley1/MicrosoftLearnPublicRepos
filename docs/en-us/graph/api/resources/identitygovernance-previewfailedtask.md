<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-previewfailedtask?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-27 -->

# previewFailedTask resource type

Namespace: microsoft.graph.identityGovernance

Represents a [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) that failed during a preview operation of a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definitionId | String | The identifier of the task definition of the task that failed during the preview operation of a workflow. |
| failureReason | String | The reason why the task failed in the preview operation of a workflow. |
| name | String | The name of the task that failed within the preview operation of a workflow. |
| taskId | String | The identifier of the task that failed during the preview operation of a workflow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.previewFailedTask",
  "definitionId": "String",
  "failureReason": "String",
  "name": "String",
  "taskId": "String"
}
```
