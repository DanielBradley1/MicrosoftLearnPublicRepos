<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrulesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringRuleSettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings that control how a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) is enforced.

This type is used by the **settings** property of [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | [microsoft.graph.networkaccess.securityRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#securityrulestatus-values) | The enforcement status of the rule. The possible values are: `enabled`, `disabled`, `reportOnly`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringRuleSettings",
  "status": "String"
}
```
