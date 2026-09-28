<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerruleoverride?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerRuleOverride resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an overridden rule as part of [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the override. Allowed override values will be dependent on the property affected by the rule. |
| rules | String collection | Overridden rules. These are used as rules for the override instead of the default rules. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerRuleOverride",
  "name": "String",
  "rules": ["String"]
}
```
