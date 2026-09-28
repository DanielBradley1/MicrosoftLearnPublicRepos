<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrulesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallRuleSettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration settings for a [cloud firewall rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta), including the enabled or disabled status.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | microsoft.graph.networkaccess.securityRuleStatus | The status of the rule. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRuleSettings",
  "status": "String"
}
```
