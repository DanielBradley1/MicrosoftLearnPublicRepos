<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide -->
<!-- Sitemap-Last-Modified: 2026-10-12 -->

# Administer Microsoft 365 Copilot plugins

Define organizational requirements early, review the exact plugin package, make approved plugins available, configure required connections, apply controls throughout the lifecycle, monitor use, and retire plugins safely.

## Understand what you're administering

Identify the exact plugin package and the capabilities or dependencies that require separate controls.

| Object | What to identify |
| --- | --- |
| Plugin package | The exact package identity, version, publishing method, availability, and assignment state. |
| Included agent | The agent identity, version, owner, and applicable Agent Registry controls. |
| Skill | Whether the skill is separately packaged or bundled with other capabilities; a bundled skill doesn't have its own blocking control. |
| MCP server | The server, endpoint, exposed tools, authentication requirements, and applicable tool controls. |
| Connector | The connector model, connection, owner, supported experiences, and applicable data or policy controls. |
| Connection | The account, authentication method, user or organizational scope, and revocation procedure. |
| External service | The service owner, account access, consent, data handling, operational dependencies, and removal procedure. |

These objects can use different administration surfaces and enforcement mechanisms. Controlling one object doesn't automatically control every referenced component, connection, external service, or runtime dependency. To identify who acts next, see the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map.

## Follow the plugin lifecycle

| Stage | What you need to do |
| --- | --- |
| Prepare | Define allowed audiences, identity and consent requirements, data boundaries, licensing, support, governance outcomes, and permitted capabilities. |
| Build or reuse | Provide approved development environments, registrations, permissions, data access, test users, and external-service requirements. |
| Package & test | Review the package identity, ownership, declared components, permissions, data flows, dependencies, test evidence, limitations, and support information. |
| Publish & distribute | Confirm the supported method, intended audience, acquisition or approval process, assignment model, ownership, and support responsibilities. |
| Make available & govern | Complete only the required review, acquisition, assignment, enablement, connection, access, tool, and blocking actions for the selected method. |
| Monitor, update & retire | Monitor available signals, evaluate behavior when appropriate, review updates, adjust access, investigate issues, transfer ownership where supported, and retire the solution and its dependencies safely. |
| Discover & use | Direct users to the supported product's discovery and setup guidance; confirm that they can complete sign-in, consent, connections, and intended tasks. |

Use [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins) to separate publishing, approval, availability, assignment, consent, connections, and removal. These steps aren't interchangeable.

## Govern skills at the package boundary

Use **Agents** > **Tools** > **Registry** to review plugin and separately packaged skill records in the Microsoft 365 admin center. For plugin user availability, use **Agents** > **Tools** > **Plugins** > *plugin* > **Users**. Follow [Manage plugins, skills, and MCP servers](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/manage-plugins-skills-mcp-servers) for supported actions.

For a bundled skill, apply the plugin's controls. You can't block an individual skill inside a package today. Blocking a package that contains an agent also blocks that agent; a package with an agent and a skill appears under both Tools and Agents as one entity.

Don't assume every skill is stored in the plugin registry. Skills used in Word, Excel, and PowerPoint are stored in OneDrive today. An individual MCP tool's blocking control isn't a skill-level control.

For object-specific restrictions, see [Govern access, tools, and connections for plugins and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage). Keep Power Platform connector policies and product connection settings separate from package approval.

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

Use this record to agree who completes rollout and who supports the plugin afterward. Complete only the actions required by the distribution method. A per-user connection isn't an organization-level deployment, and package availability doesn't grant access to every dependency.

## Find administration guidance

| What you need to do | Start with |
| --- | --- |
| Understand the separate setup and access steps | [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins) |
| Locate the right Microsoft 365 administration page | [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) |
| Complete rollout for intended users | [Make plugins and agents available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin) |
| Restrict access or manage individual objects | [Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage) |
| Investigate usage or failures | [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin) |
| Support, update, hand over, or retire the solution | [Choose a lifecycle task](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin#choose-a-task) |

Use the linked product administration articles as the source of truth for current procedures, interface labels, availability, and enforcement behavior.

## Plan organizational readiness

- Define allowed distribution scopes and capability types in the [plugin solution brief](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide).
- Establish review, approval, and exception processes.
- Assign support and lifecycle owners.
- Confirm [licensing and cost](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/cost-considerations) requirements.
- Review [data, privacy, and security](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/data-privacy-security), compliance, and external-service implications.
- Establish update, incident, ownership-transfer, and retirement procedures.

## Related content

- [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview)
- [Choose capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-components)
- [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Test and validate your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin)
- [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365)
- [Make plugins and agents available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin)
- [Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)
- [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)
- [Monitor, update, and retire your plugin or agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
- [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin)
