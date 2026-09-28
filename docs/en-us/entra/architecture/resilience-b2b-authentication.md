<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-b2b-authentication -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Build resilience in external user authentication

[Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b) \(Microsoft Entra B2B\) is a feature of [External Identities](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure) that enables collaboration with other organizations and individuals. It enables the secure onboarding of guest users into your Microsoft Entra tenant without having to manage their credentials. External users bring their identity and credentials with them from an external identity provider \(IdP\) so they don't have to remember a new credential.

## Ways to authenticate external users

You can choose the methods of external user authentication to your directory. You can use Microsoft IdPs or other IdPs.

With every external IdP, you take a dependency on the availability of that IdP. With some methods of connecting to IdPs, there are things you can do to increase your resilience.

Note

Microsoft Entra B2B has the built-in ability to authenticate any user from any [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/) tenant or with a personal [Microsoft Account](https://account.microsoft.com/account). You do not have to do any configuration with these built-in options.

### Considerations for resilience with other IdPs

When you use external IdPs for guest user authentication, there are configurations that you must maintain to prevent disruptions.

| Authentication Method | Resilience considerations |
| --- | --- |
| Federation with social IDPs like [Facebook](https://learn.microsoft.com/en-us/entra/external-id/facebook-federation) or [Google](https://learn.microsoft.com/en-us/entra/external-id/google-federation). | You must maintain your account with the IdP and configure your Client ID and Client Secret. |
| [SAML/WS-Fed identity provider \(IdP\) federation](https://learn.microsoft.com/en-us/entra/external-id/direct-federation) | You must collaborate with the IdP owner for access to their endpoints upon which you're dependent. You must maintain the metadata that contain the certificates and endpoints. |
| [Email one-time passcode](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode) | You're dependent on Microsoft's email system, the user's email system, and the user's email client. |

## Self-service sign-up

As an alternative to sending invitations or links, you can enable [Self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview). This method allows external users to request access to an application. You must create an [API connector](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-add-api-connector) and associate it with a user flow. You associate user flows that define the user experience with one or more applications.

It's possible to use [API connectors](https://learn.microsoft.com/en-us/entra/external-id/api-connectors-overview) to integrate your self-service sign-up user flow with external systems' APIs. This API integration can be used for [custom approval workflows](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-add-approvals), [performing identity verification](https://learn.microsoft.com/en-us/entra/external-id/code-samples-self-service-sign-up), and other tasks such as overwriting user attributes. Using APIs requires that you manage the following dependencies.

- **API Connector Authentication**: Setting up a connector requires an endpoint URL, a username, and a password. Set up a process by which these credentials are maintained, and work with the API owner to ensure you know any expiration schedule.
- **API Connector Response**: Design API Connectors in the sign-up flow to fail gracefully if the API isn't available. Examine and provide to your API developers these [example API responses](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-add-api-connector) and the [best practices for troubleshooting](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-add-api-connector). Work with the API development team to test all possible response scenarios, including continuation, validation-error, and blocking responses.

## Next steps

### Resilience resources for administrators and architects

- [Build resilience with credential management](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-credentials)
- [Build resilience with device states](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-device-states)
- [Build resilience by using Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-continuous-access-evaluation)
- [Build resilience in your hybrid authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid)
- [Build resilience in application access with Application Proxy](https://learn.microsoft.com/en-us/entra/architecture/resilience-on-premises-access)

### Resilience resources for developers

- [Build IAM resilience in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
- [Build resilience in your CIAM systems](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
