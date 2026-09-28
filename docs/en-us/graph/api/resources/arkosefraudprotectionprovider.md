<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/arkosefraudprotectionprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# arkoseFraudProtectionProvider resource type

Namespace: microsoft.graph

Used to configure fraud protection using Arkose Labs that integrates with Microsoft Entra External ID to help protect against fraudulent activities during user registration \(sign-up\) events.

Inherits from [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientSubDomain | String | Used to invoke the Arkose service from the client application. Request from your Arkose Customer Success Manager or use the default `client-api` value. |
| displayName | String | The display name of this Arkose fraud protection provider configuration. Inherited from [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0). |
| id | String | The unique identifier for this Arkose fraud protection provider configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| privateKey | String | The private key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. |
| publicKey | String | The public key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. |
| verifySubDomain | String | Used to invoke the Arkose service from the Microsoft authentication server. Request from your Arkose Customer Success Manager or use the default `verify-api` value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "publicKey": "String",
  "privateKey": "String",
  "clientSubDomain": "String",
  "verifySubDomain": "String"
}
```
