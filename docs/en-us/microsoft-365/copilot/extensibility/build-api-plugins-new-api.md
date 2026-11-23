<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-new-api -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Build API plugins with a new API for Microsoft 365 Copilot

Important

MCP and API plugins provide actions within [declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent). They're not standalone installable plugin packages: only the containing agent can access their functions and tools. For information about the package and action manifest relationship, see [Plugins and declarative agent actions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview#plugins-and-declarative-agent-actions).

Tip

**Recommended:** Start with [Work IQ Dev Tools](https://aka.ms/wiqd/docs) for supported pro-code declarative-agent and plugin scenarios. See the [WIQD quickstart](https://microsoft.github.io/wiqd/getting-started/quickstart/). Toolkit-based instructions remain available for existing projects and workflows that require them. Check [capability and target-experience support](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools) before choosing a tool: WIQD doesn't target custom engine agents.

[API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) let a declarative agent call a REST API. Use the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) to generate an agent project, an API plugin manifest, and a REST API implementation as a starting point.

- Requirements specified in [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit)
- [Node.js](https://nodejs.org/) 20.x or 22.x. To confirm your installed version, run `node --version`.

## Create the agent and API

Note

The screenshots and user-interface references in this article use a release version of [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit). Prerelease versions might differ from the user interface shown.

1. Open Visual Studio Code. If Agents Toolkit isn't already installed, see [Install Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/install-teams-toolkit) for installation instructions.
2. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
3. Select **Create a New Agent/App** in the Agents Toolkit task pane.

   ![A screenshot of the Agents Toolkit interface](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/create-plugin-toolkit.png)
4. Select **Declarative Agent**.
5. Select **Add an Action**, then select **Start with a New API**.
6. Select **OAuth** for the **Authentication Type**.
7. Select your preferred programming language: JavaScript or TypeScript. This guide assumes TypeScript.
8. Choose a location for the agent project.
9. Enter `Repairs Agent` as a name for your agent project.

When you complete these steps, Agents Toolkit generates the agent and API project files, including the API plugin manifest, and opens the project in a new Visual Studio Code window. For details, see the **README.md** file in the generated project's root directory.

## Run the API and sideload the agent

1. In the Visual Studio Code window with the agent project loaded, select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
2. In the **Accounts** pane, select **Sign in to Microsoft 365**. \(If you're already signed in continue to the next step\).
3. Confirm that both **Custom App Upload Enabled** and **Copilot Access Enabled** display under your Microsoft 365 account. If they don't, check with your organization admin. See [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options) for details.
4. Select the **Run and Debug** icon in the left-hand Activity Bar.
5. Select either **Debug in Copilot \(Edge\)** or **Debug in Copilot \(Chrome\)**, then press **F5** to start debugging.

Agents Toolkit builds the project, creates an app package containing the agent and its API plugin configuration, and sideloads the agent for your user account. It also starts the API locally. A new browser window opens to the Microsoft Teams app.

## Test the agent's API action

1. In Microsoft Teams in your browser, select **Copilot**.
2. Select **Repairs Agentlocal** in the Agents list on the right-hand side. If the list isn't available, select the **Copilot chats and more** icon in the top right corner.
3. Send a message to Copilot about repairs. For example, try `Which repairs are assigned to Karin?`.

At this point, the REST API is running locally on your development machine without authentication. To add authentication, deploy the API to Azure.

## Deploy to Azure and enable authentication

1. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
2. In the **Lifecycle** pane, select **Provision**.
3. When asked for a resource group name, either accept the default or change it as desired and press **Enter**.
4. Select a location for the resource group.
5. Review the message in the dialog. If everything looks correct, select **Provision** to continue.
6. Wait for the provisioning steps to complete, then select **Deploy** in the **Lifecycle** pane.

When you complete these steps, you deploy the REST API as an Azure Function with authentication. The agent calls that hosted API through its API plugin configuration.

## Test the agent with the authenticated API

1. In Microsoft Teams in your browser, select **Copilot**.
2. Select **Repairs Agentdev** in the Agents list on the right-hand side.
3. Send a message to Copilot about repairs. For example, try `Which repairs are assigned to Issac?`.
