<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-selectedobjectssubjectset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# selectedObjectsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a scope that includes only the selected directory objects. This type is used in the **scope** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) to target specific objects for policy evaluation.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| inScopeObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | The directory objects that are included in the policy scope. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.selectedObjectsSubjectSet"
}
```
