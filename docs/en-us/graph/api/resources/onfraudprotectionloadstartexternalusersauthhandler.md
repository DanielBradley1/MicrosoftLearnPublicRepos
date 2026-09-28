<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartexternalusersauthhandler?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# onFraudProtectionLoadStartExternalUsersAuthHandler resource type

Namespace: microsoft.graph

A managed handler that defines what third-party fraud protection is enabled or disabled in an external identities user flow for Microsoft Entra External ID tenants.

Inherits from [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| signUp | [fraudProtectionConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionconfiguration?view=graph-rest-1.0) | Specifies the fraud protection configuration for sign-up events. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
  "signUp": {
    "@odata.type": "microsoft.graph.fraudProtectionConfiguration"
  }
}
```
