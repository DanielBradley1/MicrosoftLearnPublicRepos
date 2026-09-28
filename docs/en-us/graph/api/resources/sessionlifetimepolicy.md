<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sessionlifetimepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# sessionlifetimepolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the session lifetime policies Microsoft Entra ID applied to a sign-in event. This object is configured in the **sessionLifetimePolicies** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

For more details about session management with conditional access in Microsoft Entra ID, see the [conditional access session management documentation](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationRequirement | expirationRequirement | If a conditional access session management policy required the user to authenticate in this sign-in event, this field describes the policy type that required authentication. The possible values are: `rememberMultifactorAuthenticationOnTrustedDevices`, `tenantTokenLifetimePolicy`, `audienceTokenLifetimePolicy`, `signInFrequencyPeriodicReauthentication`, `ngcMfa`, `signInFrequencyEveryTime`, `unknownFutureValue`. |
| detail | String | The human-readable details of the conditional access session management policy applied to the sign-in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sessionLifetimePolicy",
  "expirationRequirement": "String",
  "detail": "String"
}
```
