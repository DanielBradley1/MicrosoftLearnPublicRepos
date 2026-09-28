<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# fraudProtectionProvider resource type

Namespace: microsoft.graph

Represents the configuration details for a third-party fraud protection provider that integrates with Microsoft Entra External ID to help protect against fraudulent activities during authentication events. This is an abstract type that serves as the base resource for specific provider implementations. The following derived types are currently supported.

- [arkoseFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/arkosefraudprotectionprovider?view=graph-rest-1.0) resource type
- [humanSecurityFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/humansecurityfraudprotectionprovider?view=graph-rest-1.0) resource type

For more information, see [Integrate Microsoft Entra External ID with Arkose Labs and HUMAN Security for fraud protection \(preview\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-integrate-fraud-protection).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-list-fraudprotectionproviders?view=graph-rest-1.0) | [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) collection | Get a list of the fraudProtectionProviders and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-post-fraudprotectionproviders?view=graph-rest-1.0) | [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) | Create a new fraudProtectionProvider object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/fraudprotectionprovider-get?view=graph-rest-1.0) | [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) | Read the properties and relationships of [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/fraudprotectionprovider-update?view=graph-rest-1.0) | None | Update the properties of a fraudProtectionProvider object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-delete-fraudprotectionproviders?view=graph-rest-1.0) | None | Delete a fraudProtectionProvider object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the fraud protection provider configuration. |
| id | String | The unique identifier for the fraud protection provider configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fraudProtectionProvider",
  "id": "String (identifier)",
  "displayName": "String"
}
```
