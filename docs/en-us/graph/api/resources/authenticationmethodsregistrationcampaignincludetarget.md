<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsregistrationcampaignincludetarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# authenticationMethodsRegistrationCampaignIncludeTarget resource type

Namespace: microsoft.graph

Represents the users and groups that are targeted for [authentication method registration campaigns](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsregistrationcampaign?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The object identifier of a Microsoft Entra user or group. |
| targetedAuthenticationMethod | String | The authentication method that the user is prompted to register. The value can be `Fido2` or `microsoftAuthenticator`. |
| targetType | authenticationMethodTargetType | The type of the authentication method target. The possible values are: `user`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodsRegistrationCampaignIncludeTarget",
  "id": "String (identifier)",
  "targetedAuthenticationMethod": "String",
  "targetType": "String"
}
```
