<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/agent-user-oauth-flow -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Agent's user account impersonation protocol

Agent's user account impersonation enables agent identities to operate with user context through an agent's user account, combining user permissions with autonomous operation. In this scenario, an agent identity blueprint \(actor 1\) impersonates an agent identity \(actor 2\) that impersonates an agent's user account \(subject\) using FIC. Access is scoped to delegations assigned to the agent identity. The agent's user account can be impersonated only by a single agent identity.

Warning

Microsoft recommends using the approved SDKs like Microsoft.Identity.Web and Microsoft Entra ID Auth SDK \(sidecar\) libraries to implement these protocols. Manual implementation of these protocols is complex and error-prone, and using the SDKs helps ensure security and compliance with best practices.

## Managed identities integration

Managed identities are the preferred credential type. In this configuration, the managed identity token serves as the credential for the parent agent identity blueprint, while standard MSI protocols apply for credential acquisition. This integration allows the agent ID to receive the full benefits of MSI security and management, including automatic credential rotation and secure storage.

## Protocol steps

Then following are the protocol steps.

![Diagram showing the illustration of agent's user account token acquisition flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-user-oauth-flow/agent-user-flow.png)

1. The agent identity blueprint requests an exchange token \(T1\) that it uses for agent identity impersonation. The agent identity blueprint presents client credentials that could be a secret, a certificate, or a managed identity token used as an FIC.

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


   Where TUAMI is the MSI token for user assigned managed identity \(UAMI\). This returns token T1.

2. The agent identity requests a token \(T2\) that it uses for agent's user account impersonation. The agent identity presents T1 as its client assertion. Microsoft Entra ID returns T2 to the agent identity after validating that T1 \(aud\) == Agent identity parent app == Agent identity blueprint.​

   ```
   POST /oauth2/v2.0/token
   Content-Type: application/x-www-form-urlencoded

   client_id=AgentIdentity
   &scope=api://AzureADTokenExchange/.default
   &client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
   &client_assertion={T1}
   &grant_type=client_credentials
   ```


   This returns token T2.

3. The agent identity then sends an OBO token exchange request to Microsoft Entra ID, including both T1 and T2. Microsoft Entra ID validates that T2 \(aud\) == agent identity.

   ```
   POST /oauth2/v2.0/token
   Content-Type: application/x-www-form-urlencoded

   client_id=AgentIdentity
   &scope=https://resource.example.com/scope1
   &client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
   &client_assertion={T1}
   &user_federated_identity_credential={T2}
   &username=agentuser@contoso.com
   &grant_type=user_fic
   &requested_token_use=on_behalf_of
   ```

4. Microsoft Entra ID then issues the resource token.

### Sequence diagram

The following sequence diagram shows the agent's user account impersonation flow

![Diagram showing the token sequence of agent's user account token acquisition flow for agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/agent-user-oauth-flow/agent-user-flow-token-sequence.png)

Agent's user account impersonation requires credential chaining that follows the pattern agent identity blueprint → Agent identity → Agent's user account. Each step in this chain uses the token from the previous step as a credential, creating a secure delegation pathway. The same client ID must be used for both phases to prevent privilege escalation attacks.
