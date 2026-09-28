<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorfeaturesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# microsoftAuthenticatorFeatureSettings resource type

Namespace: microsoft.graph

Represents Microsoft Authenticator settings such as application context and location context, and whether they're enabled for all users or specific users only.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayAppInformationRequiredState | [authenticationMethodFeatureConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodfeatureconfiguration?view=graph-rest-1.0) | Determines whether the user's Authenticator app shows them the client app they're signing into. |
| displayLocationInformationRequiredState | [authenticationMethodFeatureConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodfeatureconfiguration?view=graph-rest-1.0) | Determines whether the user's Authenticator app shows them the geographic location of where the authentication request originated from. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAuthenticatorFeatureSettings",
  "displayAppInformationRequiredState": {
    "@odata.type": "microsoft.graph.authenticationMethodFeatureConfiguration"
  },
  "displayLocationInformationRequiredState": {
    "@odata.type": "microsoft.graph.authenticationMethodFeatureConfiguration"
  }
}
```
