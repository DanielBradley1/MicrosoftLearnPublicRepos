<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/authentication-with-auth-sdk-sidecar -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Authentication with Microsoft Entra ID Auth SDK sidecar

Use the Microsoft Entra ID Auth SDK sidecar when your cloud agent isn't built with ASP.NET Core and Microsoft.Identity.Web. The sidecar runs next to the agent, holds the blueprint credential, acquires and caches tokens, and returns authorization headers or calls downstream APIs.

The agent communicates with the sidecar through `localhost` in a shared network namespace. Don't expose the sidecar endpoint publicly.

## Choose this integration

Use the sidecar when the agent needs to:

- Call an API as its Agent ID.
- Call an API as a signed-in user through On-Behalf-Of \(OBO\).
- Validate an incoming user token and read its claims.
- Change credential sources without changing agent code.

For ASP.NET Core agents, use the integrated Microsoft.Identity.Web guidance in this documentation instead.

## How the sidecar works

| Component | Responsibility |
| --- | --- |
| Upstream client | Signs in a user and sends an access token to the agent when user context is required. |
| Agent | Applies business logic and requests an authorization header or downstream call. |
| Sidecar | Validates inbound tokens, authenticates with the configured shared client ID and blueprint credential, and caches tokens. |
| Protected API | Validates the resulting access token and authorizes the request. |

For a cloud agent, the sidecar supports two token acquisition patterns:

- **App-only Agent ID:** The agent requests a token without an inbound user token.
- **Agent acting for a signed-in user:** The agent forwards the inbound user token and the sidecar performs OBO.

If you're building a platform that hosts separate agents for teams or customers, or your scenario needs an agent's dedicated user account, follow the [agent fleet tutorial](https://learn.microsoft.com/en-us/entra/agent-id/sidecar-fleet-provision-agent-identities).

The following diagram shows an agent and sidecar running in the same private environment. The agent requests an authorization header from the sidecar, which gets an access token from Microsoft Entra.

[![Diagram that shows an agent requesting an authorization header from a sidecar, which obtains an access token from Microsoft Entra ID.](https://learn.microsoft.com/en-us/entra/agent-id/media/configure-third-party-agents/sidecar-pattern-architecture.png)](https://learn.microsoft.com/en-us/entra/agent-id/media/configure-third-party-agents/sidecar-pattern-architecture.png#lightbox)

## Security boundary

Run the sidecar in the same network namespace as the agent, such as the same pod or container app. Production builds restrict callers to loopback; separate containers on a private bridge aren't sufficient. For Docker Compose, follow the [shared-network configuration](https://learn.microsoft.com/en-us/entra/agent-id/microsoft-entra-sdk-for-agent-identities#add-the-sidecar-container). Only trusted agent code should be able to call it. Use a managed identity and federated identity credential for hosted deployments. Use client secrets only for local development.

## Next steps

1. [Configure the Auth SDK sidecar](https://learn.microsoft.com/en-us/entra/agent-id/microsoft-entra-sdk-for-agent-identities).
2. [Run the sidecar locally](https://learn.microsoft.com/en-us/entra/agent-id/sidecar-local-development).
3. [Call a custom API as the agent](https://learn.microsoft.com/en-us/entra/agent-id/sidecar-call-custom-api-as-agent).

## Related content

- [Microsoft Entra ID Auth SDK sidecar source code](https://github.com/AzureAD/microsoft-identity-web/tree/master/src/Microsoft.Identity.Web.Sidecar)
- [Official Agent ID sidecar samples](https://github.com/microsoft/entra-agentid-samples/tree/dev/sidecar)
- [Microsoft Entra ID Auth SDK sidecar endpoint reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)
- [Choose an authentication protocol for an agent](https://learn.microsoft.com/en-us/entra/agent-id/agent-oauth-protocols)
