<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/telecomprovidersettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-31 -->

# telecomProviderSettings resource type

Namespace: microsoft.graph

Represents configuration for routing SMS and voice authentication traffic through a telecom provider integration. This complex type is used by the **telecomProviderSettings** property of the [smsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0) and [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | Guid | The application \(client\) ID used to authenticate to the telecom provider. |
| isEvaluationModeEnabled | Boolean | `true` to run the telecom provider integration in evaluation \(nonenforcing\) mode; otherwise, `false`. |
| migrationPercentage | Int32 | The percentage of authentication traffic routed to the telecom provider. Valid values range from 0 through 100. |
| url | String | The endpoint URL of the telecom provider integration. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.telecomProviderSettings",
  "url": "String",
  "appId": "Guid",
  "isEvaluationModeEnabled": "Boolean",
  "migrationPercentage": "Integer"
}
```
