<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Govern plugin access and connections

Control who can use your plugin over time. Start with the plugin's controls in the Microsoft 365 admin center; use separate capability controls only when the package setting doesn't cover the access you need.

Use the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map to find the page for a task and identify when a capability has controls outside the package.

## Apply plugin controls

| Goal | Where | Procedure | Verify |
| --- | --- | --- | --- |
| Change who can use the plugin | **Agents** > **Tools** > **Plugins** > **Users** | [Manage plugin availability for users](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#manage-plugin-availability-for-users) | The intended audience can use it; users outside the scope can't. |
| Set allowed publisher categories | **Agents** > **Settings** > **Agent and plugin access** | [Manage plugin availability at the organization level](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#manage-plugin-availability-at-the-organization-level) | The selected category matches organizational policy. |
| Respond to access requests | **Agents** > **Tools** > **Requests** | [Review plugin access requests](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#review-plugin-access-requests) | The request is approved or rejected; verify the requester's resulting access. |
| Stop use across the organization | **Agents** > **Tools** > **Plugins** | [Block a tool](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#block-a-tool) | The plugin is blocked; test access in a new conversation. |
| Restore use | **Agents** > **Tools** > **Plugins** | Follow the [supported plugin controls](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#manage-plugins-and-skills) for the affected package. | Its status and availability match the intended audience. |
| Change an administrator installation | **Agents** > **Tools** > **Plugins** | [Install](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#install-a-tool) or [uninstall](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#uninstall-a-tool) as needed. | The installation state matches the plan. |

Restricted plugins can remain discoverable and users can request access. Blocking is a separate package control. In Cowork, [blocking takes effect for new conversations](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins#block-a-plugin-thats-already-been-shared); conversations already using the plugin continue until they end.

## Apply a component control when required

Use a separate control only when the plugin-level setting doesn't cover the access or behavior you need to manage.

- **If an agent included in your plugin has applicable Agent Registry controls**, use those controls for agent-specific availability, deployment, ownership, requests, or lifecycle actions. See [Governance and lifecycle actions for agents](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-actions?context=/microsoft-365/copilot/extensibility/context).
- **If your plugin requires a separately managed connector connection**, use the connector's product experience for connection, authentication, data-source, indexing, synchronization, or policy settings. For Power Platform connector visibility, see [Overview of the Tools page](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-tools-overview?context=/microsoft-365/copilot/extensibility/context).
- **If your plugin references a remote MCP server**, use its hosting and administration environment for credentials, authorization, security, availability, logging, and runtime controls.
- **If you need to block a separately managed MCP server**, follow [Block or allow an MCP server](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#block-or-allow-an-mcp-server). Review linked plugins and other users before applying a server-wide control.
- **If your plugin uses an app registration, permission, account, or external service**, use the product that owns that setting.

Blocking or uninstalling a plugin doesn't necessarily stop a remote service, revoke consent, remove indexed connector data, or prevent another plugin from using the same MCP server or connector. Check the documented effect of each action.

## Verify the governance outcome

1. Confirm that the plugin has the intended status and user scope.
2. Test an allowed user and, when access is restricted, a user outside the scope in a new conversation.
3. Verify that required agent, connection, permission, and remote-service controls enforce the intended access.
4. Review access requests and assign an owner and next action to any that remain.
5. Record the applied controls, exceptions, remaining dependencies, and owner.

Note

This article governs plugin packages and their included capabilities. For an existing standalone \(unpackaged\) item, use its product-specific administration guidance, such as [Agent Registry](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry?context=/microsoft-365/copilot/extensibility/context) or [Manage plugins, skills, and MCP servers](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context).

## Next step

[Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)

## Related content

- [Make your plugin available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365)
- [Make your plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin)
- [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)
- [Improve and update your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
- [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin)
