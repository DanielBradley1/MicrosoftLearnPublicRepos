<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinpreferences?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-18 -->

# signInPreferences resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings and preferences for the sign-in experience of a user. Currently, only system-preferred MFA settings are available. For more information, see [System-preferred multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-system-preferred-multifactor-authentication).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSystemPreferredAuthenticationMethodEnabled | Boolean | Indicates whether the credential preferences of the system are enabled. |
| userPreferredMethodForSecondaryAuthentication | userDefaultAuthenticationMethodType | The default second-factor method used by the user when signing in. If a user is enabled for system-preferred authentication, then this value is ignored except for a few scenarios where a user is authenticating via NPS extension or ADFS adapter. Possible values are `push`, `oath`, `voiceMobile`, `voiceAlternateMobile`, `voiceOffice`, `sms`, and `unknownFutureValue` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInPreferences",
  "isSystemPreferredAuthenticationMethodEnabled": "Boolean",
  "userPreferredMethodForSecondaryAuthentication": "String"
}
```
