<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Plan a Microsoft Entra External ID deployment

Microsoft Entra External ID adds customer identity and access management \(CIAM\) to your app on the Microsoft Entra platform, so you get consistent app integration, tenant management, and operations across workforce and customer scenarios.

**Applies to external tenants:** Feature support varies by authentication approach and API or SDK version. Compare Microsoft-hosted authentication, Embedded native authentication, and Bring Your Own UX \(BYO UX\) in the [authentication approach overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach). Check feature availability in the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability).

Use this guide to plan your deployment in six steps. Each section summarizes the key choices and links to setup instructions and reference documentation.

![Diagram of six setup steps: create a tenant, choose authentication, register an app, integrate a user flow, secure sign-in, and customize sign-in.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal.png)

Jump to a step for details, or go straight to the **How-to guides**.

| Step | How-to guides |
| --- | --- |
| **[Step 1: Create an external tenant](#step-1-create-an-external-tenant)** | • [Create an external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal)  <br>• [Or start a free trial](https://aka.ms/ciam-free-trial?wt.mc_id=ciamcustomertenantfreetrial_linkclick_content_cnl) |
| **[Step 2: Choose an authentication approach](#step-2-choose-an-authentication-approach)** | • [Choose an authentication approach](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach) |
| **[Step 3: Register your application](#step-3-register-your-application)** | • [Register your application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) |
| **[Step 4: Integrate a sign-in flow with your app](#step-4-integrate-a-sign-in-flow-with-your-app)** | • [Create a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers)  <br>• [Add your app to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application) |
| **[Step 5: Secure your sign-in](#step-5-secure-your-sign-in)** | • [Add multifactor authentication \(MFA\)](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers)  <br>• [Review security and governance](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-security-customers) |
| **[Step 6: Customize your sign-in](#step-6-customize-your-sign-in)** | • [Customize branding](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers) *\(Microsoft-hosted pages\)*  <br>• [Use a custom URL domain](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-url-domain)  <br>• [Add custom authentication extensions](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-extensions) |

## Step 1: Create an external tenant

![Diagram showing the setup flow with step 1, create an external tenant, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-1.png)

Your external tenant is the resource where you register apps and manage customer identities, separate from your workforce tenant. When you create it, you choose its geographic location and domain name. If you're migrating from Azure AD B2C, review the [Azure AD B2C migration planning guidance](https://learn.microsoft.com/en-us/entra/external-id/customers/plan-your-migration-from-b2c-to-external-id). For other identity deployments, review [user migration guidance](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users).

The directory contains both [admin accounts](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-manage-admin-accounts) and customer accounts. Customers usually self-register; you can also [create local accounts](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-manage-customer-accounts). Customer accounts have a restricted [default permission set](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-user-permissions) and can't see other users, groups, or devices.

### How to create an external tenant

- [Create an external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal) in the Microsoft Entra admin center.
- Don't have a tenant yet? [Start a free trial](https://aka.ms/ciam-free-trial?wt.mc_id=ciamcustomertenantfreetrial_linkclick_content_cnl).
- Using Visual Studio Code? Use the [Microsoft Entra External ID extension](https://aka.ms/ciamvscode/quickstarts/marketplace) and its [quickstart guide](https://aka.ms/ciamvscode/quickstartguide).

## Step 2: Choose an authentication approach

![Diagram showing the setup flow with step 2, choose an authentication approach, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-2.png)

Decide how to build the sign-in experience before you register your app. This choice drives the rest of your integration.

- **Microsoft-hosted authentication** — Microsoft hosts the sign-in page, and your app redirects users to it. You can apply company branding or application-specific branding themes.
- **Embedded native authentication** — Your app presents the sign-in interface and calls an SDK or the Native Authentication API. Your team manages the interface and integration.
- **Bring Your Own UX \(BYO UX\)** — Your team hosts a separate authentication website within a browser-based authorization flow. Microsoft Entra External ID applies authentication policies and verifies credentials.

### How to choose an authentication approach

- [Choose an authentication approach](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach) — feature comparison and trade-offs.
- [Embedded native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication) — integration guidance for an interface in your app.

## Step 3: Register your application

![Diagram showing the setup flow with step 3, register your application, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-3.png)

Register your app in your external tenant to establish its application identity. Follow the registration guide for your platform and authentication approach.

| Setting | Microsoft-hosted | Embedded native authentication | BYO UX |
| --- | --- | --- | --- |
| Redirect URI | Register a callback URI for your app. | Configure the redirect required by your platform or browser integration, separately from direct native code redemption. | Register a web-type redirect URI, including for public clients. |
| Client type | Choose the registration for your app's platform. | Public client; enable public client flows. | Public or confidential client. |
| Service API authority | Default tenant domain or a custom URL domain. | The Native Authentication API V2 requires a tenant-verified custom domain for browser-based apps, not for non-browser clients using native HTTP transports. | Tenant-verified custom domain for API calls. |
| Integration setup | Configure hosted sign-in. | Enable native authentication for the app. | Use Microsoft Graph beta to configure your self-hosted authentication page. |

After registration, configure your application and tenant identifiers. Keep confidential-client credentials on the server; don't place client secrets in mobile apps or browser code.

### How to register your application

- Find platform-specific guidance on the [Samples by app type and language page](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all).
- If your platform isn't listed, follow the general [register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) quickstart.
- For Embedded native authentication app settings, see [Configure an app for Embedded native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-configure-app).

## Step 4: Integrate a sign-in flow with your app

![Diagram showing the setup flow with step 4, integrate a sign-in flow with your app, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-4.png)

Create a sign-up and sign-in user flow that defines the sign-in methods, attributes to collect, and identity providers for your app. Use the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability) to check which configured features are available through your integration.

For the Native Authentication API integrations, follow the [attribute collection contract](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-user-attributes).

### Plan your user flow

- **Number of user flows.** Each app uses one user flow. You can share one flow across apps or create up to 10 per tenant for differentiated experiences.
- **Attributes to collect.** Decide which built-in attributes you need and whether you need [custom attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes).
- **Terms and conditions consent.** Use custom attributes to capture consent with links to your terms and privacy policies.
- **Token claims.** [Add required attributes to the token](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-attributes-to-token) if your app depends on them.
- **Sign-in methods.** Configure local account methods and identity providers for each user flow. With Microsoft-hosted authentication, configured federated providers can include [Google](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-google-federation-customers), [Facebook](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers), [Apple](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers), [another Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-entra-id-federation-customers), or [custom OpenID Connect \(OIDC\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers). Federation isn't supported through the Native Authentication API. Confirm method and journey availability in the [methods and journeys comparison](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#methods-and-journeys-by-approach).

### How to integrate a user flow with your app

- [Define custom attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes) \(if needed\).
- [Create the sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).
- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application).
- Integrate your app code:

  - **Microsoft-hosted:** Follow a [sample or quickstart](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all) for your app type.
  - **Embedded native authentication:** Start with the [application configuration guide](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-configure-app), [SDK quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication), or [Native Authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication). Confirm platform and SDK coverage in the [native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication#how-to-use-native-authentication). For an existing V1 integration, use the [V1 API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1) and [migration guide](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2).
  - **Bring Your Own UX:** Review the [Bring Your Own UX overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-bring-your-own-ux) for architecture, requirements, and implementation guidance.

## Step 5: Secure your sign-in

![Diagram showing the setup flow with step 5, secure your sign-in, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-5.png)

Plan MFA and review security for your customer-facing apps. Configure tenant policies and protect application sessions, tokens, and any credentials or state your integration handles. Assign ownership for the interface, integration, and hosting components your team operates. For responsibility boundaries, see [authentication integration responsibilities](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach#security-considerations).

- **Enable MFA.** Review [available MFA methods](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers).
- **Review security and governance.** Plan for Conditional Access, risk-based policies, and auditing. See [Security and governance](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-security-customers).

## Step 6: Customize your sign-in

![Diagram showing the setup flow with step 6, customize your sign-in, highlighted.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-planning-your-solution/planning-flow-horizontal-step-6.png)

Customize the sign-in look and feel and extend it with your own business logic. You can configure Microsoft-hosted pages, manage the interface in your app with Embedded native authentication, or host your own page with BYO UX.

- **Customize branding** *\(Microsoft-hosted pages\)*. Apply your logo, colors, and language strings to the sign-in pages. See [Customize the sign-in look and feel](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers).
- **Use a custom URL domain where required.** The Native Authentication API V2 requires a tenant-verified custom domain for browser-based apps, such as SPAs, but not for non-browser clients, such as iOS and Android apps using native HTTP transports. BYO UX requires a tenant-verified custom domain. See [Custom URL domain](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-url-domain).
- **Add custom authentication extensions.** Extend the flow with server-side logic. Event availability can differ by approach and API or SDK version. See [Custom authentication extensions](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-extensions).

## Next steps

- [Start a free trial](https://aka.ms/ciam-free-trial?wt.mc_id=ciamcustomertenantfreetrial_linkclick_content_cnl) or [create your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
- [Find samples and guidance for integrating your app](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all).
- [Learn how to migrate users from your current identity provider](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users).
- See also the [Microsoft Entra External ID Developer Center](https://aka.ms/ciam/dev) for the latest developer content and resources.
- [Microsoft Entra External ID deployment guide for security operations](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-operations).
