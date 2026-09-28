<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/deploy-azure-bot-service-manually -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Deploy your agent to Azure manually

Running a Microsoft 365 Agents SDK agent on Azure requires the following steps:

- [Create and configure an Agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart)
- [Provision an Azure Bot resource and configure authentication for the resource](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually)
- Deploy your agent to Azure
- Optionally, deploy your agent to Teams or Microsoft 365 Copilot

This document covers deploying an agent you created to Azure and Teams or Microsoft 365 Copilot.

If you didn't create an agent yet, start with [Quickstart: Create and test a basic agent using C#](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart-dotnet).

## Publish your agent to Azure as a web app

1. Deploy your agent code to Azure. An Agents SDK agent is a web application. To publish your agent, you can use the methods you'd normally use to deploy a web application to Azure:

   - Deploy as a ZIP package to an Azure App Service app
   - Visual Studio publish to an Azure App Service app or container
   - Other container deployments supported by Azure
   - Microsoft 365 Agents Toolkit deployment

Important

If you're using an Azure App Service app and either federated credentials or User-Assigned Managed Identity, you need to add that identity under **Settings** > **Identity**.

Once your agent code is deployed, it has a *base URL*, such as `example.azurewebsites.net`.

1. In Azure, go to your Azure Bot resource. Under **Configuration**, change the **Messaging endpoint** to `https://{yourwebsite}/api/messages`. Replace `{yourwebsite}` with your web app's base URL.

## Test in Web Chat

To see your message in web chat, select **Test in Web Chat** in your Azure Bot resource and send messages to your agent.

## Prepare your Teams and Microsoft 365 Copilot manifest

For Microsoft Teams and Microsoft 365 Copilot, you need to create and upload a *manifest*. It isn't possible to provide a manifest example that covers all Teams or Microsoft 365 Copilot needs. Teams features require specific manifest content.

These steps provide an overview of a basic "chat" style Teams agent.

1. Create an empty folder in your project.
2. Copy the contents of [Teams manifest files](https://github.com/microsoft/Agents/blob/main/samples/dotnet/quickstart/appManifest) into the folder.
3. In the folder, open `manifest.json` and make the following edits:

   - *Everywhere* you see the placeholder string `<<AAD_APP_CLIENT_ID>>`, replace it with the `ClientId` for your Azure Bot resource.
   - Replace `<<BOT_DOMAIN>>` with your agent base URL.
   - Zip up the contents of the folder to create a `manifest.zip` with the contents:

     - `manifest.json`
     - `outline.png`
     - `color.png`

## Deploy to Microsoft 365

1. Ensure that your Azure Bot resource has the **Microsoft Teams** channel added under **Channels**.
2. Navigate to the Microsoft Admin Portal \(MAC\).
3. Under **Settings** and **Integrated Apps,** select **Upload Custom App**.
4. Select the `manifest.zip` created in the previous section, and upload the file.

After a short period of time, the agent shows up in Microsoft Teams and Microsoft 365 Copilot.
