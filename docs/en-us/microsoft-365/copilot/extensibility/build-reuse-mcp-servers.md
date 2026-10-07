<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-mcp-servers -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Build or reuse MCP servers

Use the MCP server decision from your component plan to provide remotely hosted tools or resources. The running MCP server remains separate from the plugin package, so you must implement or confirm both the remote runtime and the supported connection to the target Microsoft experience.

## Reuse an MCP server

Before you build a server:

1. Identify an approved MCP server that exposes the required tools or resources.
2. Review its tool definitions, inputs, outputs, errors, annotations, and confirmation behavior.
3. Confirm that its transport, authentication model, and protocol features are supported by the target Microsoft experience.
4. Confirm the server owner, endpoint, version, availability, data handling, support, and change process.
5. Obtain access and configure the development or test connection.
6. Test representative discovery, authentication, invocation, and failure scenarios.

Referencing an MCP server doesn't transfer responsibility for operating it. Record the service owner and support agreement before you reuse it.

## Build and operate an MCP server

Build a new MCP server when no approved server meets the requirement.

1. Implement only the tools and resources required by the component plan.
2. Define clear names, descriptions, inputs, outputs, errors, and safety annotations.
3. Implement authentication, authorization, data access, and least-privilege behavior.
4. Configure hosting, networking, secrets, logging, monitoring, scaling, and incident response.
5. Version the protocol behavior and document compatibility expectations.
6. Test the server independently before connecting it to a Microsoft experience.

GitHub Copilot can assist with server code, schemas, tests, and repository changes. It doesn't provide the MCP runtime, hosting, authentication, or Microsoft 365 connection by itself.

## Connect the server

Use the integration supported by the selected development tool and target experience.

| Development approach | Start with |
| --- | --- |
| Declarative agent with Agents Toolkit | [Build a plugin for a declarative agent from an MCP server](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-mcp-plugins) |
| Work IQ Dev Tools | [Build a plugin with Work IQ Dev Tools](https://microsoft.github.io/wiqd/getting-started/build-a-plugin/) |
| Copilot Studio | [Microsoft Copilot Studio documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/) |
| Interactive MCP response | [Add MCP apps to declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps) |
| BYO remote MCP server registration with Agent 365 CLI | [Register a remote MCP server in Agent Tools](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-tools-for-agent?context=/microsoft-365/copilot/extensibility/context#register-a-remote-mcp-server) |

Important

The Agent 365 CLI BYO MCP route is in preview and uses a separate registration and administration model from an MCP plugin packaged for a Microsoft 365 declarative agent. The documented supported clients are Copilot Studio, Visual Studio Code, Claude Code, and GitHub Copilot CLI. Microsoft 365 declarative agents aren't supported by this route. Administrators use Agent Tools to review, approve, consent to, block, and monitor the registered server.

### Work IQ Dev Tools

The alpha `wiqd plugin add connector` command adds a remote MCP connector to a WIQD plugin package. The documented server requirements include:

- HTTPS with TLS 1.2 or later.
- Streamable HTTP transport using JSON-RPC 2.0.
- Support for `tools/list` and `tools/call`.
- Tool calls that complete in less than 30 seconds.

WIQD scaffolds against manifest version 1.29, where `mcpToolDescription` is optional. Copilot Cowork still requires a tool-description file. If Cowork is a target experience, capture the server's `tools/list` output and pass it with `--tool-description`; otherwise, the package can pass WIQD validation but fail connection verification in Cowork.

For OAuth or API-key authentication, register the credential first and add only its reference identifier to the package. Don't put client secrets, API keys, or tokens in the manifest. See the [WIQD plugin authoring reference](https://microsoft.github.io/wiqd/getting-started/plugin-reference/#connector--remote-mcp-server-requirements).

Configure [authentication](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication), choose [dynamic discovery or pinned tools](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-dynamic-tool-discovery), and add the metadata required by the target experience.

## Confirm that the MCP capability is working

The MCP server and its connection are ready for integration when:

- The endpoint is available from the development or test environment.
- Required tools or resources can be discovered by the target experience.
- Representative operations return the expected structured results.
- Authentication, authorization, consent, and permissions work as intended.
- Confirmation, timeout, unavailable-service, invalid-input, and partial-failure behavior is understandable.
- Logs and monitoring provide enough information to diagnose failures.
- The server owner, version, endpoint, hosting, dependencies, limitations, and test evidence are recorded.

Use [local MCP and API debugging](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-debug-local) when the server isn't publicly reachable during development.

Continue with any other components in the plan. When they are complete, [integrate and test your components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components).

## Related content

- [MCP servers as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-mcp-servers)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [MCP apps UX guidelines](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps-ui-guidelines)
- [Troubleshoot MCP apps](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps-troubleshooting)
