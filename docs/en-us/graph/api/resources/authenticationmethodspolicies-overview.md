<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicies-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# Microsoft Entra authentication methods policies API overview

Namespace: microsoft.graph

Authentication methods policies define [authentication methods](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0) and the users that are allowed to use them to sign in and perform multifactor authentication \(MFA\) in Microsoft Entra ID. Authentication methods policies that can be managed in Microsoft Graph include FIDO2 Security Keys and Passwordless Phone Sign-in with Microsoft Authenticator app.

The authentication method policies APIs are used to manage policy settings. For example:

- Define the types of FIDO2 security keys that can be used in the Microsoft Entra tenant.
- Define the users or groups of users who are allowed to use FIDO2 Security Keys or Passwordless Phone Sign-in to sign in to Microsoft Entra ID.
- Define the users or groups of users who should be reminded to set up the Microsoft Authenticator for MFA using push notifications.

Note

Requests to the authentication methods policies APIs time-out after 60 seconds.

## What authentication methods policies can be managed in Microsoft Graph?

| Authentication method policy | Description |
| :--- | :--- |
| [emailauthenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/emailauthenticationmethodconfiguration?view=graph-rest-1.0) | Define users who can use email OTP on the Microsoft Entra tenant. |
| [externalauthenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) | Define users who can use an external MFA to satisfy the second factor of Microsoft Entra ID multifactor authentication requirements. |
| [fido2authenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0) | Define FIDO2 security key restrictions and users who can use them to sign in to Microsoft Entra ID. |
| [microsoftauthenticatorauthenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0) | Define users who can use Microsoft Authenticator on the Microsoft Entra tenant. |
| [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) | Define users who can use QRCodePin to sign in to Microsoft Entra ID. |
| [smsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0) | Defines users who can use Text Message on the Microsoft Entra tenant. |
| [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0) | Defines users who can use a third-party software OATH authentication method. |
| [temporaryaccesspassauthenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0) | Defines users who can use Temporary Access Pass to sign in to Microsoft Entra ID. |
| [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) | Defines users or groups that are enabled to use the voice call authentication method. |
| [x509CertificateAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0) | Defines users who can use X.509 certificate to sign in to Microsoft Entra ID. |

## Policies available for authentication methods registration campaign

| Policy | Description |
| :--- | :--- |
| [authenticationMethodsRegistrationCampaign](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsregistrationcampaign?view=graph-rest-1.0) | Define users who should be reminded to set up an authentication method \(currently only supported for the Microsoft Authenticator\). |

## Next step

- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
