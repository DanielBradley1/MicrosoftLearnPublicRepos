<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-third-party-account-take-over-protection-native-api -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Tutorial: Integrate third-party account takeover protection with native authentication API

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial guides you through integrating third-party Account Takeover \(ATO\) protection providers with Native API authentication in Microsoft Entra External ID. By using a Web Application Firewall \(WAF\) to intercept authentication requests, you can implement risk-based MFA challenges during sign-in to protect against automated attacks and account compromise.

Important

Third-party ATO protection for native authentication is supported through a WAF placed in front of the native authentication API endpoints. This is the supported architecture for Native API flows. Microsoft Entra External ID doesn't expose a `RiskPreventionProvider`-style configuration for native authentication; risk evaluation is performed by your third-party provider via the WAF, and Microsoft Entra enforces the resulting MFA requirement through Conditional Access authentication context. Browser-delegated \(web-hosted\) sign-in flows aren't covered by this tutorial.

Note

This tutorial assumes you manually make raw HTTP requests to execute the authentication flow. When possible, use a Microsoft-built and supported authentication SDK. See [Tutorial: Prepare your Android mobile app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-android-app) and [Tutorial: Prepare your iOS/macOS mobile app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-ios-macos-app).

## Prerequisites

- An [external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal). If you don't already have one, create an external tenant.
- A [registered application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) in the Microsoft Entra admin center with the following configuration:

  - Application \(client\) ID and Directory \(tenant\) ID recorded.
  - [Admin consent granted](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#grant-admin-consent-external-tenants-only).
  - [Public client and native authentication flows enabled](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication#how-to-enable-native-authentication).

- A [user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) created in the Microsoft Entra admin center and [associated with your application](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application).
- A test customer user [registered in your tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-manage-customer-accounts#create-a-customer-account) for sign-in flow testing.
- An account with at least an [Authentication Extensibility Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#authentication-extensibility-administrator) or [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) role in the external tenant.
- A [custom domain](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-url-domain) associated with your external tenant.
- A third-party ATO protection provider account \(this tutorial uses LexisNexis Risk Solutions as an example\) with the following configuration values:

  - Session query API credentials.
  - Update API access.
  - SDK integration details.

- A WAF platform account \(this tutorial uses Cloudflare\) with domain administrator privileges.

## How ATO protection works

When a user attempts to sign in using Native Authentication, the authentication request flows through a Web Application Firewall \(WAF\) that intercepts the /token endpoint. The WAF evaluates the request with your third-party ATO provider using their risk assessment APIs. If the request is flagged as suspicious based on device fingerprinting, behavioral analysis, or other risk signals, the WAF triggers a Conditional Access policy with an authentication context that requires MFA. The user must then complete the MFA challenge before authentication proceeds.

This approach allows you to apply risk-based protections during the native sign-in flow without requiring browser-based redirects, maintaining the native app user experience while protecting against account takeover attacks.

## Architecture components

This integration involves several key components working together to provide risk-based authentication:

- **External tenant:** A dedicated Microsoft Entra ID instance for managing external identities and customer access.
- **Native application:** A mobile or desktop application that uses Microsoft Entra External ID \(native authentication\) to sign users up and sign them in.
- **Native APIs:** Service endpoints that enable mobile and desktop apps to perform sign-up, sign-in, and self-service password reset \(SSPR\) flows in-app, without a browser redirect.
- **Web Application Firewall \(WAF\):** A firewall that inspects incoming and outgoing HTTP traffic, intercepts authentication requests, and coordinates with the third-party provider for risk evaluation.
- **Third-party ATO provider:** A third-party provider that delivers bot detection, device fingerprinting, and risk-assessment services.
- **Conditional Access \(CA\) policy:** A policy that specifies which users, apps, and conditions are in scope and the controls required to grant access, triggered by authentication context.
- **Authentication context:** A Conditional Access feature that allows applying granular policies to specific actions or scenarios rather than at the app level.

[![Diagram of risk-based authentication flow showing native app, WAF, third-party provider, and MFA steps.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/native-app-sign-in-flow.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/native-app-sign-in-flow.png#lightbox)

## Configuration steps

1. Create a sign-in flow for an external tenant.
2. Create a WAF configuration.
3. Enable MFA for the tenant.
4. Set up the Conditional Access authentication context.
5. Create a Conditional Access policy using authentication context.
6. Update the WAF layer to intercept specific API requests during sign-in flow.
7. Update the native app sign-in API call flow to introduce MFA.

## Configure basic sign-in flow for your external tenant

1. If you don't already have one, [create an external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
2. If you haven't already, [register an application in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). Make sure to:

   - Record the **Application \(client\) ID** and **Directory \(tenant\) ID** for later use.
   - [Grant admin consent](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#grant-admin-consent-external-tenants-only) to the application.
   - [Enable public client and native authentication flows](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication#how-to-enable-native-authentication).

3. If you haven't already, [create a user flow in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers#to-add-a-new-user-flow). When you create the user flow, take note of the user attributes you configure as required. These attributes are the ones that Microsoft Entra expects your app to submit.
4. [Associate your app registration with the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application).
5. For sign-in flow, [register a customer user](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-manage-customer-accounts#create-a-customer-account) to use for testing. Alternatively, you can get this test user after you run the sign-up flow.

## Create a WAF configuration

A WAF configuration is required to intercept the authentication requests for risk evaluation. This tutorial uses Cloudflare as an example, but you can use any WAF that supports request interception and custom logic execution.

Important

A custom domain must be associated with your external tenant before you configure the WAF. Without a custom domain, the WAF can't intercept authentication requests.

For detailed Cloudflare WAF setup instructions, see [Configure Cloudflare WAF with Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-configure-waf-integration).

## Enable multifactor authentication \(MFA\) for the tenant

To enforce MFA challenges when suspicious sign-in attempts are detected, first enable MFA for your tenant. This tutorial uses email OTP as the second factor authentication method for users during risky sign-ins.

For detailed setup instructions, see [Enable Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa).

Note

Currently, risk-based MFA for native authentication can only be applied for the "Email with Password" sign-in flow. The user must have email configured as a strong authentication method.

## Set up the Conditional Access authentication context

[Conditional Access authentication context](https://learn.microsoft.com/en-us/entra/identity-platform/developer-guide-conditional-access-authentication-context) \(auth context\) allows you to apply Conditional Access policies at a granular level based on specific actions or data sensitivity, rather than just at the application level. In this scenario, you use authentication context to trigger MFA only when the WAF determines that a sign-in attempt is risky, rather than requiring MFA for all sign-in attempts.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. In the **Conditional Access** section, select **Authentication contexts**, then select **New authentication context**.

   [![Screenshot showing the Conditional Access authentication contexts page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-authentication-contexts.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-authentication-contexts.png#lightbox)

   [![Screenshot showing the new authentication context creation form.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/add-authentication-context-form.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/add-authentication-context-form.png#lightbox)
3. Add a **Name** \(required\) and a **Description** \(optional\).
4. Select an **ID** for your auth context. The IDs range from c1 to c99. For this example, select **c3**.
5. Select **Create**.

Tip

The authentication context ID is used in the /token endpoint to indicate that the user is using a specific authentication context. Make note of the ID you selected \(for example, c3\) as you need it when configuring the WAF worker.

## Create a Conditional Access policy using authentication context

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**, then select **+ New policy**.

   [![Screenshot showing the Conditional Access policies page with the new policy option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-policies-page.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-policies-page.png#lightbox)
3. Enter a **Name** for the policy and select the specific **user or user group** \(or all users\) that the policy affects. The user needs to have email as a strong authentication method if you want to enforce email MFA with native authentication APIs.

   [![Screenshot showing the policy name and user assignment options.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-policy-users.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-policy-users.png#lightbox)

   ![Screenshot showing the user selection for the Conditional Access policy.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-authentication-context.png)
4. In **Target resources**, select **Authentication context** in the dropdown, then select the authentication context that you created earlier.
5. For **Grant**, select the action to enforce for the user \(for example, require multifactor authentication\). Select **Select**, set **Enable policy** to **On**, then select **Create**.

   ![Screenshot showing the grant controls and policy enablement settings.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/conditional-access-grant-settings.png)

At this point, you have a Conditional Access policy configured to require MFA for the selected user when they sign in to any of the tenant apps.

## Configure WAF worker for risk evaluation

This section describes how to configure the WAF to intercept /token requests and perform risk evaluation with your third-party ATO provider.

### Update the WAF layer to intercept specific API requests during sign-in flow

This tutorial uses a Cloudflare WAF. The Cloudflare WAF setup instructions are provided in the [Create a WAF configuration](#create-a-waf-configuration) section of this tutorial.

1. Sign in to the **Cloudflare account** for the external domain \(mentioned in the Create a WAF configuration step\) associated with the external tenant with at least **Domain Administrator** privilege.
2. Go to **Workers Routes**, then select **Create application**.

   ![Screenshot showing the Cloudflare Workers Routes page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/cloud-flare-workers-routes-page.png)

   ![Screenshot showing the Create application option in Cloudflare.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/cloud-flare-workers-create-application.png)
3. Select **Start with Hello World**.

   [![Screenshot of Cloudflare application creation options showing GitHub, GitLab, Hello World, template, and static file upload buttons.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/ship-something-new-cloud-flare.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/ship-something-new-cloud-flare.png#lightbox)
4. Name the worker and select **Deploy**.  [![Screenshot of Cloudflare Workers deployment screen showing worker name, code preview, and Deploy button for Hello World setup.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/deploy-hello-world-worker.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/deploy-hello-world-worker.png#lightbox)
5. After the worker is deployed, select the **Settings** tab. Select **+Add** in **Domains & Routes**.

   [![Screenshot of the Settings tab with Domains & Routes section and a visible +Add link for adding routes.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/worker-domains-routes.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/worker-domains-routes.png#lightbox)
6. Select **Route**.  [![Screenshot of Domains & Routes settings with Custom domain and Route options for mapping a Worker endpoint.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/cloud-flare-domains-routes.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/cloud-flare-domains-routes.png#lightbox)
7. Select the domain from **Zone**. Add the following value in the **Route** field:

   `*<custom_domain>/<external_tenant_id(guid)>/oauth2/v2.0/token*`

   Select **Fail Closed** for failure mode.

   [![Screenshot showing the route configuration with zone and failure mode settings.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/route-configuration-failure-mode.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/tutorial-third-party-account-take-over-protection-native-api/route-configuration-failure-mode.png#lightbox)
8. Select **Add Route**.

If the WAF setup is configured properly, all requests to the external tenant /token endpoint are intercepted by the worker. Configure the worker logic to determine which requests to challenge by MFA and to do the risk evaluation with the third-party risk provider.

### Configure worker logic for risk evaluation

Configure the worker logic to:

1. Extract relevant information from the authentication request \(device fingerprint, IP address, behavioral data\).
2. Send this data to your third-party ATO provider's risk assessment API.
3. Evaluate the risk score returned by the provider.
4. If the risk score exceeds your threshold, modify the request to include the authentication context that triggers MFA.
5. Forward the request to the Microsoft Entra /token endpoint.

Tip

For a complete Android SDK implementation example using WAF-based ATO protection, see the [LexisNexis Risk Solutions ATO protection sample app](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample/tree/feature/integrate-lnr-signin-ato-protection).

### Third-party provider integration

This tutorial uses [LexisNexis Risk Solutions](https://risk.lexisnexis.com/) as the third-party ATO provider. The session query API provided by LexisNexis is used for risk evaluation. Refer to the following LexisNexis documentation:

- [Session Query API](https://portal.threatmetrix.com/kb-en/Implementation_Guides/APIs/Session_Query_API.htm)
- [Update API](https://portal.threatmetrix.com/kb-en/Implementation_Guides/APIs/update_api.htm)
- SDK documentation: [Introduction to ThreatMetrix SDK and FAQ](https://portal.threatmetrix.com/kb-en/Implementation_Guides/ThreatMetrix%20SDK/introduction_to_threatmetrix_sdk_and_faq.htm)

## Update the native app sign-in API call flow to support MFA

The standard sign-in flow using native API endpoints is described in the [Native authentication API reference documentation](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api?tabs=emailOtp#api-reference-for-sign-in-flow). This flow doesn't invoke MFA by default. This section describes how to update your native app to support risk-based MFA.

In this tutorial, you invoke risk-based MFA using the auth context configured in the previous steps.

Note

Currently, risk-based MFA can only be applied for the "Email with Password" flow.

The following flow uses the WAF as the layer to evaluate the risk for the /token calls.

### Logical flow to initiate MFA

1. Invoke `/token` with the auth context defined for the MFA flow.
2. The `/initiate` endpoint continues to use a `CredentialToken` as state object for the first factor authentication flow.
3. The `/challenge` endpoint continues to use a `CredentialToken` as state object for the first factor authentication flow.
4. On `/token`, risk is evaluated in WAF layer. If the WAF layer decides to review the request with a challenge, a new `/token` call is made with the `AuthContext` configured for the MFA flow \("c3" in this example\).
5. The `/introspect` endpoint reads methods from `CredentialVerificationInputState` and returns them to the user.
6. The `/challenge` endpoint picks the strong auth method used for challenging, by reading the strong auth methods from `CredentialVerificationInputState` and comparing them against the request's challenge\_types. When a method is selected and passed to EC UCV for challenge operation, the ID and type of the selected method are written to `CredentialVerificationIntermediateState`.
7. The `/token` endpoint reads the strong auth method ID and type from `CredentialVerificationIntermediateState`, and passes this to EC UCV verify operation, along with the oob value from the request. When EC UCV returns successfully, the `/token` handler pops and merges `CredentialVerificationIntermediateState` onto `CredentialToken`. By doing so, the FlowToken in `StsRequest` is updated with MFA details. `StsRequest` runs through the pipeline to complete the authentication flow.

Tip

Your native app must be prepared to handle the MFA flow when triggered. Ensure your app can call the `/introspect` endpoint, handle the `/challenge` for email OTP, and submit the OTP value in the final `/token` call.

### Test the end-to-end flow

After you finish the configuration, validate the integration:

1. Sign in with a test customer user from a low-risk context \(for example, a known device and IP\). The sign-in should complete without an MFA challenge.
2. Repeat the sign-in from a context that your third-party ATO provider classifies as risky \(for example, a new device, anonymized IP, or simulated bot traffic per your provider's testing guidance\). The WAF should trigger the Conditional Access authentication context, and your app should receive a challenge that requires email OTP MFA before issuing tokens.
3. Confirm that the `/token` response after MFA contains the expected access and ID tokens, and that sign-in telemetry in your tenant and provider dashboard reflects the risk decision.

If MFA isn't triggered as expected, verify that the user has email configured as a strong authentication method, the Conditional Access policy targets the correct authentication context \(for example, `c3`\), and the WAF worker is invoking the provider's risk API and forwarding the auth context on the `/token` call.

## Next steps

Now that you've integrated ATO protection with native authentication, explore these related resources:

- [Native authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api)
- [Tutorial: Prepare your Android mobile app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-android-app)
- [Tutorial: Prepare your iOS/macOS mobile app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-ios-macos-app)
- [Configure Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policies)
- [Authentication context in Conditional Access](https://learn.microsoft.com/en-us/entra/identity-platform/developer-guide-conditional-access-authentication-context)
- [Configure custom domains for external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-url-domain)
- [Enable Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa)
- [Configure Cloudflare WAF with Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-configure-waf-integration)
- [LexisNexis Risk Solutions ATO protection sample app](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample/tree/feature/integrate-lnr-signin-ato-protection)
