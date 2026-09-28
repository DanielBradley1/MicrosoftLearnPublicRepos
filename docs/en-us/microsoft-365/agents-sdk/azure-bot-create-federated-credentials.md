<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-create-federated-credentials -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Provision agent resources in Azure Bot Service using federated credentials

This article shows how to register an agent with Azure AI Bot Service using federated credentials.

Note

Federated credentials doesn't work for local debugging via dev tunnels.

## Create a User-Assigned Managed Identity

Create a User-Assigned Managed Identity. This identity is used as the identity for the Azure Bot resource and is associated with the app registration using federated credentials. This allows the bot to authenticate using its managed identity when deployed to Azure, without needing to manage secrets.

1. Go to the Azure portal.
2. Create a User-Assigned Managed Identity:

   1. In the right pane, find/select **Create a resource** and select **User Assigned Managed Identity**.

      ![Screenshot of creating a User Assigned Managed Identity resource in the Azure portal.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/create-user-managed-identity.png)
   2. Select **Create** and supply the required information.

      ![Screenshot of the User Assigned Managed Identity details form with required fields.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/user-assigned-identity-details.png)
   3. Complete creation by selecting **Create**. When you're done, select **Go to resource**.
   4. Record the **ClientId**. You use this later when setting up Federated Credentials on the app registration. This is also used when configuring the Agent settings, and is the `FederatedClientId` setting.

## Create the Azure Bot resource

1. In the right pane, select **Create a resource**.
2. Find and select the **Azure Bot** card.

   ![Screenshot of the Azure Bot resource card in the Azure portal marketplace.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-resource.png)
3. Select **Create**.
4. Enter values in the required fields and review and update settings.

   1. Provide information under Project details. Select whether your agent has global or local data residency. Currently, the local data residency feature is available for resources in the "westeurope" and "centralindia" region. For more information, see [Regionalization in Azure AI Bot Service](https://learn.microsoft.com/en-us/azure/bot-service/bot-builder-concept-regionalization?view=azure-bot-service-4.0&preserve-view=true).


   ![Screenshot of the Azure Bot project details configuration page showing subscription, resource group, and region settings.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-project-details.png)


   1. Provide information under Microsoft App ID. Select how your agent identity is managed in Azure and whether to create a new identity or use an existing one.


   ![Screenshot of the Azure Bot Microsoft App ID configuration section with identity management options.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-ms-app-id-single.png)

5. Select **Review + create**.
6. If the validation passes, select **Create**.

## Configure authentication for your Azure Bot resource using federated credentials

1. Once the Azure Bot resource is done deploying, select **Go to resource**. You should see the agent and related resources listed in the resource group you selected.
2. If this is a Teams or Microsoft 365 agent:

   1. Select **Settings**, then select **Channels**.
   2. Select **Microsoft Teams** from the list and choose appropriate options.

3. Select **Settings**, then **Configuration**.
4. Select **Manage Password** next to **Microsoft App ID**.

   ![Screenshot of the Azure Bot configuration page showing the Manage Password option next to Microsoft App ID.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/azure-bot-configuration-single.png)
5. On the **Overview** pane, record the **Application \(client\) ID** and **Directory \(tenant\) ID**

   - This is used when configuring the agent settings, and is the `ClientId` and `TenantId` settings.

6. Select **Certificates & secrets**, then select **Client secrets**. If there's a secret listed, you can delete the secret so that it's not used for authentication. The federated credential you set up in the next steps are used for authentication instead of a client secret.
7. Select **Federated credentials**.
8. Select **Add credential**.
9. Set credential properties.

   ![Screenshot of the Add Federated Credential dialog with managed identity configuration options.](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/provision-azurebot/add-federated-managed-identity.png)

   1. **Federated credential scenario**: **Managed Identity**.
   2. Select **Select a managed identity** and select the User-Assigned Managed Identity you created previously.
   3. Set the **Name**, for example, "agent."
   4. When you're done, select **Add**.

Important

Store the **ClientId**, **TenantId** from the Azure Bot resource, and store the **ClientId** from the Managed Identity. You need the information later when configuring your agent configuration.

## Next Steps

- [Add user authorization using federated identity credential](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-user-authorization-federated-credentials)
- [Configure authentication in a .NET agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options#federated-credentials)
- [Configure authentication in a JavaScript agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-authentication-for-javascript#single-tenant-with-federated-identity-credential)
