<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerFieldRules resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the rules and permissions that apply to a property as part of a [plannerTaskPropertyRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpropertyrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultRules | String collection | The default rules that apply if no override matches to the current data. |
| overrides | [plannerRuleOverride](https://learn.microsoft.com/en-us/graph/api/resources/plannerruleoverride?view=graph-rest-beta) collection | Overrides that specify different rules for specific data associated with the field. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerFieldRules",
  "defaultRules": ["String"],
  "overrides": [{"@odata.type": "microsoft.graph.plannerRuleOverride"}]
}
```
