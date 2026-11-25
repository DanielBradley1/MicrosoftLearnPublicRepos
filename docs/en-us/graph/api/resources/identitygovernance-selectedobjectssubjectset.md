<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-selectedobjectssubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# selectedObjectsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Represents a scope that includes only the selected directory objects. This type is used in the **scope** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) to target specific objects for policy evaluation.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| inScopeObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The directory objects that are included in the policy scope. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.selectedObjectsSubjectSet"
}
```
