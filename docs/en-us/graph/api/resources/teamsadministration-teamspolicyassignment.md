<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# teamsPolicyAssignment resource type

Namespace: microsoft.graph.teamsAdministration

Represents the root entity for managing Teams policy assignments. It provides access to user policy assignments and supports the resolution of policy IDs.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get policy ID](https://learn.microsoft.com/en-us/graph/api/teamsadministration-teamspolicyassignment-getpolicyid?view=graph-rest-1.0) | [microsoft.graph.teamsAdministration.policyIdentifierDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-policyidentifierdetail?view=graph-rest-1.0) collection | Get the [policy ID](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-policyidentifierdetail?view=graph-rest-1.0) for a given policy name and policy type within Teams administration. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userAssignments | [microsoft.graph.teamsAdministration.teamsPolicyUserAssignment](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-teamspolicyuserassignment?view=graph-rest-1.0) collection | The collection of user policy assignments. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.teamsPolicyAssignment"
}
```
