<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# authenticationMethod resource type

Namespace: microsoft.graph

An abstract type that represents an authentication method registered to a user. An [authentication method](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-methods) is something used by a user to authenticate or otherwise prove their identity to the system. Some examples include password, phone \(usable via SMS or voice call\), FIDO2 security keys, and more.

The **authenticationMethod** resource type is an abstract type that's inherited by the following derived types:

- [emailAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0)
- [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0)
- [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0)
- [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0)
- [passwordAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordauthenticationmethod?view=graph-rest-1.0)
- [phoneAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/phoneauthenticationmethod?view=graph-rest-1.0)
- [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0)
- [qrCodePinAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethod?view=graph-rest-1.0)
- [softwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethod?view=graph-rest-1.0)
- [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0)
- [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0)

Important

Listing users' authentication methods only returns methods supported on this API version and registered to the user. See [Microsoft Entra authentication methods API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0) for a list of currently supported methods.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authentication-list-methods?view=graph-rest-1.0) | [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) collection | Read the properties and relationships of all of a user's **authenticationMethod** objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Represents the date and time when an entity was created. Read-only. |
| id | String | The identifier of this instance of an authentication method registered to this user. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethod",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)"
}
```
