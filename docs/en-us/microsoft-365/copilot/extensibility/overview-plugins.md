<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# MCP and API plugins for declarative agents

MCP and API plugins are custom actions that enable declarative agents in Microsoft 365 Copilot to interact with [Model Context Protocol \(MCP\)](https://modelcontextprotocol.io/) servers or REST APIs that have an [OpenAPI description](https://www.openapis.org/what-is-openapi). By using one of these plugins, users can ask a declarative agent to query an MCP server or REST API for information and, when supported, create, update, and delete data and objects through natural language prompts.

This article uses *plugin* for the technical MCP or API custom action used by a declarative agent. For the customer-facing plugin product, package, registry, and lifecycle, see [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview).

Important

This article uses *plugin* only for MCP and API actions in declarative agents. Package, publishing, and governance requirements vary by route.

Important

MCP and API plugins are supported as actions within [declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent). They aren't enabled as standalone experiences in Microsoft 365 Copilot.

A plugin provides a plugin manifest that Copilot uses to learn the capabilities of the plugin's MCP server or API. Copilot can then decide when an installed and enabled plugin is suited to answer any given prompt. To learn more about the manifest file that a plugin requires, see [Plugin manifest schema for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4).

## How Copilot discovers MCP server tools

For plugins based on an MCP server, Copilot resolves the plugin's tools dynamically at runtime by default, directly from the MCP server. Dynamic tool discovery means you get the latest tools the MCP server exposes without waiting for the agent to be repackaged and republished. When building the agent, a developer can optionally pin a fixed set of tools in the plugin manifest instead. REST API plugins always use the tools defined in the plugin manifest. For more information, see [Build plugins from an MCP server for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-mcp-plugins) and [Dynamic tool discovery for MCP plugins in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery).

This default applies to plugins only. It doesn't extend to agent connectors, which register an MCP server through the `agentConnectors` node in the Microsoft 365 app manifest rather than through a plugin manifest. For agent connectors, dynamic tool discovery requires app manifest version 1.29 or later *and* a host that permits it. For more information, see [Register MCP servers as agent connectors](https://learn.microsoft.com/en-us/microsoftteams/platform/m365-apps/agent-connectors).

## Plugin example

- [MCP Server](#tabpanel_1_mcp)
- [REST API](#tabpanel_1_rest)

Consider a budgets MCP server that allows for querying and creating budgets, charging expenses, or adding funds to existing budgets. The prompt "How much is left in the Contoso travel budget" could trigger a budget plugin, invoking the `get-budgets` tool.

```http
POST /mcp
Content-Type: application/json

{
  "method": "tools/call",
  "params": {
    "name": "get-budgets",
    "arguments": {
      "budgetName": "contoso travel"
    }
  }
}
```

Copilot uses the response from the tool result to generate its response: "The Contoso travel budget currently has $5,000 in available funds. If you need to allocate funds to specific categories or track expenses, I can assist you with that as well. Just let me know how I can help!"

The prompt "Charge $500 to the Contoso travel budget for Megan's airline ticket" could be translated to the following MCP tool call.

```http
POST /mcp
Content-Type: application/json

{
  "method": "tools/call",
  "params": {
    "name": "charge-budget",
    "arguments": {
      "budgetName": "contoso travel",
      "amount": 500,
      "description": "Megan's airline ticket"
    }
  }
}
```

Copilot responds to the user by using the information returned: "The charge of $500 for Megan's airline ticket is successfully processed. The Contoso travel budget now has $4,500 remaining in available funds. If you need to make any more transactions or require further assistance with your budget, please let me know!"

Consider a budgets API that you can use to query and create budgets, charge expenses, or add funds to existing budgets. The prompt "How much is left in the Contoso travel budget" triggers a budget plugin that makes the following API call.

```http
GET /budgets?name=contoso%20travel
```

Copilot uses the response from the API call to generate its response: "The Contoso travel budget currently has $5,000 in available funds. If you need to allocate funds to specific categories or track expenses, I can assist you with that as well. Just let me know how I can help!"

The prompt "Charge $500 to the Contoso travel budget for Megan's airline ticket" translates to the following API call.

```http
POST /budgets/charge
Content-Type: application/json

{
  "budgetName": "Contoso travel",
  "amount": 500,
  "description": "Megan's airline ticket"
}
```

Copilot responds to the user by using the information returned: "The charge of $500 for Megan's airline ticket is successfully processed. The Contoso travel budget now has $4,500 remaining in available funds. If you need to make any more transactions or require further assistance with your budget, please let me know!"

## How plugins work

![A sequence diagram showing the plugin data flow](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/diagrams/plugin-data-flow.png)

1. The user asks the agent "How much is left in the Fourth Coffee lobby renovation budget?"
2. For an MCP plugin that uses [dynamic tool discovery](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery), the agent fetches the current tool definitions from the plugin's MCP server at runtime and validates any new or changed tools before using them. For a plugin with a pinned tool set, or for a REST API plugin, the agent uses the tools defined in the plugin manifest instead.
3. The agent identifies a budget-related plugin from its available plugins that has an MCP server tool or API `GetBudget` to get budget details. It maps parts of the user's question to the parameters of the function: `budgetName=""`.
4. The agent [asks the user](#confirming-actions) to allow it to send `Fourth Coffee lobby renovation` to the plugin.
5. The user chooses to allow data to be shared with the plugin once, or chooses to always allow data to be shared for this function.
6. If the plugin's MCP server or API requires [authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication), the plugin requests a token or API key from the token store.
7. The token store returns a token or key. If needed, the token store causes the agent to prompt the user to sign in.
8. The agent sends a request to the plugin's MCP server or API, which is hosted outside of Microsoft 365.
9. The MCP server or API returns a response.

   ```json
   {
     "name": "Fourth Coffee lobby renovation",
     "availableFunds": 5000.00
   }
   ```

10. The agent generates a response based on the MCP server or API response.
11. The agent sends the response "The available funds left in the Fourth Coffee lobby renovation budget are $5,000."

## Confirming actions

Copilot asks the user before sending any data for the first time to a plugin.

![A screenshot of a plugin confirmation dialog.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/first-connection-confirmation.png)

After the user confirms the connection, MCP server tools and APIs that only retrieve data don't require confirmation, while tools and APIs that modify data do. Plugin developers can override these defaults. For details, see [Confirmation prompts for MCP and API plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-confirmation-prompts).

## Customizing response presentation

Copilot generates conversational responses by using data from the MCP server or API responses. Plugins can customize how this data is presented, and the mechanism depends on the plugin type.

- **MCP plugins** can deliver rich, interactive responses by using [MCP apps](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps) - UI widgets that the MCP server returns alongside the tool result at runtime. Because the widget is delivered with the tool response rather than defined in the manifest, MCP apps work whether the plugin uses a pinned set of tools or [dynamic tool discovery](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery).
- **API plugins** can provide [Adaptive Card](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api-plugin-adaptive-cards) templates in the plugin manifest to display data in a structured way. Because the templates are defined against the operations declared in the manifest, this approach applies to API plugins and to MCP plugins that use a pinned set of tools.

For source-linked citations on any plugin type, Copilot uses response semantics and can infer citation metadata automatically from the tool or API response. Automatic inference is especially useful for MCP plugins that use dynamic tool discovery, where tools are resolved at runtime and there's no manifest tool definition to configure. For more information, see [Show citations with response semantics](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-citations).

![A screenshot of an Adaptive Card response from an API plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/api-plugins/adaptive-card-citation.png)

## URL handling in action responses

The Microsoft 365 Copilot chat experience might render URLs returned as part of action responses - whether from MCP plugins, API plugins, connectors, or flows - as clickable links. The Copilot runtime controls this behavior and doesn't evaluate it against any domains the plugin declares \(such as the `servers` section of an API plugin's OpenAPI description\).

Platform security, trust, and policy rules govern URL rendering behavior for action responses and it might change over time. Don't rely on clickable URLs in action responses for production-critical scenarios.

## Help the Copilot orchestrator choose your plugin

Microsoft 365 Copilot can uniquely choose the right skill from the many skills in its repertoire. But how can you make sure Copilot chooses *your plugin* to provide the right skill?

The answer lies in how you describe your plugin, its skills, and the parameters for initiation of skills. Specify concise and accurate descriptions in your plugin manifest to best ensure that the Copilot orchestrator knows when and how to invoke your plugin.

The way you describe your plugin to the orchestrator depends on the type of plugin you build, as described in the following table.

| Plugin type | Described by | Learn more |
| --- | --- | --- |
| API plugins | OpenAPI description | [How to make an OpenAPI document effective in extending Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/openapi-document-guidance) |
| Copilot Studio actions | Names and descriptions in Copilot Studio conversation map | [Orchestrate copilot topics and actions with generative AI](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions) |
| Message extension plugins | App manifest | [Guidelines for message extension plugins](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/high-quality-message-extension?context=/microsoft-365/copilot/extensibility/context) |

## Build a declarative agent plugin

Developers can use two tools to generate API plugin packages:

- The [Microsoft 365 Agents Toolkit](https://aka.ms/M365AgentsToolkit) in [Visual Studio](https://visualstudio.microsoft.com/) or [Visual Studio Code](https://code.visualstudio.com/) creates plugin packages based on an existing MCP server or OpenAPI description. Agents Toolkit also has starter projects with an example API and corresponding plugin package.
- [Kiota](https://learn.microsoft.com/en-us/openapi/kiota/overview) is a command line tool and a Visual Studio Code extension that generates plugin packages based on an existing OpenAPI description.

Tip

**Work IQ Dev Tools \(preview\)** — You can also attach and check actions from the command line. `wiqd agent add action` adds an action to a declarative agent, and `wiqd agent validate --mode deep` confirms that an action's OpenAPI description is reachable and well-formed and that a referenced plugin manifest declares the right authentication scheme. An alpha `wiqd plugin` command tree also exists, but its interface is subject to change. For more information, see the [Work IQ Dev Tools documentation](https://aka.ms/wiqd/docs).

## Limitations

When a declarative agent includes up to five plugins defined in the [declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.7), the agent always injects the plugins into the prompt. When the agent includes more than five plugins, it uses semantic matching. Semantic matching is based on the plugin's description, not on any of the individual functions or tools within the plugin itself.

A plugin can include an unlimited number of functions or MCP tools. All of a matched plugin's functions or tools are returned, even if only one is matched. For an MCP plugin that uses [dynamic tool discovery](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery), the tools resolved from the MCP server at runtime count toward this total. Due to token window limits, the quality of the responses might degrade if more than 10 functions or tools are included.

The token window for inputs to and outputs from a plugin truncates large content. The functional limit is subject to change as models improve and depending on any system overhead. Optimize for small token lengths or opt for extensibility options that allow for streaming large content if necessary.

## Related content

- [Build plugins from an MCP server for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-mcp-plugins)
- [Add MCP apps to declarative agents in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps)
- [Dynamic tool discovery for MCP plugins in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery)
- [Build API plugins from an existing API for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-existing-api)
- [Build API plugins with a new API for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-new-api)
- [Plugin manifest schema for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-manifest-2.4)
- [Write effective instructions for declarative agents with API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/instructions-api-plugins)
