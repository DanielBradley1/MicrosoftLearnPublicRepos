<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-directoryobjectworkflowsubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# directoryObjectWorkflowSubject resource type

Namespace: microsoft.graph.identityGovernance

Represents a [directory object](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0), such as a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), as a subject for lifecycle workflow activation. Use this type when a lifecycle workflow processes an existing directory object; the **directoryObject** relationship returns the specific object being processed.

Inherits from [workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| directoryObject | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that's being processed by the lifecycle workflow. The runtime type is the specific derived type of the object, for example, [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.directoryObjectWorkflowSubject"
}
```
