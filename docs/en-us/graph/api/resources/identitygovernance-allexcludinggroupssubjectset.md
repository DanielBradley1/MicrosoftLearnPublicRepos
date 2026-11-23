<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludinggroupssubjectset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# allExcludingGroupsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a scope that includes all identities except members of the excluded groups. This type is used in the **scope** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) to exclude specific groups from policy evaluation.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| excludedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | The groups whose members are excluded from the policy scope. A maximum of 10 excluded groups are allowed per policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.allExcludingGroupsSubjectSet"
}
```
