<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/apps-agents-overview -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Build Copilot-powered apps

Use APIs when people interact with an application that you host and operate. This path gives you control over the user experience, runtime, deployment, and application lifecycle.

To build an agent for Microsoft 365 Copilot—including a custom engine agent that you host and package as a plugin—see [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin).

## Choose an approach

| Option | Use it to |
| --- | --- |
| [Work IQ APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/) | Use Microsoft 365 work context through supported REST, agent-to-agent \(A2A\), and MCP interfaces |
| [Microsoft 365 Copilot APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview) | Add Copilot search, retrieval, chat, export, meeting, reporting, and administration capabilities to an application |

You can combine these options. For example, an application can use the Microsoft 365 Copilot APIs for chat and retrieval and Work IQ APIs for Microsoft 365 work context.

## Understand how this path differs from plugins

Applications are experiences that you own and operate. They can use APIs, SDKs, models, services, and data sources without becoming plugins.

Calling an API doesn't by itself publish a plugin. A plugin uses the applicable package, registry, distribution, and governance lifecycle for supported Microsoft experiences. An application can interact with plugins or include separately packaged capabilities, but each part retains its own lifecycle requirements.

An API plugin is a technical action mechanism used by a declarative agent. It isn't a Microsoft 365 Copilot API or a peer capability in the plugin registry model.

## Plan the application

Before implementation:

- Define the users, customer outcome, and experience that you own.
- Choose the required APIs, SDKs, models, and hosting services.
- Plan user, application, and service identities.
- Identify permissions, consent, authentication, and connection requirements.
- Review data access, storage, retention, privacy, security, and responsible AI requirements.
- Define deployment environments, monitoring, support, versioning, and incident response.
- Determine whether any part of the solution also requires a plugin or Microsoft 365 app package.

If the solution also requires a plugin, see [Plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide).

## Follow the application lifecycle

1. Choose the APIs, SDKs, runtime, and hosting model.
2. Register and configure the required identities and permissions.
3. Build and test the application.
4. Validate behavior, security, data access, and supported environments.
5. Deploy through the distribution channel for your application platform.
6. Monitor availability, usage, cost, security, and quality.
7. Update, deprecate, or retire the solution according to your service lifecycle.

## Related content

- [Ways to extend Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview)
- [For builders](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/builder-guide)
- [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview)
- [Work IQ APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)
- [Build a custom engine agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent)
