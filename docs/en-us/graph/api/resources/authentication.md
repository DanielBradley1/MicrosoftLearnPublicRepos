<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authentication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-28 -->

# authentication resource type

Namespace: microsoft.graph

Exposes authentication method states for users and relationships that represent the authentication methods supported by Microsoft Entra ID.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| emailMethods | [emailAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethod?view=graph-rest-1.0) collection | The email address registered to a user for authentication. |
| externalAuthenticationMethods | [externalAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethod?view=graph-rest-1.0) collection | Represents the external MFA registered to a user for authentication using an external identity provider. |
| fido2Methods | [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0) collection | Represents the FIDO2 security keys registered to a user for authentication. |
| methods | [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) collection | Represents all authentication methods registered to a user. |
| microsoftAuthenticatorMethods | [microsoftAuthenticatorAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethod?view=graph-rest-1.0) collection | The details of the Microsoft Authenticator app registered to a user for authentication. |
| operations | [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0) collection | Represents the status of a long-running operation, such as a password reset operation. |
| passwordMethods | [passwordAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/passwordauthenticationmethod?view=graph-rest-1.0) collection | Represents the password registered to a user for authentication. For security, the password itself is never returned in the object, but action can be taken to reset a password. |
| platformCredentialMethods | [platformCredentialAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/platformcredentialauthenticationmethod?view=graph-rest-1.0) collection | Represents a platform credential instance registered to a user on Mac OS. |
| phoneMethods | [phoneAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/phoneauthenticationmethod?view=graph-rest-1.0) collection | The phone numbers registered to a user for authentication. |
| softwareOathMethods | [softwareOathAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethod?view=graph-rest-1.0) collection | The software OATH time-based one-time password \(TOTP\) applications registered to a user for authentication. |
| temporaryAccessPassMethods | [temporaryAccessPassAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0) collection | Represents a Temporary Access Pass registered to a user for authentication through time-limited passcodes. |
| windowsHelloForBusinessMethods | [windowsHelloForBusinessAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/windowshelloforbusinessauthenticationmethod?view=graph-rest-1.0) collection | Represents the Windows Hello for Business authentication method registered to a user for authentication. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authentication"
}
```
