<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodtarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# voiceAuthenticationMethodTarget resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A collection of groups enabled to use voice call authentication via the [voice call authentication methods policy](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-beta) in Microsoft Entra ID. Inherits from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object ID of a Microsoft Entra group. |
| isRegistrationRequired | Boolean | Determines whether the user is enforced to register the authentication method. **Not supported**. |
| targetType | authenticationMethodTargetType | The possible values are: `group`, and `unknownFutureValue`. From December 2022, targeting individual users using `user` is no longer recommended. Existing targets remain but we recommend moving the individual users to a targeted group. Inherited from [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.voiceAuthenticationMethodTarget",
  "id": "String (identifier)",
  "targetType": "String",
  "isRegistrationRequired": "Boolean"
}
```
