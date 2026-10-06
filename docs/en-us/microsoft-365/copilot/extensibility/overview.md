<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Ways to extend Microsoft 365 Copilot

Start by deciding where people will use the experience:

- **Inside Microsoft 365 Copilot experiences.** Build or configure supported agents, connectors, skills, and tools, and then follow the package, distribution, and governance guidance for the selected route.
- **In your apps and custom agents.** Use APIs and SDKs to add Microsoft 365 work context and Copilot capabilities to experiences that you own and operate.

You can use both approaches in one solution. Choose the primary path based on the user experience, runtime, distribution model, and operating responsibilities.

## Choose where the experience lives

| Where people use the experience | Start with | Use it when |
| --- | --- | --- |
| Inside Microsoft 365 Copilot experiences | [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview) | You want to build or configure a plugin with supported agents, skills, connectors, or MCP-based tools |
| In your apps and custom agents | [Build Copilot-powered apps and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/apps-agents-overview) | You want to use Microsoft 365 work context or Copilot capabilities in an experience that you host and operate |

## Choose by what you want to create

| If you want to | Start with |
| --- | --- |
| Build a declarative agent that uses Copilot's orchestrator and models | [Declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent) |
| Add reusable instructions or workflows to a declarative agent | [Skills as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-skills) |
| Ground Microsoft 365 Copilot in approved external organizational data | [Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-copilot-connector) |
| Make remote MCP tools available through a supported route | [MCP servers and plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-mcp-servers) |
| Maintain or evaluate a Teams message extension integration | [Message extensions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-message-extension-bot) |
| Build and distribute a plugin that brings supported capabilities together | [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview) |
| Build an application that uses Microsoft 365 work context | [Work IQ APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/) |
| Add Copilot search, retrieval, chat, export, meeting, reporting, or administration capabilities to an application | [Microsoft 365 Copilot APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview) |
| Build an agent with your own orchestration, models, hosting, or runtime | [Custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent) |

For help comparing declarative and custom engine agents, see [Compare declarative and custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-overview).

## Combine both paths

A solution can combine multiple paths. For example:

- A declarative agent can call an external API or remote MCP server through a supported action.
- An application can use a Copilot API while a separately packaged agent gives users a related experience inside Microsoft 365 Copilot.
- A custom engine agent can use Work IQ APIs and also follow the package or distribution requirements of its target channel.

Using an API doesn't by itself select a package or distribution route. Each part of a combined solution retains its own identity, authentication, deployment, distribution, and governance requirements.

## Plan and continue

- [Plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide) across data, identity, security, distribution, compatibility, cost, and ownership.
- [For builders](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/builder-guide), choose a development experience and implementation guidance.
- [For administrators](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide), prepare the organization and identify applicable controls.
- [For ISVs and software publishers](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/isv-publisher-guide), determine the supported customer distribution route.

## Related content

- [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview)
- [Build Copilot-powered apps and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/apps-agents-overview)
- [Compare declarative and custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-overview)
- [Custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-custom-engine-agent)
- [Work IQ APIs](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)
- [Microsoft 365 Copilot APIs overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-apis-overview)
