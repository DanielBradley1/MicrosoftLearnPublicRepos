<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activategroupscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# activateGroupScope resource type

Namespace: microsoft.graph.identityGovernance

Represents activating a group scope for a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) of a workflow.

Inherits from [microsoft.graph.identityGovernance.activationScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activationscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | The group scope of the workflow being run. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.activateGroupScope"
}
```
