<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-new-api -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Build API plugins with a new API for Microsoft 365 Copilot

Important

Plugins are only supported as actions within [declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent). They are not enabled in Microsoft 365 Copilot.

[API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) connect a REST API to Microsoft 365 Copilot. You can use the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) to quickly generate a plugin and a corresponding REST API that you can use as a starting point for your plugin development.

- Requirements specified in [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit)
- [Node.js](https://nodejs.org/) 20.x or 22.x. To confirm your installed version, run `node --version`.

## Create the plugin and API

Note

The screenshots and references to user interface of the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) in this document were generated using the latest **Release** version, 6.0. Pre-Release versions of Agents Toolkit may differ from the user interface in this document.

1. Open Visual Studio Code. If Agents Toolkit isn't already installed, see [Install Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/install-teams-toolkit) for installation instructions.
2. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
3. Select **Create a New Agent/App** in the Agents Toolkit task pane.

   ![A screenshot of the Agents Toolkit interface](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/create-plugin-ttk.png)
4. Select **Declarative Agent**.
5. Select **Add an Action**, then select **Start with a New API**.
6. Select **OAuth** for the **Authentication Type**.
7. Select your preferred programming language: JavaScript or TypeScript. This guide assumes TypeScript.
8. Choose a location for the API plugin project.
9. Enter `Repairs Agent` as a name for your plugin project.

Once you complete these steps, Agents Toolkit generates the required files for the plugin and opens a new Visual Studio Code window with the plugin project loaded. For details on the project, see the **README.md** file in the generated project's root directory.

## Run the plugin

1. In the Visual Studio Code window with the plugin project loaded, select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
2. In the **Accounts** pane, select **Sign in to Microsoft 365**. \(If you're already signed in continue to the next step\).
3. Confirm that both **Custom App Upload Enabled** and **Copilot Access Enabled** display under your Microsoft 365 account. If they don't, check with your organization admin. See [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options) for details.
4. Select the **Run and Debug** icon in the left-hand Activity Bar.
5. Select either **Debug in Copilot \(Edge\)** or **Debug in Copilot \(Chrome\)**, then press **F5** to start debugging.

Agents Toolkit builds the project, creates the plugin package, and sideloads it for your user account. Once that is done, a new browser window opens to the Microsoft Teams app.

## Test the plugin

1. In Microsoft Teams in your browser, select **Copilot**.
2. Select **Repairs Agentlocal** in the Agents list on the right-hand side. If the list isn't available, select the **Copilot chats and more** icon in the top right corner.
3. Send a message to Copilot about repairs. For example, try `Which repairs are assigned to Karin?`.

At this point, the plugin is running locally on your development machine without authentication. In order to add authentication, deploy the solution to Azure.

## Deploy to Azure and enable authentication

1. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
2. In the **Lifecycle** pane, select **Provision**.
3. When asked for a resource group name, either accept the default or change it as desired and press **Enter**.
4. Select a location for the resource group.
5. Review the message in the dialog. If everything looks correct, select **Provision** to continue.
6. Wait for the provisioning steps to complete, then select **Deploy** in the **Lifecycle** pane.

Once you complete these steps, the plugin is deployed as an Azure Function with authentication.

## Test the plugin with authentication

1. In Microsoft Teams in your browser, select **Copilot**.
2. Select **Repairs Agentdev** in the Agents list on the right-hand side.
3. Send a message to Copilot about repairs. For example, try `Which repairs are assigned to Issac?`.
