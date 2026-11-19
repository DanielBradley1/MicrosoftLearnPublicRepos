<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Microsoft Entra External ID authentication approaches overview

Choose how your customer-facing application presents Microsoft Entra External ID authentication. Compare where the interface runs, what your team maintains, and which capabilities you need. Different applications can use different approaches.

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

## Authentication approach options

| Approach | How required authentication steps are presented | What your team controls |
| --- | --- | --- |
| **Microsoft-hosted authentication** | On Microsoft-hosted pages reached through a browser redirect. | **Company branding:** Tenant-wide logos, text, and styling. **Branding themes:** Customization for selected applications. |
| **Embedded native authentication** | In authentication screens your app implements. | Screens and their integration with your app. |
| **Bring Your Own UX \(BYO UX\)** | On a separate authentication website your team hosts. | The website, its presentation, and its integration. |

### Common policy foundation

All approaches use user flows and authentication policies configured in Microsoft Entra External ID. External ID provides the authentication service; the approaches differ in how the interface is hosted and integrated.

For each application, consider your sign-up, sign-in, account recovery, identity provider, and policy requirements. Confirm that your chosen integration supports those journeys by using the [methods and journeys comparison](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach). Feature availability can differ by approach and API or SDK version.

## Application and audience requirements

Match each requirement to a candidate, then verify its journeys and integration requirements.

| Requirement | Approach to evaluate | Verification or next step |
| --- | --- | --- |
| **Microsoft-managed authentication pages** | [Microsoft-hosted authentication](#when-to-use-microsoft-hosted-authentication). | Review [company branding](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers), application-specific themes, and [sign-up and sign-in availability](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach). Plan the app integration and presentation settings. |
| **Authentication screens integrated into your app** | [Embedded native authentication](#when-to-use-embedded-native-authentication). | Review [platform support](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication#how-to-use-native-authentication) and [method availability](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach). Plan the app screens and authentication-state handling. |
| **An authentication website with its own UI and release cycle** | [Bring Your Own UX](#when-to-use-bring-your-own-ux). | Review the website and domain requirements for one or more applications. Plan the website's API and browser integration. |
| **Different interaction requirements across applications** | Combine approaches. | Evaluate each application's interface, integration, session, and journey requirements. |

Important

The Native Authentication API V2 and Bring Your Own UX \(BYO UX\) are in preview. The Native Authentication API V1 remains generally available. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to preview features.

Plan how your team updates the authentication interface:

- Configure company branding and themes for Microsoft-hosted pages.
- Release Embedded native authentication screens with your application.
- Deploy a BYO UX website on its own release schedule.

## Microsoft-hosted authentication

Evaluate Microsoft-hosted authentication when you want authentication pages hosted and managed by Microsoft. Configure [company branding](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers) across the tenant, or use [branding themes](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-customize-branding-themes-apps) for selected applications. Your team integrates the app and configures policy.

## Embedded native authentication

Evaluate Embedded native authentication when you want authentication interactions integrated into your application's interface. Your team builds the screens and handles credentials, state, and integration. Confirm platform and SDK support in the [native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication). For method and journey support, use the [methods and journeys comparison](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach) and [browser fallback requirements](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback).

The Native Authentication API V2 requires a [tenant-verified custom domain](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-url-domain) for browser-based apps, such as single-page applications \(SPAs\), to help protect against cross-site request forgery \(CSRF\). Also plan a cross-origin resource sharing \(CORS\) proxy or edge policy for cross-origin browser calls. Non-browser clients, such as Android and iOS apps using native HTTP transports, don't require a custom domain or CORS configuration. Enable the required methods in your tenant and test the journeys your app needs.

## Bring Your Own UX

With Bring Your Own UX \(BYO UX\), you control and operate the authentication website instead of using Microsoft-hosted pages. Unlike embedded native authentication, the authentication website runs separately from your applications and can serve multiple apps.

Choose BYO UX when you want more control over the presentation and user experience than Microsoft-hosted custom branding provides, or if you want a sign-in website you can share across applications and update independently of their releases. Your team takes responsibility for hosting and maintaining the website. For details, see the [Bring Your Own UX overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-bring-your-own-ux).

## Ownership and security responsibilities

For every approach, your team configures authentication policies, integrates the application, and protects application sessions and tokens. Plan accessibility, testing, monitoring, security updates, incident response, and release coordination for the components your team operates.

Microsoft maintains Microsoft-hosted sign-in pages. With Embedded native authentication, your team maintains app screens and state handling. With BYO UX, your team hosts and manages the website, proxy, and browser integration.

Protect any credentials, continuation state, and tokens your integration handles. Avoid exposing them in URLs or logs. Test what happens when policy requires another verification step and when a session expires. Identify the team responsible for deploying fixes to the components your organization operates.

## Feature comparison

Use the [authentication approach support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability) to compare methods, policies, and journeys.

| Requirement | Coverage to review |
| --- | --- |
| **Sign-up, sign-in, and password reset** | Confirm [method and journey availability](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach) for your approach. For tenant configuration, see [identity providers and authentication methods](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-authentication-methods-customers). |
| **Additional verification** | Confirm method availability and factor registration requirements in the [multifactor authentication \(MFA\) guidance](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers). |
| **Session behavior** | Review [Conditional Access](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#conditional-access), [sign-in frequency](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-session-lifetime#user-sign-in-frequency), and [single sign-on](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#single-sign-on). Plan sign-out for each app's session. |
| **Custom business logic** | Confirm which [custom authentication extension events](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-extensions) your integration supports. |

### Supported languages and frameworks

For Microsoft-hosted integration, see [Samples by app type and language](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all) and [Register an app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). For Embedded native authentication, confirm platform and SDK requirements in the [native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication). For BYO UX, plan a self-hosted browser authorization flow with a web-type redirect URI.

## Related content

- [Plan your customer identity solution](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution).
- [Supported features in workforce and external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers).
- [Authentication methods for customer-facing applications](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-authentication-methods-customers).
