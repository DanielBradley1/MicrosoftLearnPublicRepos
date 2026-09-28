<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/strongauthenticationrequirements?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-11 -->

# strongAuthenticationRequirements resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Captures settings relating to per-user Microsoft Entra multifactor authentication.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| perUserMfaState | perUserMfaState | Sets the per-user MFA state for the user. The possible values are: `disabled`, `enforced`, `enabled`, `unknownFutureValue`. When you update a user's MFA state to `enabled` and the user has already registered an MFA method, their state changes automatically to `enforced`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.strongAuthenticationRequirements",
  "perUserMfaState": "String"
}
```
