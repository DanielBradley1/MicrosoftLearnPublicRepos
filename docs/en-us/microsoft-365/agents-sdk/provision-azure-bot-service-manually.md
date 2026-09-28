<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Provision Azure resources for your agent manually

Provisioning creates the Azure resources that connect your agent to channels and host its production dependencies. It's separate from configuring your agent code.

To run an agent through Azure Bot Service:

1. Provision an Azure Bot resource and its identity resources.
2. [Configure the agent connection](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal) to match the Azure Bot identity.
3. Test the connection locally or deploy the agent code to Azure.

This article covers the first step. The instructions apply regardless of which language you use for the Agents SDK agent.

## Provision Azure resources based on authentication type

The Azure AI Bot Service supports multiple authentication types. The details of how to configure each authentication type in your Azure Bot resource and in your agent code are covered in the following articles. Consider the security implications of each authentication type when making your choice.

- [Provision agent resources in Azure Bot Service using client secret](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-single-secret): Use a client secret for local testing if your tenant allows secrets.
- [Provision agent resources in Azure Bot Service using User-Assigned Managed Identity](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-managed-identity): For better security, use User-Assigned Managed Identity.
- [Provision agent resources in Azure Bot Service using federated credentials](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-federated-credentials): If you're creating a Teams agent that requires single sign-on \(SSO\), select federated credentials.
- [Add user authorization using federated identity credential](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-user-authorization-federated-credentials)

Provision storage accounts, databases, and other service dependencies separately based on the capabilities your agent uses. For storage provider options, see [Use storage in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/storage).

## Next steps

- [Configure the connection between your agent and Azure Bot Service](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal)
- [Test a local agent with a dev tunnel](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/test-with-dev-tunnel)
- [Deploy your agent to Azure](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/deploy-azure-bot-service-manually)
