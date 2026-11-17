<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflowscontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecycleWorkflowsContainer resource type

Namespace: microsoft.graph.identityGovernance

A container for the relationships that expose the Microsoft Entra ID Governance Lifecycle Workflows API capabilities. This object is configured in the **lifecycleWorkflows** relationship of the [identityGovernance](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance?view=graph-rest-1.0) resource.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List lifecycle policies](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | Get lifecycle policies in the tenant. |
| [Create lifecycle policy](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | Create a lifecycle policy of a concrete derived type. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier used for individually addressing the lifecycle workflows objects. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customTaskExtensions | [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) collection | The **customTaskExtension** instance. |
| deletedItems | [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteditemcontainer?view=graph-rest-1.0) | Deleted workflows and lifecycle policies in your lifecycle workflows instance. |
| insights | [microsoft.graph.identityGovernance.insights](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-insights?view=graph-rest-1.0) | The insight container holding workflow insight summaries for a tenant. |
| lifecyclePolicies | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | The lifecycle policies for guest users and agent identities. |
| lifecyclePolicyPriorityConfigurations | [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) collection | The ordered lifecycle policy identifiers for each subject type. |
| settings | [microsoft.graph.identityGovernance.lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) | The settings of the lifecycle workflows instance. |
| taskDefinitions | [microsoft.graph.identityGovernance.taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) collection | The definition of tasks within the lifecycle workflows instance. |
| workflows | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | The workflows in the lifecycle workflows instance. |
| workflowTemplates | [microsoft.graph.identityGovernance.workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) collection | The workflow templates in the lifecycle workflow instance. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecycleWorkflowsContainer",
  "id": "String (identifier)"
}
```
