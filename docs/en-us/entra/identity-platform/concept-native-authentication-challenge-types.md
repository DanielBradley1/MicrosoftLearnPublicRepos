<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-challenge-types -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Native authentication challenge types and capabilities

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Native authentication supports two authentication flows:

- Email with one-time passcode \(OTP\)
- Email and password with support for self-service password reset \(SSPR\)

A client app that uses native authentication to sign in users can use either authentication flow. To make successful calls to the native authentication API, the app must declare which authentication flows and capabilities it supports. The native authentication API enables client apps to advertise their supported challenge types and capabilities using predefined values.

## Challenge types

Challenge types are predefined values that client apps include in their requests to declare which authentication flows they support to the native authentication API.

The following table contains the supported challenge type values:

| Challenge type | Description |
| --- | --- |
| *password* | This challenge type indicates that the app supports collecting a password credential from the user. |
| *oob* | This challenge type indicates that the application supports using one-time password or passcode \(OTP\) codes sent to the user using a secondary channel. Currently, the API supports only email and SMS OTP. |
| *redirect* | This challenge type indicates that the application supports falling back to the browser-delegated authentication, also known as web fallback. All native authentication compliant apps must support this capability. This requirement means that in every call the app makes to the native authentication API, it must include this challenge type. If the client app fails to include this challenge type, the request fails. |

New values are added when native authentication supports new authentication methods.

## Challenge type values for native authentication flows

The following table summarizes the challenge type values an app should use for various authentication flows:

|  | Sign-up flow | Sign-in flow | SSPR |
| --- | --- | --- | --- |
| **Email with password** | *oob*, *password*, and *redirect* | *oob*, *password*, and *redirect* | *oob* and *redirect* |
| **Email OTP** | *oob* and *redirect* | *oob* and *redirect* | Not applicable |

**Important notes:**

- Apps that use the [native authentication API](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api) directly must include the *redirect* challenge type when declaring their supported challenge types.
- Apps that use native authentication SDKs \(Android, iOS, or JavaScript\) don't need to include the *redirect* challenge type as the SDK automatically includes it.

## Capabilities

In addition to challenge types, client apps can specify a list of *capabilities*. While `challenge_type` defines which authentication methods the app supports, `capabilities` indicate which additional flows the client app can handle and what UI experiences it can provide to users.

Native authentication API supports the following capabilities:

- `mfa_required`: Indicates that the client app can handle multifactor authentication \(MFA\) flows inline, including calling the `/introspect`, `/challenge`, and `/token` endpoints in sequence and displaying the appropriate UI for users to complete MFA challenges when required. Advertise this capability if your app integrates inline MFA scenarios such as risk-based MFA driven by Conditional Access authentication context \(for example, third-party account takeover protection integrations that use a Web Application Firewall in front of native authentication endpoints\). If the app doesn't advertise `mfa_required` and MFA is required, the native authentication API initiates a [web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback).
- `registration_required`: The client can handle strong authentication registration: it can call the registration APIs and show UI to guide users through registering strong authentication methods.

## Behavior for unsupported challenge types and capabilities

The following table summarizes the behavior when either the native authentication API or the client app doesn't support a given challenge type or capability:

| Scenario | Behavior |
| --- | --- |
| **Client app includes unsupported challenge type** | Native authentication API returns an error and treats the request as invalid. |
| **Client app includes unsupported capability** | Native authentication API returns an error and treats the request as invalid. |
| **Client app fails to include a required challenge type** | The app doesn't support a challenge type configured by the administrator. Native authentication API initiates a [web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback). |
| **Client app fails to include a required capability** | The app functions normally if MFA or strong authentication registration is not required. If these capabilities are required but not supported, native authentication API initiates a [web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback) to complete the authentication flow. |

## Related content

- [Native authentication web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback)
- [Native authentication Android SDK tutorials](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-android-sign-in)
- [Native authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api)
