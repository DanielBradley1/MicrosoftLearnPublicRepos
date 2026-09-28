<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/akamaiwebapplicationfirewallprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# akamaiWebApplicationFirewallProvider resource type

Namespace: microsoft.graph

Represents an Akamai web application firewall \(WAF\) provider configuration integrated with Entra External ID.

Inherits from [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessToken | String | Akamai API access token used to authenticate to the Akamai account. Contact your Akamai Customer Success Manager for assistance with your accessToken. |
| clientSecret | String | Akamai API client secret used in conjunction with the client token and access token for authentication. Contact your Akamai Customer Success Manager for assistance with this information. |
| clientToken | String | Akamai API client token used for authentication to the Akamai account. Contact your Akamai Customer Success Manager for assistance with this information. |
| displayName | String | The friendly display name of the Akamai provider configuration. Inherited from [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0). |
| hostPrefix | String | Prefix used to identify the host or domain in Akamai configuration operations. This value may be required for certain API calls or configuration scenarios. |
| id | String | Unique identifier for the provider resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.akamaiWebApplicationFirewallProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "hostPrefix": "String",
  "clientSecret": "String",
  "clientToken": "String",
  "accessToken": "String"
}
```
