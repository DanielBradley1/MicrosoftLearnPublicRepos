<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/agent-autonomous-app-oauth-flow -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Agent autonomous app OAuth flow - App-only protocol

App-only operations enable agent identities to act autonomously without user context, using client credentials flows. The agent identity is both the actor and subject. An administrator grants the application permissions required for the operation.

The protocol below describes **multi-instance** Agent IDs, where the blueprint impersonates a child identity. A single-instance Agent ID instead requests a token directly with the shared client ID and a credential configured on the blueprint. It doesn't use the intermediate T1 token or `fmi_path`. For that request, see [Request an app-only token for a single-instance Agent ID](https://learn.microsoft.com/en-us/entra/agent-id/authenticate-single-instance-agent#request-an-app-only-token).

Agent identity blueprints can only impersonate their child agent identities. Only a single agent identity blueprint can impersonate an agent identity. An agent identity blueprint can impersonate many agent identities, but no agent identity can be owned by multiple blueprints. Agent identities are always single-tenant regardless of their parent Agent identity blueprint's tenancy model. Each agent identity operates within one tenant's security and policy boundaries.

Warning

Microsoft recommends using the approved SDKs like Microsoft.Identity.Web and Microsoft Entra ID Auth SDK \(sidecar\) libraries to implement these protocols. Manual implementation of these protocols is complex and error-prone, and using the SDKs helps ensure security and compliance with best practices.

## Managed identities integration

For Azure-hosted agents, prefer a managed identity when the hosting service provides one. Its token authenticates the parent blueprint through a configured federated identity credential; configuring the managed identity alone doesn't grant API access to the agent. A local developer's Azure CLI sign-in isn't a managed identity. For hosting requirements and local credential alternatives, see [Configure blueprint credentials](https://learn.microsoft.com/en-us/entra/agent-id/create-blueprint#configure-credentials-for-the-agent-identity-blueprint).

## Protocol steps

The following are the protocol steps.

![Diagram showing the illustration of autonomous app token acquisition flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-autonomous-app-oauth-flow/autonomous-app-flow.png)

1. Agent identity blueprint requests an exchange token T1. The agent identity blueprint presents its credentials that could be a secret, a certificate, or a managed identity token. Microsoft Entra ID returns the T1 to the agent identity blueprint. In this example we use a managed identity as Federated Identity Credential \(FIC\).

   Warning

   Client secrets shouldn't be used as client credentials in production environments for agent identity blueprints due to security risks. Instead, use more secure authentication methods such as [federated identity credentials \(FIC\) with managed identities](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity) or client certificates. These methods provide enhanced security by eliminating the need to store sensitive secrets directly within your application configuration.

   ```
   POST /oauth2/v2.0/token
   Content-Type: application/x-www-form-urlencoded

   client_id=AgentBlueprint
   &scope=api://AzureADTokenExchange/.default
   &fmi_path=AgentIdentity
   &client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
   &client_assertion=TUAMI
   &grant_type=client_credentials
   ```


   - `fmi_path`: The client ID \(app ID\) of the agent identity. This parameter tells Microsoft Entra ID which child agent identity the blueprint is impersonating during the token exchange.


   Where TUAMI is the managed identity token for user assigned managed identity \(UAMI\). This step returns T1. Where T1 is the token-exchange token for FIC.

2. Agent identity sends a token exchange request to Microsoft Entra ID. The request includes the token T1.

   ```
   POST /oauth2/v2.0/token
   Content-Type: application/x-www-form-urlencoded

   client_id=AgentIdentity
   &scope=https://resource.example.com/.default
   &client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
   &client_assertion={T1}
   &grant_type=client_credentials
   ```

3. Microsoft Entra ID issues an app-only resource access token \(TR\) to the agent identity after validating T1. T1's audience is the token-exchange resource requested in step 1, not the blueprint. Microsoft Entra ID validates that T1 is bound to the blueprint and that its subject resolves to the child agent identity performing the exchange. The resource token represents the agent identity, not the blueprint.

## Sequence diagram

The following is a sequence diagram for the app-only flow:

![Diagram showing the token sequence of autonomous app token acquisition flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-autonomous-app-oauth-flow/autonomous-app-flow-token-sequence.png)

## Related content

- [Oauth2.0 flows for agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-oauth-protocols)
- [On-behalf-of flow in agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-on-behalf-of-oauth-flow)
- [Agent's user account flow in agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-user-oauth-flow)
