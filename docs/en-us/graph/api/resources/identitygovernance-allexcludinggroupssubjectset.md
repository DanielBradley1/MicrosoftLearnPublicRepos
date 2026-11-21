<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludinggroupssubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# allExcludingGroupsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Represents a scope that includes all identities except members of the excluded groups. This type is used in the **scope** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) to exclude specific groups from policy evaluation.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| excludedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | The groups whose members are excluded from the policy scope. A maximum of 10 excluded groups are allowed per policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.allExcludingGroupsSubjectSet"
}
```
