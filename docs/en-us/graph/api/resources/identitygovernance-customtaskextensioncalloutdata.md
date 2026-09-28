<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncalloutdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# customTaskExtensionCalloutData resource type

Namespace: microsoft.graph.identityGovernance

Represents the data sent to Azure Logic Apps as part of a [customExtensionCalloutRequest](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutrequest?view=graph-rest-1.0). This object is configured in the **data** property of that resource for the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource.

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| targetSubject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The target subject for workflow execution. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subject | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user that the `workflow` is executed for. |
| task | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | The task that references the custom extension making this callout. |
| taskProcessingResult | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) | The `taskProcessingResult` tracking the instance information of the executing `task`. |
| workflow | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | The `workflow` associated with the task that references the custom extension that will be making the callout. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionCalloutData",
  "targetSubject": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSubject"
  }
}
```
