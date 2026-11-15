<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/prerequisites?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Prepare a partner integration with Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Before you build a partner integration with Copilot Managed Runtime, set up the required packages and development environment. Then register a multitenant Microsoft Entra application, configure delegated permissions, get customer admin consent, and authenticate the CLI for local or hosted use.

## Required packages

| Package | Purpose | Install location |
| --- | --- | --- |
| [`@microsoft/managed-apps-cli`](https://www.npmjs.com/package/@microsoft/managed-apps-cli) | The `ms` app lifecycle and integration CLI | Partner development container or developer machine |
| [`@microsoft/managed-apps`](https://www.npmjs.com/package/@microsoft/managed-apps) | Runtime SDK used by app code | App production dependencies |
| [`@microsoft/managed-apps-vite-plugin`](https://www.npmjs.com/package/@microsoft/managed-apps-vite-plugin) | Local config and Local Play integration for Vite | App development dependencies |

For current supported developer tools and packages see the [developer overview](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/?view=o365-worldwide).

## Set up the development environment

- [Node.js](https://nodejs.org/) \(LTS version\) >= v24.11.0.
- [npm](https://www.npmjs.com/package/npm).
- Git for platform-managed or external repository modes.
- A Microsoft Entra account in an eligible tenant.
- A user-scoped workspace containing the app source.

Install the CLI in the development environment:

```bash
npm install --global @microsoft/managed-apps-cli
ms --version
```

For the basic setup and authentication flow, see the [CLI quickstart](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide).

## Register a Microsoft Entra application

Register an application with the [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) for your product integration and configure it as **Accounts in any Microsoft Entra directory**. This creates a [multitenant application](https://learn.microsoft.com/en-us/entra/identity-platform/single-and-multi-tenant-apps) that app makers from customer tenants can use with their organizational identity.

After creating the application:

1. Retain its application \(client\) ID for customer consent, Microsoft allowlisting, and integration configuration.
2. Add the required delegated permissions listed below.
3. **Recommended:** [Mark the application as publisher verified](https://learn.microsoft.com/en-us/entra/identity-platform/mark-app-as-publisher-verified) so customer administrators can verify the publisher in the consent dialog. Publisher verification is required if the application is later submitted as a multitenant OpenID Connect application for gallery publication.
4. Provide the application \(client\) ID to Microsoft for allowlisting. Microsoft must allowlist the application before it can be used for the Copilot Managed Runtime partner integration.

### Required delegated permissions

For each required permission:

1. Go to **API permissions** > **Add a permission** > **APIs my organization uses**.
2. Search for the API and select the exact name shown below, not a similarly named test entry.
3. Under **Delegated permissions**, add the listed scope.

For Power Platform API, expand `ManagedApps` to find `ManagedApps.ReadWrite.All`.

| API to search for | Delegated scope | Purpose |
| --- | --- | --- |
| **Power Platform API** | `ManagedApps.ReadWrite.All` | Create and manage apps on behalf of the signed-in app maker. |
| **Power Platform API** | `Connectivity.Connections.UserConsent` | Request authorization for the partner application to use the signed-in maker's connector connection. |
| **Dataverse** | `user_impersonation` | Access Microsoft Dataverse as the signed-in app maker. |
| **Azure API Connections** | `Runtime.All` | Use connector connections on behalf of the signed-in app maker. |

Configure these scopes on the partner application. The customer tenant administrator reviews the requested permissions in the admin consent dialog.

For general instructions, see [configure a client application's delegated API permissions](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-configure-app-access-web-apis#add-permissions-to-access-your-web-api).

The partner's Microsoft Entra application is used by the partner gateway to acquire tokens for the app maker and the upstream resource being called, with the permissions needed for Copilot Managed Runtime and organizational connectors. The gateway, not the hosted CLI process, owns acquisition, storage, and refresh of those tokens.

### Add the application to a customer tenant

Preconfigure the required delegated permissions in your application registration. The customer doesn't select or configure those permissions. Instead, a customer tenant administrator must review and accept them for the organization.

Direct the administrator to the tenant-wide admin consent URL, substituting the customer tenant ID and the partner application's client ID:

```text
https://login.microsoftonline.com/<customer-tenant-id>/adminconsent?client_id=<partner-application-client-id>
```

The administrator sees the requested permissions in the consent dialog and must accept them. Approval creates the application's service principal in the customer tenant and grants the configured permissions on behalf of the organization. App makers aren't prompted to configure or individually consent to those permissions afterward. If you add a required permission later, a customer administrator must grant consent again.

For details, see [grant tenant-wide admin consent to an application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/grant-admin-consent#construct-the-url-for-granting-tenant-wide-admin-consent) and [create an enterprise application from a multitenant application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/create-service-principal-cross-tenant).

### Optional: publish in the Microsoft Entra application gallery

Customer admin consent doesn't require a listing in the Microsoft Entra application gallery. Gallery publication is a separate, optional step for public discoverability. See the [application gallery overview](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/overview-application-gallery) and [gallery publishing and submission process](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/v2-howto-app-gallery-listing). Review the current submission notice on that page before planning around a new listing.

## Authenticate the CLI

Use [HTTP Forward Mode](#http-forward-mode) to authenticate and run the CLI in a hosted service.

### Browser-based authentication

For local developer use, the CLI supports a browser-based Microsoft Entra flow:

```bash
ms auth login --account creator@contoso.com
ms auth status --json
```

Multiple accounts can be cached. Verify or switch the active account before an app mutation:

```bash
ms auth switch --account creator@contoso.com
```

For command details, see the [CLI reference](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#authentication).

This browser flow authenticates the CLI directly and is separate from partner product sign-in. In [HTTP Forward Mode](#http-forward-mode), authentication is instead delegated to the partner gateway; the hosted workflow doesn't run `ms auth login`.

### HTTP Forward Mode

*HTTP Forward Mode* is the supported way to authenticate and use the CLI in a hosted service. It sends every outbound CLI request, including telemetry, to a partner-owned gateway. The gateway authenticates the caller, routes the request to its original destination, supplies any required upstream token, and returns the upstream response.

This pattern lets an untrusted or ephemeral container run without a persistent CLI token cache:

1. The app maker signs in to the partner product and Microsoft Entra.
2. The gateway securely associates the maker's Microsoft Entra identity and tokens with the correct user and tenant, and owns token refresh.
3. The container receives only forward-mode configuration and, when used, a gateway hop token injected at runtime.
4. The CLI sends requests to the gateway. The gateway validates the hop, acquires a token for the requested upstream audience, forwards the request, and relays the response.

This avoids storing the CLI's MSAL token cache in the container. It doesn't make the container secret-free: a forward hop token or secret-bearing custom header must be protected like any other credential.

Enable HTTP Forward Mode by setting these environment variables before running CLI commands:

```bash
export MS_CLI_USE_HTTP_FORWARD=true
export MS_CLI_HTTP_FORWARD_URL=<forward-service-url>
export MS_CLI_HTTP_FORWARD_AUTH_TOKEN=<bearer-token>
export MS_CLI_HTTP_FORWARD_TENANT_ID=<tenant-id>
export MS_CLI_HTTP_FORWARD_HEADERS='{"x-forward-secret":"<secret>"}'
```

| Variable | Required | Description |
| --- | --- | --- |
| `MS_CLI_USE_HTTP_FORWARD` | Yes, set to `true` | Enables forward mode. The CLI won't start if set without `MS_CLI_HTTP_FORWARD_URL`. |
| `MS_CLI_HTTP_FORWARD_URL` | Yes | Single gateway URL to which every outbound request is sent. |
| `MS_CLI_HTTP_FORWARD_AUTH_TOKEN` | No | Bearer credential for the CLI-to-gateway hop. When set, the CLI sends it in `Authorization` on every forwarded request. When unset, the header is omitted and the gateway must establish trust another way. |
| `MS_CLI_HTTP_FORWARD_TENANT_ID` | For tenant-scoped commands | Microsoft Entra tenant ID of the calling app maker. Required by `ms app *`, `ms connector list`, and `ms connector list-actions`. |
| `MS_CLI_HTTP_FORWARD_HEADERS` | No | JSON object of additional static string headers sent on every request. Use only for gateway-specific routing or authentication values. |

Inject secret values at runtime from a secret manager. Don't commit them or persist them in shell profiles, `.env` files, container images, or pipeline configuration.

#### Enable connection user consent

For hosted partner integrations, set this environment variable where the CLI process runs, before adding connector data sources:

```bash
export MS_CLI_ENABLE_CONNECTOR_USER_CONSENT=true
```

The flag enables the CLI to request authorization for your application to use the signed-in app maker's connector connection. It is off by default while the consent endpoint rolls out. When unset, the CLI skips this request.

The flag doesn't replace the [`Connectivity.Connections.UserConsent` delegated permission](#required-delegated-permissions) or [customer tenant administrator consent](#add-the-application-to-a-customer-tenant). For the data-source workflow, see [Connect partner apps to data](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/connect-to-data?view=o365-worldwide).

#### Gateway request and response contract

The CLI preserves the original HTTP method, body, query string, and other headers, but changes the destination to `MS_CLI_HTTP_FORWARD_URL` and adds:

| Header | When sent | Gateway responsibility |
| --- | --- | --- |
| `x-ms-target-url` | Every request | Route to the original destination after validating that the destination is allowed. |
| `x-ms-auth-resource` | The upstream request requires authentication | Acquire or select a user token for this audience and use it for the upstream request. |
| `x-ms-body-token-resource` | An upstream flow carries its token in the JSON body | Replace the exact gateway hop-token value in the body with a newly acquired on-behalf-of token for this audience. This flow requires `MS_CLI_HTTP_FORWARD_AUTH_TOKEN`. |
| `Authorization` | `MS_CLI_HTTP_FORWARD_AUTH_TOKEN` is set | Validate this bearer as the CLI-to-gateway credential. Don't forward it upstream; replace or inject a token for the upstream audience when required. |
| Custom headers | `MS_CLI_HTTP_FORWARD_HEADERS` is set | Apply gateway-specific authentication or routing. Treat secret-bearing values as credentials. |

Return the upstream response, including its HTTP status, headers, and body, so the CLI can apply its normal success and error handling. Don't turn an upstream failure into a successful response.

#### Security and failure handling

Follow these requirements to protect user and tenant context and preserve actionable error information in HTTP Forward Mode.

- Treat `x-ms-target-url`, audience headers, and the configured tenant ID as request inputs, not proof of identity. Bind them to the authenticated partner user and Microsoft Entra tenant, and allow only expected Copilot Managed Runtime, connector, and telemetry destinations and audiences.
- Isolate stored tokens by user and tenant. Never reuse one maker's token or tenant context for another maker's request.
- CLI protocol headers take precedence over custom headers. Custom values that collide case-insensitively with `Authorization`, `Content-Type`, `x-ms-target-url`, `x-ms-auth-resource`, `x-ms-body-token-resource`, or `x-ms-client-request-id` are ignored. Header names and values containing CR or LF are rejected.
- The CLI refuses to start when forward mode has no URL or when `MS_CLI_HTTP_FORWARD_HEADERS` isn't a JSON object containing only string values. Tenant-scoped commands refuse to run without `MS_CLI_HTTP_FORWARD_TENANT_ID`.
- Preserve the CLI's normal error output for gateway authentication, routing, network, and upstream HTTP failures so the app maker or support workflow can diagnose the failure.

HTTP Forward Mode applies to CLI HTTP requests. It doesn't configure authentication or network access for raw Git operations or the maker's browser.
