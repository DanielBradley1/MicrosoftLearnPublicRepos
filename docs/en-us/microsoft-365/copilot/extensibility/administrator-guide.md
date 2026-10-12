<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Administer Microsoft 365 Copilot plugins

Define organizational requirements early, review the exact plugin package, make approved plugins available, configure required connections, apply controls throughout the lifecycle, monitor use, and retire plugins safely.

## Understand what you're administering

Identify the exact plugin package and the capabilities or dependencies that require separate controls.

| Object | What to identify |
| --- | --- |
| Plugin package | The exact package identity, version, publishing method, availability, and assignment state. |
| Included agent | The agent identity, version, owner, and applicable Agent Registry controls. |
| Skill | The declared skill, the package that includes it, and any separate availability control. |
| MCP server | The server, endpoint, exposed tools, authentication requirements, and applicable tool controls. |
| Connector | The connector model, connection, owner, supported experiences, and applicable data or policy controls. |
| Connection | The account, authentication method, user or organizational scope, and revocation procedure. |
| External service | The service owner, account access, consent, data handling, operational dependencies, and removal procedure. |

These objects can use different administration surfaces and enforcement mechanisms. Controlling one object doesn't automatically control every referenced component, connection, external service, or runtime dependency. To identify who acts next, see the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map.

## Follow the plugin lifecycle

| Stage | What you need to do |
| --- | --- |
| Prepare to build your plugin | Define allowed audiences, identity and consent requirements, data boundaries, licensing, support, governance outcomes, and permitted capabilities. |
| Build or reuse capabilities | Provide approved development environments, registrations, permissions, data access, test users, and external-service requirements. |
| Package and test | Review the package identity, ownership, declared components, permissions, data flows, dependencies, test evidence, limitations, and support information. |
| Publish or share | Confirm the supported method, intended audience, acquisition or approval process, assignment model, ownership, and support responsibilities. |
| Make available and govern | Complete only the required review, acquisition, assignment, enablement, connection, access, tool, and blocking actions for the selected method. |
| Monitor, update, and retire | Monitor available signals, evaluate behavior when appropriate, review updates, adjust access, investigate issues, transfer ownership where supported, and retire the solution and its dependencies safely. |

## Operate approved plugins

Start with the publishing record supplied by the builder or publisher. Confirm:

- Object identity and exact version.
- Publisher or creator identity and any publisher provenance supplied by the method.
- Publishing or sharing method.
- Intended users or groups.
- Supported Microsoft experiences.
- Included agents, skills, connectors, MCP servers, and other components, including their descriptions and dependencies.
- Required licenses.
- Permissions and consent.
- Connections and external services.
- Known limitations.
- Support and update owner.

Complete only the actions required by the selected method. Not every method requires review, acquisition, assignment, enablement, or connection. A per-user connection isn't the same as organization-level deployment. Package availability and component or runtime controls can be separate operations.

| What you need to do | Start with |
| --- | --- |
| Complete the review, acquisition, assignment, enablement, connection, and access actions the method requires | [Make your plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin) |
| Identify an included capability or dependency that requires a separate control | [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) |
| Monitor use and investigate problems | [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin) |
| Evaluate, improve, and roll out an update | [Improve and update your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin) |
| Take down the plugin and clean up resources | [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin) |

These actions can use different administration surfaces and enforcement mechanisms. Don't assume that one approval, assignment, or block propagates to every Microsoft experience or dependency unless the linked product procedure confirms it.

## Find administration guidance

- To distinguish Agent Registry from Tools Registry and direct package and capability tasks, see the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map.
- To complete method-specific rollout actions, see [Make your plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin).
- To manage and restrict access over time, see [Govern plugin access and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage).
- To investigate usage or failures, see [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin).
- To evaluate, improve, and release a change, see [Improve and update your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin).
- To take down the plugin, see [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin).

Use the linked product administration articles as the source of truth for current procedures, interface labels, availability, and enforcement behavior.

## Plan organizational readiness

- Define allowed distribution scopes and capability types in the [plugin solution brief](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide).
- Establish review, approval, and exception processes.
- Assign support and lifecycle owners.
- Confirm [licensing and cost](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/cost-considerations) requirements.
- Review [data, privacy, and security](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/data-privacy-security), compliance, and external-service implications.
- Establish update, incident, ownership-transfer, and retirement procedures.

## Related content

- [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview)
- [Choose capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-components)
- [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Publish or share your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Test and validate your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin)
- [Make your plugin available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365)
- [Make your plugin available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin)
- [Govern plugin access and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)
- [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)
- [Improve and update your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
- [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin)
