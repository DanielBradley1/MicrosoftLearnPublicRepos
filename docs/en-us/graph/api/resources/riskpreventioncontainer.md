<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskpreventioncontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# riskPreventionContainer resource type

Namespace: microsoft.graph

Represents the entry point for risk prevention features in [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/external-identities-overview).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fraudProtectionProviders | [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) collection | Represents entry point for fraud protection provider configurations for Microsoft Entra External ID tenants. |
| webApplicationFirewallProviders | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider?view=graph-rest-1.0) collection | Collection of WAF provider configurations registered in the External ID tenant. |
| webApplicationFirewallVerifications | [webApplicationFirewallVerificationModel](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallverificationmodel?view=graph-rest-1.0) collection | Collection of verification operations performed for domains or hosts with WAF providers registered in the External ID tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskPreventionContainer"
}
```
