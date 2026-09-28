<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/agent-oauth-protocols -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Authentication protocols in agents

Agents use OAuth 2.0 protocols with specialized token exchange patterns enabled by Federated Identity Credentials \(FIC\). All agent auth flows involve multi-stage token exchanges where the agent identity blueprint impersonates the agent identity to perform operations. This article explains the authentication protocols and token flows used by agents. It covers delegation scenarios, autonomous operations, and federated identity credential patterns. Microsoft recommends that you use our SDKs like [Microsoft Entra ID Auth SDK \(sidecar\)](https://aka.ms/entra/sdk/agentid) since implementing these protocol steps isn't easy.

All agent entities are confidential clients that can also serve as APIs for On-Behalf-Of scenarios. Interactive flows aren't supported for any agent entity type, ensuring that all authentication occurs through programmatic token exchanges rather than user interaction flows.

Warning

Microsoft recommends using the approved SDKs like Microsoft.Identity.Web and Microsoft Entra ID Auth SDK \(sidecar\) libraries to implement these protocols. Manual implementation of these protocols is complex and error-prone, and using the SDKs helps ensure security and compliance with best practices.

## Prerequisites

If you aren't familiar already, go through the following protocol docs.

- [Microsoft identity platform and OAuth 2.0 On-Behalf-Of flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow)
- [Microsoft identity platform and the OAuth 2.0 client credentials flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow)

## Supported grant types

The following are the supported grant types for agent applications.

### Agent identity blueprint

Agent identity blueprints support `client_credentials` enabling secure token acquisition for impersonation scenarios. The `jwt-bearer` grant type facilitates token exchanges in [On-Behalf Of scenarios](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow), allowing for delegation patterns. `refresh_token` grants enable background operations with user context, supporting long-running processes that maintain user authorization.

### Agent identity

Agent identities use `client_credentials` for app-only autonomous operations, enabling independent functionality without user context, and impersonation for a user agent identity. The `jwt-bearer` grant type supports both [client credential flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow) and [On-Behalf Of \(OBO\) flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-on-behalf-of-flow) providing flexibility in delegation patterns.`refresh_token` grants facilitate background user-delegated operations, allowing agent identities to maintain user context across extended operations.

### Unsupported flows

- The agent application model explicitly excludes certain authentication patterns to maintain security boundaries. Agents aren't supported for interactive \(`/authorize`\) flows, ensuring all authentication occurs programmatically.
- Public client capabilities aren't available, requiring all agents to operate as confidential clients.
- A web redirect URI can be configured on a blueprint for consent flows only \(`response_type=none`\), but can't be used for interactive token acquisition. Full redirect URI functionality is configured on the client application.

## Core protocol patterns

Agents can operate in three primary modes:

- Agents operating on behalf of regular users in Microsoft Entra ID \(interactive agents\). This is a regular on-behalf-of flow.
- Agents operating on their own behalf using service principals created for agents \(autonomous\).
- Agents operating on their own behalf using user principals created specifically for that agent \(for instance agents having their own mailbox\).

## Managed identities integration

Managed identities are the preferred credential type. In this configuration, the managed identity token serves as the credential for the parent agent identity blueprint, while standard MSI protocols apply for credential acquisition. This integration allows the agent ID to receive the full benefits of MSI security and management, including automatic credential rotation and secure storage.

Warning

Client secrets shouldn't be used as client credentials in production environments for agent identity blueprints due to security risks. Instead, use more secure authentication methods such as [federated identity credentials \(FIC\) with managed identities](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity) or client certificates. These methods provide enhanced security by eliminating the need to store sensitive secrets directly within your application configuration.

## Oauth protocols

There are three agent oauth flows:

[![Diagram showing the illustration of oauth flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-oauth-protocols/agent-flows.png)](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-oauth-protocols/agent-flows.png#lightbox)

- [Agent on-behalf of flow](https://learn.microsoft.com/en-us/entra/agent-id/agent-on-behalf-of-oauth-flow): Agents operating on behalf of regular users \(interactive agents\).
- [Autonomous app flow](https://learn.microsoft.com/en-us/entra/agent-id/agent-autonomous-app-oauth-flow): App-only operations enable agent identities to act autonomously without user context.
- [Agent's user account flow](https://learn.microsoft.com/en-us/entra/agent-id/agent-user-oauth-flow): Agents operating on their own behalf using user principals created specifically for agents.

## Related content

- [Grant agents access to Microsoft 365 resources](https://learn.microsoft.com/en-us/entra/agent-id/grant-agent-access-microsoft-365) - admin-focused guidance on consent, manual authorization, and other authorization systems.
- [Agent identity token claims](https://learn.microsoft.com/en-us/entra/agent-id/agent-token-claims) - claims reference for tokens issued to agents.
