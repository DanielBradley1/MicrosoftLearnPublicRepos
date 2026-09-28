<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-awaitedworkflowprocessingresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# awaitedWorkflowProcessingResult resource type

Namespace: microsoft.graph.identityGovernance

Represents the result of a workflow execution that waits for completion. This type is returned by the [activateAndWait](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activateandwait?view=graph-rest-1.0) action on the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | The processing status of the workflow execution. |
| statusReasons | String collection | A collection of reasons for the current processing status. May be empty. |
| subject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The subject that was processed by the workflow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.awaitedWorkflowProcessingResult",
  "processingStatus": "String",
  "statusReasons": [
    "String"
  ],
  "subject": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSubject"
  }
}
```
