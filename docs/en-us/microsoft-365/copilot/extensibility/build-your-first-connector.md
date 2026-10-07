<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-your-first-connector -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Build your first synced Copilot connector with Microsoft 365 Agents Toolkit

[Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-copilot-connector) enable you to ingest your line-of-business data into Microsoft Graph to make it available to Microsoft 365 Copilot. When your data is ingested, Copilot can reason over the data and use it to respond to user prompts.

This walkthrough creates a synced Copilot connector that can provide external data access as a component of a Microsoft 365 Copilot plugin. It doesn't create or package a complete plugin.

The [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) includes a template that you can use to build Copilot connectors. The Copilot connector template is designed to help you build connectors quickly by using the Copilot connector API in Microsoft Graph. The template scaffolds a connector that pulls data from the GitHub API into Microsoft Graph. After you build your connector, you can run it locally via the F5 experience or deploy it via Azure Functions.

This article provides a walkthrough of the steps to build your first Copilot connector by using the Microsoft 365 Agents Toolkit in Visual Studio Code.

Before you begin, confirm that your component plan identifies a synced connector as the appropriate model and that Microsoft 365 Agents Toolkit supports your target experience. For planning guidance, see [Connectors as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-connectors).

Note

This walkthrough builds a synced connector. It doesn't build a federated connector, an MCP plugin, an MCP server, or an agent connector.

## What you build

In this walkthrough, Agents Toolkit scaffolds a synced connector implementation that retrieves GitHub issues. When you run the project, the toolkit provisions a Microsoft Entra application, creates an external connection and schema in Microsoft Graph, and ingests external items from the configured GitHub repository.

The connector is one component of your solution. Complete any additional plugin components separately, and then integrate and test the components together.

## Prerequisites

The following prerequisites are required to complete the steps in this article:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)
- [Azure Functions Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions)
- [Node.js](https://nodejs.org/), supported versions: 18, 20, 22
- A [Microsoft 365 Copilot license](https://www.microsoft.com/microsoft-365/copilot/enterprise) or a [Microsoft 365 Developer tenant](https://developer.microsoft.com/microsoft-365/dev-program) with [uploading custom apps enabled](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/prerequisites#prepare-a-developer-tenant-for-testing).

  Note

  To test your connector in Microsoft 365 Copilot Chat, you need a Microsoft 365 Copilot license.
- You must have the ability to admin consent in Microsoft Entra admin center. You must be or complete this step as a Global administrator. See [Grant tenant-wide admin consent to an application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/grant-admin-consent#prerequisites) for the required roles.
- Your user must have the role Search Administrator, Cloud Application Developer to see the connector in the Microsoft 365 admin center.

## Build your first custom connector

Use the following steps to build your first connector.

1. In the sidebar in Visual Studio Code, choose the **Microsoft 365 Agents Toolkit > Create a New Agent/App**.

   ![Microsoft 365 Agents Toolkit menu](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/create-new-app.png)
2. Select **Copilot connector**.

   ![Project picker](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/select-copilot-connector.png)
3. Enter `Github Issues` as the connector name.
4. Create a tenant-wide unique ID for the connector. For details about the requirements for the connector ID, see the [id property of the externalConnection resource](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection#properties).
5. Select **Default folder** to store your project root folder in the default location.
6. Configure the repository you want to pull issues from by using the `CONNECTOR_REPOS` field from in the `.env.local` file.

   ![env-local-file](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/env-local.png)
7. Press **F5** to run the connector locally. The toolkit creates a Microsoft Entra app for your connector and starts the provisioning process.
8. Follow the link in the terminal to the Microsoft Entra admin center and select **Grant admin consent**.

   Note

   To complete this step, you must be a Global Admin in your organization.

   ![The Grant admin consent button in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/admin-consent.png)
9. The app creates the connection, registers the schema, and then does a full crawl to ingest items.

   Note

   Registering the schema might take up to 10 mins.
10. After the full crawl completes, in the Microsoft 365 admin center:

    - In the left pane, go to **Settings** > **Search & Intelligence** > **Data sources**.
    - Find your Connection ID.
    - Choose **Include connector results**.

      ![The Include connector results button in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/include-connector-results.png)

      Note

      To complete this step, you must be a Search Admin. This step enables results from the connector to be used by Microsoft 365 Copilot Chat. If you are only going to use this connector as a [knowledge source for a declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#copilot-connectors), this step isn't necessary.


    Tip


    If you need to look up the Connection ID programmatically instead of in the admin center, you can [query your existing connectors in Graph Explorer](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids#copilot-connectors) by using the `ExternalConnection.Read.All` scope.

11. To verify that the items were indexed, choose the relevant connector name. Check the **Items indexed** field to see how many issues were indexed.

    ![Github issues connector with 11 items indexed displayed](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/items-indexed.png)
12. Open Microsoft 365 Copilot Chat and test a sample prompt such as "What are the two latest GitHub Issues?". Notice the external item citations at the bottom of the page. These citations are the data from your Copilot connector.

    ![M365 Copilot Output with Github issues](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/atk-copilot-connectors/copilot-output.png)

This test confirms that the connector works independently. It doesn't validate a complete plugin package or confirm that the connector works with other plugin components.

## Customize the template for your data source

To customize this template for your custom data, you can update the content of the following folders:

- `src/custom`: Contains custom code to gather and transform data to be ingested into Microsoft Graph. Although the example uses the GitHub issues API, you can replace it with any other API.
- `src/references`: Includes the schema definition of the connector. Adjust it to match the data and metadata you want to ingest.
- `src/models`: Contains the model definition for an internal representation of the data and configuration. Both models can be customized to fit your needs.

In addition to these folders, you can customize other parts of the code, depending on the scenario. You can search the code for comments starting with the `[Customization point]` string. These comments indicate areas for potential customization.

## Next step

Record the connection ID, schema, environment, permissions, test evidence, and connector owner in your implementation record. If your plugin includes other components, build them before you [integrate and test your plugin components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components).

## Related content

- [Connectors as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-connectors)
- [Build or reuse connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-connectors)
- [Integrate and test your plugin components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components)
- [Package a plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/package-plugin)
- [Copilot connectors API](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-api-overview?context=%2Fmicrosoft-365-copilot%2Fextensibility%2Fcontext)
- [Microsoft 365 Agents Toolkit overview](https://aka.ms/M365AgentsToolkit)
- [Copilot connector samples](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-copilot-connector#microsoft-365-copilot-connector-samples)
- [Community samples](https://github.com/pnp/graph-connectors-samples)
- [Find your connector's ID by querying connectors in Graph Explorer \(ExternalConnection.Read.All\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids#copilot-connectors)
