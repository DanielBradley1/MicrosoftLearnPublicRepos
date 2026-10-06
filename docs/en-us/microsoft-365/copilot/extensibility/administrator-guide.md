<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Administer Microsoft 365 Copilot plugins and agents

Define organizational requirements early, review the exact objects being published, make approved solutions available, configure required connections, apply controls throughout the lifecycle, monitor use, and retire solutions safely.

## Understand what you're administering

Identify the exact object before you apply a control.

| Object | What to identify |
| --- | --- |
| Plugin package | The exact package identity, version, publishing route, availability, and assignment state. |
| Agent | The specific agent identity, version, owner, sharing or publishing state, and supported Microsoft experiences. |
| Skill | The declared skill, the agent or package that references it, and the surface that controls its availability. |
| MCP server | The server, endpoint, exposed tools, authentication requirements, and applicable tool controls. |
| Connector | The connector model, package or definition, owner, supported experiences, and applicable availability controls. |
| Connection | The account, authentication method, user or organizational scope, and revocation procedure. |
| External service | The service owner, account access, consent, data handling, operational dependencies, and removal procedure. |
| Microsoft 365 app | The app identity, Microsoft 365 app package, catalog or publishing state, and applicable app-management controls. |

These objects can use different administration surfaces and enforcement mechanisms. Controlling one object doesn't automatically control every referenced component, connection, external service, or runtime dependency. To identify who acts next on each object, see [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins).

## Follow the plugin lifecycle

| Stage | What you need to do |
| --- | --- |
| Prepare to build your plugin | Define allowed audiences, identity and consent requirements, data boundaries, licensing, support, governance outcomes, and permitted capabilities. |
| Build or reuse capabilities | Provide approved development environments, registrations, permissions, data access, test users, and external-service requirements. |
| Package and test | Review the package identity, ownership, declared components, permissions, data flows, dependencies, test evidence, limitations, and support information. |
| Publish and distribute | Confirm the supported route, intended audience, acquisition or approval process, assignment model, ownership, and support responsibilities. |
| Make available and govern | Complete only the required review, acquisition, assignment, enablement, connection, access, tool, and blocking actions for the selected route. |
| Monitor, update, and retire | Monitor available signals, evaluate behavior when appropriate, review updates, adjust access, investigate issues, transfer ownership where supported, and retire the solution and its dependencies safely. |

## Operate approved plugins

Start with the publishing record supplied by the builder or publisher. Confirm:

- Object identity and exact version.
- Publisher or creator identity and any publisher provenance supplied by the route.
- Publishing or sharing route.
- Intended users or groups.
- Supported Microsoft experiences.
- Included agents, skills, connectors, MCP servers, and other components, including their descriptions and dependencies.
- Required licenses.
- Permissions and consent.
- Connections and external services.
- Known limitations.
- Support and update owner.

Complete only the actions required by the selected route. Not every route requires review, acquisition, assignment, enablement, or connection. A per-user connection isn't the same as organization-level deployment. Package availability and component or runtime controls can be separate operations.

| What you need to do | Start with |
| --- | --- |
| Complete the review, acquisition, assignment, enablement, connection, and access actions your route requires | [Make the plugin or agent available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin) |
| Decide which control applies to which object and surface | [Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage) |
| Monitor use, review and roll out published updates, restrict access, or retire the plugin | [Monitor, update, and retire your plugin or agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin) |

These actions can use different administration surfaces and enforcement mechanisms. Don't assume that one approval, assignment, or block propagates to every Microsoft experience or dependency unless the linked product procedure confirms it.

## Find administration guidance

- See [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins) to identify who acts next.
- See [Make the plugin or agent available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin) to complete route-specific rollout actions.
- See [Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage) to identify the applicable control surface.
- See [Monitor, update, and retire your plugin or agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin) to manage the operational lifecycle.

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
- [Choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Test and validate your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin)
- [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Make plugins and agents available](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin)
- [Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)
- [Monitor, update, and retire your plugin or agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
