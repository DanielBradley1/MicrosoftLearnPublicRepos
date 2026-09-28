<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfigurationrolebase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerTaskConfigurationRoleBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a role that a [plannerTaskRoleBasedRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrolebasedrule?view=graph-rest-beta) can be applied to.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| roleKind | plannerUserRoleKind | Type of the role. The possible values are: `relationship`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskConfigurationRoleBase",
  "roleKind": "String"
}
```
