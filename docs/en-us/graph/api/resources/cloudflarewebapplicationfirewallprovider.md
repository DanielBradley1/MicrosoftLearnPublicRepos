<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudflarewebapplicationfirewallprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# cloudFlareWebApplicationFirewallProvider resource type

Namespace: microsoft.graph

Represents a Cloudflare web application firewall \(WAF\) provider configuration integrated with Entra External ID.

Inherits from [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiToken | String | Cloudflare API token or credential used by Microsoft services to authenticate to the Cloudflare account. Contact your Cloudflare Customer Success Manager for assistance with your apitoken. |
| displayName | String | The friendly display name of the Cloudflare provider configuration. Inherited from [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0). |
| id | String | Unique identifier for the provider resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| zoneId | String | Default Cloudflare Zone ID associated with this provider configuration. This ID identifies the DNS zone in Cloudflare that is commonly used for verification and configuration operations for the provider. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "apiToken": "String",
  "zoneId": "String"
}
```
