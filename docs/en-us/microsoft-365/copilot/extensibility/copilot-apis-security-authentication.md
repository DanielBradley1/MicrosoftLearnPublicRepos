<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-security-authentication -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Security and authentication for Microsoft 365 Copilot APIs

The Microsoft 365 Copilot APIs use the same authentication and authorization model as other Microsoft Graph APIs. When you build a [custom engine agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent) or integrate Copilot capabilities into your own application, your organization's existing security controls are enforced by default. You don't need to build a separate compliance or access-control layer on top of the APIs.

This article describes how the Copilot APIs authenticate requests, which organizational policies are automatically enforced, and how secure grounding works with the Microsoft 365 knowledge index.

## Authentication through Microsoft Entra ID

The permission types each Copilot API supports vary by API, so check the reference documentation for the specific API you call. The [Retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview), for example, supports delegated permissions only. With delegated permissions, Entra ID authenticates both the calling application and the signed-in user, and the API enforces the signed-in user's permissions on every request.

The APIs are available as standard REST endpoints under the Microsoft Graph namespace:

- `https://graph.microsoft.com/v1.0/copilot`
- `https://graph.microsoft.com/beta/copilot`

Because the Copilot APIs follow the same authentication flow as other Microsoft Graph APIs, you can use familiar libraries and patterns to acquire tokens and call the endpoints.

For details about how to acquire authentication tokens and authorize your application, see [Authentication and authorization basics for Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

## Organizational policies enforced by default

When your application calls a Copilot API, your organization's existing policies automatically apply to the request. You don't need to configure additional enforcement as a developer.

### Identity and conditional access

Because Copilot APIs are Microsoft Graph endpoints, any Conditional Access policies already configured in your organization automatically apply to Copilot API requests. If your organization requires multifactor authentication, device compliance, or location-based restrictions for access to Microsoft 365 resources, those requirements also apply when users interact with the Copilot APIs through your application.

### Sensitivity labels

The Copilot APIs respect sensitivity labels applied to Microsoft 365 content when accessing that content. If a document, email, or other item has a sensitivity label that restricts access or applies encryption, the API honors those restrictions and returns content only in accordance with the label's protection settings. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview) and [sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels).

### Permission trimming

The API trims results to include only the content that the signed-in user has permission to access. If the user doesn't have access to a file, meeting transcript, or other resource, that content doesn't appear in API responses - even if the content is otherwise relevant to the request. This behavior is consistent with how permissions work across Microsoft Graph. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview).

## Secure grounding with the Microsoft 365 knowledge index

When the Copilot APIs access the Microsoft 365 knowledge index to ground responses in organizational data, that access is secure by default. The knowledge index inherits the same governance, compliance, audit, logging, monitoring, and policy enforcement controls that protect Microsoft 365 content elsewhere in the platform.

This means your application benefits from enterprise-grade security when it uses the Copilot APIs to retrieve or reason over organizational knowledge, without requiring you to replicate those controls in your own infrastructure. For more information, see [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview).

## Compliance, audit, and logging

Compliance controls, audit logging, and monitoring apply to Copilot API interactions. These controls help your organization meet regulatory requirements and maintain visibility into how AI capabilities are used. Audit logging for Copilot and AI interactions is available through [Microsoft Purview](https://learn.microsoft.com/en-us/purview/audit-copilot).

For detailed information about governance controls, data loss prevention, retention policies, and admin settings for agents, see [Data, privacy, and security for Microsoft 365 Copilot extensibility](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/data-privacy-security).

## Related content

- [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview)
- [Authentication and authorization basics for Microsoft Graph](https://learn.microsoft.com/en-us/graph/auth/auth-concepts)
- [Data, privacy, and security for Microsoft 365 Copilot extensibility](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/data-privacy-security)
- [Custom engine agents for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent)
- [Configure authentication for MCP and API plugins in agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication) — covers a different scenario: how an agent's MCP or API plugin \(including Microsoft Entra SSO\) authenticates to its own backend, rather than how your app authenticates to call the Copilot APIs described here.
