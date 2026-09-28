<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/humansecurityfraudprotectionprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# humanSecurityFraudProtectionProvider resource type

Namespace: microsoft.graph

Used to configure fraud protection using HUMAN Security that integrates with Microsoft Entra External ID to help protect against fraudulent activities during user registration \(sign-up\) events.

Inherits from [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Unique identifier for an individual application. You can retrieve this from the HUMAN Security Admin Console or request it from your HUMAN Security Customer Success Manager. |
| displayName | String | The display name of this HUMAN Security fraud protection provider configuration. Inherited from [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0). |
| id | String | The unique identifier for this HUMAN Security fraud protection provider configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| serverToken | String | Unique identifier used to authenticate API calls between the Server side integration and the HUMAN platform. You can retrieve this from the HUMAN Security Admin Console or request it from your HUMAN Security Customer Success Manager. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.humanSecurityFraudProtectionProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "appId": "String",
  "serverToken": "String"
}
```
