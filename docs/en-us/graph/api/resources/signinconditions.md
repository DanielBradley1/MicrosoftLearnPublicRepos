<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinconditions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# signInConditions resource type

Namespace: microsoft.graph

Represents sign-in parameters of the authenticating identity as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationFlow | [authenticationFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationflow?view=graph-rest-1.0) | Type of authentication flow. The possible value is: `deviceCodeFlow` or `authenticationTransfer`. Default value is `none`. |
| clientAppType | conditionalAccessClientApp | Client application type. The possible value is: `all`, `browser`, `mobileAppsAndDesktopClients`, `exchangeActiveSync`, `easSupported`, `other`, `unknownFutureValue`. Default value is `all`. |
| country | String | Country from where the identity is authenticating. |
| deviceInfo | [deviceInfo](https://learn.microsoft.com/en-us/graph/api/resources/deviceinfo?view=graph-rest-1.0) | Information about the device used for the sign-in. |
| devicePlatform | conditionalAccessDevicePlatform | Device platform. The possible value is: `android`, `iOS`, `windows`, `windowsPhone`, `macOS`, `all`, `unknownFutureValue`, `linux`. Default value is `all`. |
| insiderRiskLevel | insiderRiskLevel | Insider risk associated with the authenticating user. The possible value is: `none`, `minor`, `moderate`, `elevated`, `unknownFutureValue`. Default value is `none`. |
| ipAddress | String | Ip address of the authenticating identity. |
| servicePrincipalRiskLevel | riskLevel | Risk associated with the service principal. The possible value is: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Default value is `none`. |
| signInRiskLevel | riskLevel | Sign-in risk associated with the user. The possible value is: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Default value is `none`. |
| userRiskLevel | riskLevel | The authenticating user's risk level. The possible value is: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Default value is `none`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInConditions",
  "signInRiskLevel": "String",
  "userRiskLevel": "String",
  "servicePrincipalRiskLevel": "String",
  "country": "String",
  "ipAddress": "String",
  "clientAppType": "String",
  "devicePlatform": "String",
  "deviceInfo": {
    "@odata.type": "microsoft.graph.deviceInfo"
  },
  "insiderRiskLevel": "String",
  "authenticationFlow": {
    "@odata.type": "microsoft.graph.authenticationFlow"
  }
}
```
