<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# printTaskDefinition resource type

Namespace: microsoft.graph

Represents an abstract definition for a task that can be triggered when various events occur within Universal Print.

For details about how to use this resource to add pull printing support to Universal Print, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

This resource supports:

- [Subscribing to change notifications](https://learn.microsoft.com/en-us/graph/universal-print-webhook-notifications).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/print-list-taskdefinitions?view=graph-rest-1.0) | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) collection | Get a complete list of printTaskDefinitions created within Universal Print. |
| [Create](https://learn.microsoft.com/en-us/graph/api/print-post-taskdefinitions?view=graph-rest-1.0) | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Create a new printTaskDefinition. |
| [Update](https://learn.microsoft.com/en-us/graph/api/print-update-taskdefinition?view=graph-rest-1.0) | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Update a printTaskDefinition. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/print-delete-taskdefinition?view=graph-rest-1.0) | None | Delete a printTaskDefinition. |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/printtaskdefinition-list-tasks?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Get a list of tasks that have been created based on this definition. The list includes currently running tasks and recently completed tasks. |
| [Get task](https://learn.microsoft.com/en-us/graph/api/printtask-get?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Gets a task that has been created based on this definition. |
| [Update task](https://learn.microsoft.com/en-us/graph/api/printtaskdefinition-update-task?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Update a task that has been created based on this definition. **Applications that register task triggers are responsible for updating task status when processing is finished, unless the related printJob has been redirected to another printer.** Failure to report completion will result in the related print job being blocked from printing and eventually deleted. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [appIdentity](https://learn.microsoft.com/en-us/graph/api/resources/appidentity?view=graph-rest-1.0) | The application that created the printTaskDefinition. Read-only. |
| displayName | String | The name of the printTaskDefinition. |
| id | String | The printTaskDefinition's identifier. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tasks | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) collection | A list of tasks that have been created based on this definition. The list includes currently running tasks and recently completed tasks. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printTaskDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.appIdentity"
  }
}
```
