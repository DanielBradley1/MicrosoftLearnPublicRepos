<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/agent-autonomous-app-oauth-flow -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Agent autonomous app OAuth flow - App-only protocol

App-only operations enable agent identities to act autonomously without user context, using client credentials flows. The agent identity \(actor\) is used to obtain a token for itself \(subject\). To obtain this token, the agent identity blueprint impersonates the agent identity. Subjects use app-only access but are supposed to be only assigned the permissions necessary. Tenant administrators grant all permissions.

Agent identity blueprints can only impersonate their child agent identities. Only a single agent identity blueprint can impersonate an agent identity. An agent identity blueprint can impersonate many agent identities, but no agent identity can be owned by multiple blueprints. Agent identities are always single-tenant regardless of their parent Agent identity blueprint's tenancy model. Each agent identity operates within one tenant's security and policy boundaries.

Warning

Microsoft recommends using the approved SDKs like Microsoft.Identity.Web and Microsoft Entra ID Auth SDK \(sidecar\) libraries to implement these protocols. Manual implementation of these protocols is complex and error-prone, and using the SDKs helps ensure security and compliance with best practices.

## Managed identities integration

Managed identities are the preferred credential type. In this configuration, the managed identity token serves as the credential for the parent agent identity blueprint, while standard MSI protocols apply for credential acquisition. This integration allows the agent ID to receive the full benefits of MSI security and management, including automatic credential rotation and secure storage.

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

3. Microsoft Entra ID issues an app-only resource access token \(TR\) to the agent identity after validating T1. Microsoft Entra ID validates that T1 \(aud\) == Agent identity parent app == Agent identity blueprint

## Sequence diagram

The following is a sequence diagram for the app-only flow:

![Diagram showing the token sequence of autonomous app token acquisition flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-autonomous-app-oauth-flow/autonomous-app-flow-token-sequence.png)

## Related content

- [Oauth2.0 flows for agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-oauth-protocols)
- [On-behalf-of flow in agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-on-behalf-of-oauth-flow)
- [Agent's user account flow in agents](https://learn.microsoft.com/en-us/entra/agent-id/agent-user-oauth-flow)
