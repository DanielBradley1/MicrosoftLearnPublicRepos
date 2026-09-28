<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-single-secret -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Provision agent resources in Azure Bot Service using client secret

This article shows how to register an agent with Azure AI Bot Service using Client Secrets.

## Create an Azure Bot resource

Create the Azure Bot resource. This allows you to register your agent with the Azure AI Bot Service.

1. Go to the Azure portal.
2. In the right pane, select **Create a resource**.
3. Find and select the **Azure Bot** card.

   ![Screenshot of the Azure Bot resource card in the Azure portal marketplace.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-resource.png)
4. Select **Create**.
5. Enter values in the required fields and review and update settings.

   a. Provide information under Project details. Select whether your agent has global or local data residency. Currently, the local data residency feature is available for resources in the `westeurope` and `centralindia` region. Learn more in [Regionalization in Azure AI Bot Service](https://learn.microsoft.com/en-us/azure/bot-service/bot-builder-concept-regionalization?view=azure-bot-service-4.0&preserve-view=true).

   ![Screenshot of the Azure Bot project details configuration page showing subscription, resource group, and region settings.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-project-details.png)

   b. Provide information under Microsoft App ID. Select how your agent identity is managed in Azure and whether to create a new identity or use an existing one.

   ![Screenshot of the Azure Bot Microsoft App ID configuration section with identity management options.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-ms-app-id-single.png)
6. Select **Review + create**.
7. If the validation passes, select **Create**.

## Configure authentication for your Azure Bot resource using client secrets

1. Once the Azure Bot resource is done deploying, select **Go to resource**. You should see the agent and related resources listed in the resource group you selected.
2. If this is a Teams or Microsoft 365 agent:

   1. Select **Settings** on the left sidebar, then **Channels**.
   2. Select **Microsoft Teams** from the list and select appropriate options.

3. Select **Settings**, then **Configuration**.
4. Select **Manage Password** next to **Microsoft App ID**.

   ![Screenshot of the Azure Bot configuration page showing the Manage Password option next to Microsoft App ID.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-configuration-single.png)
5. On the **Overview** pane, record the **Application \(client\) ID** and **Directory \(tenant\) ID**.
6. Select **Certificates & secrets** > **Client secrets**.
7. Create a new secret by selecting **New client secret**.

Important

Store the new secret and store, **ClientId**, and **TenantId**. You need the information later when configuring your agent configuration.

## Next Steps

- [Configure authentication in a .NET agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options#single-tenant-with-client-secret)
- [Configure authentication in a JavaScript agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-authentication-for-javascript#single-tenant-with-client-secret)
- [Configure authentication in a Python agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-authentication-for-python#single-tenant-with-client-secret)
