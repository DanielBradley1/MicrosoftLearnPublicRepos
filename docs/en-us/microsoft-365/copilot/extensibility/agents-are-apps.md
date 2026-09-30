<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-are-apps -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# What is a Microsoft 365 Copilot plugin?

A plugin brings supported capabilities together for use in Microsoft 365 Copilot experiences. For example, a solution might use a skill to guide a task, a Copilot connector to access organizational content, and an MCP server to provide tools. The plugin gives that solution a way to be packaged, published, and made available through supported Microsoft routes.

You build each capability with the tools and guidance that apply to it. The plugin model connects those capabilities to a publishing and management lifecycle; it doesn't change how each capability runs.

Important

Supported components, packages, publishing routes, administration steps, and Microsoft experiences vary by product and rollout. Use the linked guidance for the capabilities and route you choose.

## Choose your path

Choose the route that matches what you need to do:

- **Package and share an existing agent:** If you have the local source project for a supported declarative agent, follow the [Work IQ Dev Tools quickstart](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/quickstart-plugin) to validate, provision, package, share, and test it without rebuilding the agent.
- **Build new capabilities:** If you need to build a new agent, skill, Copilot connector, or MCP server, [plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide) and follow the complete lifecycle.
- **Administer plugins and agents:** Follow the [administrator guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide) to review, make available, govern, monitor, update, or retire them.
- **Publish for customers:** Follow the [ISV and software publisher guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/isv-publisher-guide) for public distribution, certification, servicing, and support.

## Decide what your solution needs

Start with the job the solution should help someone do, who will use it, and where they will use it. Then choose the capabilities that support that job.

| Capability | Use it to | Learn more |
| --- | --- | --- |
| Declarative agent | Create a goal-directed experience by using instructions, knowledge, and tools | [Declarative agents overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent) |
| Skill | Provide reusable instructions or a workflow for a specific job | [Skills as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-skills) |
| Copilot connector | Make approved external organizational content available | [Copilot connectors as plugin capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-connectors) |
| MCP server | Provide tools and resources from a remote server | [MCP servers and plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-mcp-servers) |

A plugin can bring together one supported capability or several. You can build new components or reuse existing ones. A component can also exist outside a plugin and have its own administration requirements.

A plugin doesn't necessarily contain the service it uses. For example, its package can include the configuration for a remote MCP server while that server runs separately.

## Take your plugin from idea to use

1. **Prepare to build your plugin.** Define the intended users, outcome, target experiences, capabilities, and requirements.
2. **Build or reuse capabilities.** Build or reuse each required component by using its supported development guidance, and confirm that each component works independently.
3. **Package and test.** Integrate the capabilities, create and validate the required package, test the resulting experience, and evaluate agent quality when appropriate.
4. **Publish and distribute.** Submit the validated artifact through a supported distribution route.
5. **Make available and govern.** Complete the review, acquisition, assignment, enablement, connection, access, and control actions that apply to the route and capability.
6. **Monitor, update, and retire.** Monitor available signals, evaluate behavior when appropriate, release validated updates, manage ownership and access, and retire the solution when needed.

**Publishing doesn't by itself make a plugin usable.** The actions after publishing depend on the distribution route and components. Follow the procedure for your route rather than assuming that review, acquisition, assignment, enablement, and connection happen as one step.

Governance applies throughout the lifecycle. Define requirements during planning, validate identity and dependencies before publishing, apply availability and connection controls when you make the solution available, and manage updates, restrictions, and retirement during operation.

## Understand the package and registry

| Term | Meaning |
| --- | --- |
| **Plugin** | The solution that brings together supported capabilities for a particular use |
| **Plugin package** | The versioned artifact used for validation, publishing, and updates |
| **Component** | A supported capability used by the plugin |
| **Plugin registry** | Shared infrastructure for registering and distributing plugins |

The package can describe and connect components without containing their runtime services. Components can also appear in administrative inventories independently of a plugin.

Registration and distribution don't replace product-specific administration. Availability, access, tools, connections, external services, data, and runtime behavior can use separate control surfaces.

## Follow the guidance for your role

- **[Build plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/builder-guide):** Plan the solution, select tools and components, then build, package, and test it.
- **[Administer plugins and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide):** Review requirements early, then manage the applicable availability, access, connections, and operational controls.
- **[Publish plugins for customers](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/isv-publisher-guide):** Follow the full lifecycle, including the requirements for public distribution, certification, servicing, and customer support.
- **Users:** Find and use plugins made available in their Microsoft experience.

## Check product-specific requirements

The plugin model doesn't replace the development tools, manifests, certification, runtime behavior, or administration procedures for each capability.

Agents can participate in the broader plugin model in different ways depending on the agent type, package, publishing route, and Microsoft experience. Follow the publishing guidance for the agent and authoring tool you use.

Existing API plugins remain supported as actions for declarative agents. See [MCP and API plugins for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) for their packaging and lifecycle guidance.

## Next steps

- [Quickstart: Package and share an existing declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/quickstart-plugin)
- [Plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Make your plugin or agent available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Monitor, update, and retire](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
