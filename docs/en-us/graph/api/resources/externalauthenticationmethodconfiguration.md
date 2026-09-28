<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# externalAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Specifies the properties and connection information for an external MFA.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of an [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externalauthenticationmethodconfiguration-update?view=graph-rest-1.0) | [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) | Update the properties of an [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Delete an [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | **appId** for the app registration in Microsoft Entra ID representing the integration with the external provider. |
| displayName | String | Display name for the external MFA. This name is shown to users during sign-in. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users excluded from the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |
| id | String | The unique identifier for this object. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| openIdConnectSetting | [openIdConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/openidconnectsetting?view=graph-rest-1.0) | Open ID Connection settings used by this external MFA. |
| state | authenticationMethodState | The state of the method in the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use an authentication method as part of an authentication method policy in Microsoft Entra ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "displayName": "String",
  "appId": "String",
  "openIdConnectSetting": {
    "@odata.type": "microsoft.graph.openIdConnectSetting"
  }
}
```
