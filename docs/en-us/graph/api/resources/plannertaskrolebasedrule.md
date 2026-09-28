<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrolebasedrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerTaskRoleBasedRule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the rules for editing [tasks](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) created for a [scenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultRule | String | Default rule that applies when a property or action-specific rule is not provided. The possible values are: `Allow`, `Block` |
| propertyRule | [plannerTaskPropertyRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpropertyrule?view=graph-rest-beta) | Rules for specific properties and actions. |
| role | [plannerTaskConfigurationRoleBase](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfigurationrolebase?view=graph-rest-beta) | The role these rules apply to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskRoleBasedRule",
  "defaultRule": "String",
  "propertyRule": {"@odata.type": "microsoft.graph.plannerTaskPropertyRule"},
  "role": {"@odata.type": "microsoft.graph.plannerTaskConfigurationRoleBase"}
}
```
