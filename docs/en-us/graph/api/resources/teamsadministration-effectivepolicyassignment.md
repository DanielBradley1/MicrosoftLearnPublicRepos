<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-effectivepolicyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# effectivePolicyAssignment resource type

Namespace: microsoft.graph.teamsAdministration

Represents the effective policies associated with a user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| policyAssignment | [microsoft.graph.teamsAdministration.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-policyassignment?view=graph-rest-1.0) | Represents details about the policy instance, including **assignmentType**, **displayName**, **groupId**, and **policyID**. |
| policyType | String | The type of the assigned policy; for example, `TeamsMeetingPolicy` and `TeamsCallingPolicy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.effectivePolicyAssignment",
  "policyAssignment": {"@odata.type": "microsoft.graph.teamsAdministration.policyAssignment"},
  "policyType": "String"
}
```
