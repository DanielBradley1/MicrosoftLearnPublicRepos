<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerrelationshipbasedusertype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerRelationshipBasedUserType resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a role based on the caller's relationship to the [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) that a [plannerTaskRoleBasedRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrolebasedrule?view=graph-rest-beta) can be applied to.

Inherits from [plannerTaskConfigurationRoleBase](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfigurationrolebase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| role | plannerRelationshipUserRoles | Identifies the relationship of the caller to the task. The possible values are: `defaultRules`, `groupOwners`, `groupMembers`, `taskAssignees`, `applications`, `unknownFutureValue`. |
| roleKind | plannerUserRoleKind | The kind of the rule. The value must be `relationship`. The possible values are: `relationship`, `unknownFutureValue`. Inherited from [plannerTaskConfigurationRoleBase](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfigurationrolebase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerRelationshipBasedUserType",
  "role": "String",
  "roleKind": "String"
}
```
