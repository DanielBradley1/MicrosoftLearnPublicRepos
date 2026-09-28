<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-policyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# policyAssignment resource type

Namespace: microsoft.graph.teamsAdministration

Represents the details of a policy instance, such as **displayName** and **groupId**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentType | microsoft.graph.teamsAdministration.assignmentType | The type of assignment: `group` for group-based assignment, `direct` for user-based assignment. The possible values are: `direct`, `group`, `unknownFutureValue`. |
| displayName | String | Represents the name of the policy. |
| groupId | String | Represents the group identifier. |
| policyId | String | Represents the unique identifier for the policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.policyAssignment",
  "assignmentType": "String",
  "displayName": "String",
  "groupId": "String",
  "policyId": "String"
}
```
