<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# plannerTaskPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the policy configuration for [tasks](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) created for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) when they're being changed outside of the scenario.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rules | [plannerTaskRoleBasedRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrolebasedrule?view=graph-rest-beta) collection | The rules that should be enforced on the tasks when they're being changed outside of the scenario, based on the role of the caller. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskPolicy",
  "rules": [{"@odata.type": "microsoft.graph.plannerTaskRoleBasedRule"}]
}
```
