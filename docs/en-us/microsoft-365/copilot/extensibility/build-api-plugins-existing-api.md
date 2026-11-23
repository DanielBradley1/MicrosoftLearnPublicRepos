<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-existing-api -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Build API plugins from an existing API for Microsoft 365 Copilot

Important

MCP and API plugins provide actions within [declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent). They're not standalone installable plugin packages: only the containing agent can access their functions and tools. For information about the package and action manifest relationship, see [Plugins and declarative agent actions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview#plugins-and-declarative-agent-actions).

Tip

**Recommended:** Start with [Work IQ Dev Tools](https://aka.ms/wiqd/docs) for supported pro-code declarative-agent and plugin scenarios. See the [WIQD quickstart](https://microsoft.github.io/wiqd/getting-started/quickstart/). Toolkit-based instructions remain available for existing projects and workflows that require them. Check [capability and target-experience support](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools) before choosing a tool: WIQD doesn't target custom engine agents.

[API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) let a declarative agent call your existing REST API. Use the [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) to create an agent project with an API action integration based on your API's [OpenAPI specification](https://www.openapis.org/what-is-openapi).

## Prerequisites

- Requirements specified in [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options)
- An existing REST API with an OpenAPI specification \(this walkthrough uses the [Budget Tracker sample API](https://github.com/microsoftgraph/msgraph-sample-copilot-plugin)\)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit)

Tip

For the best results, make sure that your OpenAPI specification follows the guidelines detailed in [How to make an OpenAPI document effective in extending Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/openapi-document-guidance).

To follow along with this guide, download the [Budget Tracker sample API](https://github.com/microsoftgraph/msgraph-sample-copilot-plugin) and configure it to run on your local development machine. Build the sample at least once to generate the **BudgetTracker.json** file for the API.

## Create the agent and API plugin

Note

The screenshots and user-interface references in this article use a release version of [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit). Prerelease versions might differ from the user interface shown.

The API plugin's configuration includes:

- The OpenAPI specification for the REST API.
- A [plugin manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4) that references the included OpenAPI specification and describes the available operations, authentication method, and response formats.

Include these files in the containing agent's app package alongside its app manifest, agent definition, and icons. The API plugin manifest isn't itself an installable package.

1. Open Visual Studio Code. If Agents Toolkit isn't already installed, see [Install Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/install-teams-toolkit) for installation instructions.
2. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
3. Select **Create a New Agent/App** in the Agents Toolkit task pane.

   ![A screenshot of the Agents Toolkit interface](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/create-plugin-toolkit.png)
4. Select **Declarative Agent**.
5. Select **Add an Action**, then select **Start with an OpenAPI Description Document**.
6. Select **Browse** and browse to the location of the OpenAPI specification from the Budget Tracker sample, located at **./openapi/BudgetTracker.json**.
7. Select all the operations to enable for the plugin.

   ![The Agents Toolkit UI to select operations](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/select-operations-toolkit.png)
8. Choose a location for the agent project.
9. Enter `Budget Tracker` as a name for the agent project.

When you complete these steps, Agents Toolkit generates the agent project and its API plugin configuration, and opens the project in a new Visual Studio Code window.

Note

Proof Key for Code Exchange \(PKCE\) is enabled by default. If your identity server doesn't support PKCE, disable it by adding the following line to **m365agents.yml** in the agent project.

```yml
isPKCEEnabled: false
```

## Provision and sideload the agent

Sideloading makes the containing agent and its API action available for development testing. It doesn't install the API plugin as an independent capability. This procedure isn't a general distribution method for a composed plugin package. For sharing and publishing routes, see [Choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish).

1. Open the agent project in Visual Studio Code.
2. Select the **Microsoft 365 Agents Toolkit** icon in the left-hand Activity Bar.
3. In the **Accounts** pane, select **Sign in to Microsoft 365**. \(If you're already signed in continue to the next step\).
4. Confirm that both **Custom App Upload Enabled** and **Copilot Access Enabled** display under your Microsoft 365 account. If they don't, check with your organization admin. See [Requirements for Copilot extensibility options](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#requirements-for-copilot-extensibility-options) for details.
5. In the **Lifecycle** pane, select **Provision**.
6. When asked to **Enter client id for OAuth registration...**, enter your **Plugin client ID**.
7. When asked to **Enter client secret for OAuth registration...**, enter your **Plugin client secret**.
8. Read the message in the dialog and select **Confirm** to continue.
9. Wait for the toolkit to report that is finished provisioning.

   ![The Agents Toolkit message confirming successful provisioning](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/provision-complete-toolkit.png)

Your agent is now available to test with your user account in Microsoft 365 Copilot in Microsoft Teams.

## Test the agent's API action

1. Open Teams in your browser and sign in with the Microsoft 365 account you used to sideload your agent.
2. Select **Chat** in the left-hand Activity Bar.
3. Select **Copilot** in the **Chat** pane.
4. Select **Budget Tracker** in the Agents list on the right-hand side. If the list isn't available, select the **Copilot chats and more** icon in the top right corner.

   ![A screenshot of the Agents list in Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/copilot-agents.png)
5. Ask a question about budgets. For example, try `How much is left in the Fourth Coffee lobby renovation budget?`. When prompted, choose **Always allow** or **Allow once** to proceed.
6. When asked to sign in, select **Sign in to Budget Tracker**.
