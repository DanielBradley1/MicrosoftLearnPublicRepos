<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# webApplicationFirewallProvider resource type

Namespace: microsoft.graph

Represents the configuration of a web application firewall \(WAF\) provider in a Microsoft Entra External ID tenant. This abstract resource defines common properties for WAF providers integrated with Microsoft services.

This resource is an abstract type from which the following WAF provider resources derive:

- [akamaiWebApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/akamaiwebapplicationfirewallprovider?view=graph-rest-1.0)
- [cloudFlareWebApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/cloudflarewebapplicationfirewallprovider?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-list-webapplicationfirewallproviders?view=graph-rest-1.0) | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) collection | Get a list of the webApplicationFirewallProvider objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-post-webapplicationfirewallproviders?view=graph-rest-1.0) | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) | Create a new webApplicationFirewallProvider object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/webapplicationfirewallprovider-get?view=graph-rest-1.0) | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) | Read the properties and relationships of [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/webapplicationfirewallprovider-update?view=graph-rest-1.0) | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) | Update the properties of a webApplicationFirewallProvider object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-delete-webapplicationfirewallproviders?view=graph-rest-1.0) | None | Delete a webApplicationFirewallProvider object. |
| [Verify](https://learn.microsoft.com/en-us/graph/api/webapplicationfirewallprovider-verify?view=graph-rest-1.0) | [webApplicationFirewallVerificationModel](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) | Initiate a verification operation for the provider and return the verification result. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the WAF provider. |
| id | String | Unique identifier for the provider resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webApplicationFirewallProvider",
  "id": "String (identifier)",
  "displayName": "String"
}
```
