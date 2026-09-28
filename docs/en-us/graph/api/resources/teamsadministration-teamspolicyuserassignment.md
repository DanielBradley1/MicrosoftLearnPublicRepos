<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# teamsPolicyUserAssignment resource type

Namespace: microsoft.graph.teamsAdministration

Represents a [teamsPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyassignment?view=graph-rest-1.0) object used to assign or unassign a policy for a specific user. It includes the user's ID, the type of policy \(for example, `teamsMeetingBroadcastPolicy`\), and the targeted policy ID.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Assign](https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamspolicyuserassignment-assign?view=graph-rest-1.0) | None | Assign a Teams [policy](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0) to a user using the user ID, policy type, and policy ID. |
| [Unassign](https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamspolicyuserassignment-unassign?view=graph-rest-1.0) | None | Unassign a Teams [policy](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0) from a user using the user ID and policy type. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| policyId | String | The unique identifier \(GUID\) of the policy within the specified policy type. |
| policyType | String | The type of Teams policy assigned or unassigned, such as `teamsMeetingBroadcastPolicy`. |
| userId | String | The unique identifier \(GUID\) of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.teamsPolicyUserAssignment",
  "policyId": "String",
  "policyType": "String",
  "userId": "String"
}
```
