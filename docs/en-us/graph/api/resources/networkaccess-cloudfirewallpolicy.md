<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cloud firewall policy for Microsoft Global Secure Access that provides Layer 3 \(Network\) protection by monitoring and controlling all network traffic. A cloud firewall policy takes effect once the admin associates it with the desired filtering profile. For more information, see [Configure Global Secure Access cloud firewall \(preview\)](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-cloud-firewall).

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-cloudfirewallpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) collection | Get a list of the cloudFirewallPolicy objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-cloudfirewallpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) | Create a new cloudFirewallPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) | Read the properties and relationships of a cloudFirewallPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-update?view=graph-rest-beta) | None | Update the properties of a cloudFirewallPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-delete?view=graph-rest-beta) | None | Delete a cloudFirewallPolicy object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Optional. |
| id | String | A unique identifier for the policy. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Key. Not nullable. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. Read-only. |
| name | String | A unique display name for the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Required. |
| settings | [microsoft.graph.networkaccess.cloudFirewallPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicysettings?view=graph-rest-beta) | Configuration settings for the cloud firewall policy, including the default action. Required. |
| version | String | The version of the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) collection | The rules that define specific firewall behaviors within this policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.cloudFirewallPolicySettings"
  }
}
```
