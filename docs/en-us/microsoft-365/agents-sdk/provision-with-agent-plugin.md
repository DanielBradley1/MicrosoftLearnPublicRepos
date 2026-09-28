<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-with-agent-plugin -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Provision Azure resources with an Agents SDK plugin

The Agents SDK plugin for provisioning gives your AI coding assistant guidance for creating the Azure resources that connect your agent to channels. The plugin supports .NET, JavaScript, and Python agents.

The plugin can help you:

- Create an Azure Bot resource and its identity resources.
- Choose client secret, user-assigned managed identity, or federated credentials for authentication.
- Add the Microsoft Teams channel.
- Set up an OAuth connection for user sign-in.
- Generate the connection configuration for your agent.

## Prerequisites

- An Azure subscription where you have permission to create resources.
- Microsoft Entra permissions to create or configure the identity resources that you choose.
- The [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).
- [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) or [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview).

The client secret workflow requires Bicep CLI 0.26.0 or later with the Microsoft Graph Bicep extension. Your account must have the Application Administrator or Global Administrator role for this workflow.

## Install the plugin

In GitHub Copilot CLI or Claude Code, add the Agents SDK plugin marketplace:

```console
/plugin marketplace add microsoft/Agents
```

Install the common plugin:

```console
/plugin install agents-sdk-common@microsoft-agents-sdk
```

The plugin includes the `agents-sdk-provision` skill. The skill activates automatically when you ask the assistant to provision Azure resources for an Agents SDK agent.

## Provision resources

1. Open your agent project in GitHub Copilot CLI or Claude Code.
2. Sign in to Azure CLI and select the subscription to use.

   ```azurecli
   az login
   az account set --subscription "<subscription-id>"
   ```

3. Choose an authentication type based on where your agent runs:
   | Authentication type | Use when |
   | --- | --- |
   | User-assigned managed identity | Your agent is hosted on Azure and doesn't need an app registration. |
   | Federated credentials | Your agent is hosted on Azure, needs an app registration, and shouldn't use a client secret. |
   | Client secret | Your agent runs locally or outside Azure. Store and rotate the secret securely. |
4. Ask the assistant to provision the resources that your agent needs. Include the target hosting environment, your preferred authentication type, and optional capabilities in the prompt. If you're unsure which authentication type to use, ask the assistant to recommend one. For example:

   ```text
   This agent will run in Azure App Service. Provision its Azure resources with federated credentials and add the Microsoft Teams channel.
   ```

5. Provide the resource names, Azure region, and other values that the assistant requests. Review the proposed commands and resources before approving them.
6. Add the generated connection configuration to your agent project. Keep client secrets in Azure Key Vault, environment secrets, or another secure secret store. Don't commit secrets to source control.

The plugin can also set up OAuth user sign-in connections and Teams single sign-on. Describe these requirements in your provisioning prompt.

## Provision resources manually

If you can't use an AI coding assistant plugin, [provision the Azure resources manually](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually).
