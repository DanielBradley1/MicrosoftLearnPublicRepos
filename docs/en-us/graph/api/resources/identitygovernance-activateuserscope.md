<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activateuserscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# activateUserScope resource type

Namespace: microsoft.graph.identityGovernance

Represents activating a user scope for a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) of a workflow.

Inherits from [microsoft.graph.identityGovernance.activationScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activationscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| users | [microsoft.graph.user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The user scope for the workflow run. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.activateUserScope"
}
```
