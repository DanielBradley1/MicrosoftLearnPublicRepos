<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# webApplicationFirewallVerificationModel resource type

Namespace: microsoft.graph

Represents a verification operation and result for a domain managed by a [web application firewall \(WAF\) provider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-list-webapplicationfirewallverifications?view=graph-rest-1.0) | [webApplicationFirewallVerificationModel](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) collection | Get a list of the webApplicationFirewallVerificationModel objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/webapplicationfirewallverificationmodel-get?view=graph-rest-1.0) | [webApplicationFirewallVerificationModel](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) | Read the properties and relationships of [webApplicationFirewallVerificationModel](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-delete-webapplicationfirewallverifications?view=graph-rest-1.0) | None | Delete a webApplicationFirewallVerificationModel object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the verification model. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| providerType | webApplicationFirewallProviderType | Specifies the type of WAF provider used for the verification. The possible values are: `akamai`, `cloudflare`, `unknownFutureValue`. |
| verificationResult | [webApplicationFirewallVerificationResult](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationresult?view=graph-rest-1.0) | An object describing the outcome of the verification operation, including status, errors or warnings |
| verifiedDetails | [webApplicationFirewallVerifiedDetails](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverifieddetails?view=graph-rest-1.0) | Details of DNS configuration |
| verifiedHost | String | The host \(domain or subdomain\) that was verified as part of this verification operation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| provider | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) | Reference to a provider resource associated with this verification model. Represents a WAF provider that can be used to verify or manage the host. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webApplicationFirewallVerificationModel",
  "id": "String (identifier)",
  "verifiedHost": "String",
  "providerType": "String",
  "verificationResult": {
    "@odata.type": "microsoft.graph.webApplicationFirewallVerificationResult"
  },
  "verifiedDetails": {
    "@odata.type": "microsoft.graph.webApplicationFirewallVerifiedDetails"
  }
}
```
