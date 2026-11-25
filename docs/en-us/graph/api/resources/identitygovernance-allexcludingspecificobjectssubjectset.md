<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludingspecificobjectssubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# allExcludingSpecificObjectsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Represents a scope that includes all identities except the excluded directory objects. This type is used in the **scope** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) to exclude specific objects from policy evaluation.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| excludedObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The directory objects that are excluded from the policy scope. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.allExcludingSpecificObjectsSubjectSet"
}
```
