<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallPolicySettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration settings for a [cloud firewall policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta), including the default action to apply when no matching rules are found.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultAction | microsoft.graph.networkaccess.cloudFirewallAction | The default action applied when no matching rules are found. The possible values are: `allow`, `block`, `unknownFutureValue`. Only `allow` is currently supported. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicySettings",
  "defaultAction": "String"
}
```
