<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-managed-identity -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Provision agent resources in Azure Bot Service using User-Assigned Managed Identity

This article shows how to register an agent with Azure AI Bot Service using User-Assigned Managed Identity.

Note

User-Assigned Managed Identity doesn't work for local debugging via devtunnels.

## Create an Azure Bot resource

Create an Azure Bot resource. This allows you to register your agent with the Azure AI Bot Service.

1. Go to the Azure portal.
2. In the right pane, select **Create a resource**.
3. Find and select the **Azure Bot** card.

   ![Screenshot of the Azure Bot resource card in the Azure portal marketplace.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-resource.png)
4. Select **Create**.
5. Enter values in the required fields and review and update settings.

   1. Provide information under **Project details**. Select whether your agent has global or local data residency. Currently, the local data residency feature is available for resources in the "westeurope" and "centralindia" region. For more information, see [Regionalization in Azure AI Bot Service](https://learn.microsoft.com/en-us/azure/bot-service/bot-builder-concept-regionalization?view=azure-bot-service-4.0&preserve-view=true).


   ![Screenshot of the Azure Bot project details configuration page showing subscription, resource group, and region settings.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-project-details.png)


   1. Provide information under **Microsoft App ID**. For **Type of App**, select User-Assigned Managed Identity. Select whether to create a new identity or use an existing one.


   ![Screenshot of the Azure Bot Microsoft App ID configuration section with identity management options.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-ms-app-id.png)

6. Select **Review + create**.
7. If the validation passes, select **Create**.
8. Once the Azure Bot resource is done deploying, select **Go to resource**. You should see the agent and related resources listed in the resource group you selected.
9. If this is a Teams or Microsoft 365 agent:

   1. Select **Settings** on the left sidebar, then **Channels**.
   2. Select **Microsoft Teams** from the list and choose appropriate options.

Important

Store the **ClientID** of the User Managed Identity. You need the information later when configuring your agent configuration.

## Next Steps

- [Configure authentication in a .NET agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options#user-assigned-managed-identity)
- [Configure authentication in a JavaScript agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-authentication-for-javascript#single-tenant-with-user-assigned-managed-identity)
- [Configure authentication in a Python agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-authentication-for-python#user-assigned-managed-identity)
