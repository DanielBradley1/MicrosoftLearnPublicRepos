<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Declarative agents for Microsoft 365 Copilot

Declarative agents provide a goal-directed conversational experience that is powered by Microsoft 365 Copilot. You define the agent's purpose, instructions, knowledge, and supported actions to address a business scenario. A plugin can include or reference an agent with other supported capabilities, such as skills, Copilot connectors, or MCP-based tools.

Choose a declarative agent when users need a dedicated conversational experience with behavior and capabilities tailored to a specific outcome. You don't need to create an agent when an existing Microsoft experience or approved agent can use the selected skills, connectors, or tools.

Note

For information about the two approaches to building agents for Microsoft 365 Copilot, see [Agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-overview).

## Decide whether you need a declarative agent

Consider a declarative agent when the solution requires:

- A named conversational experience for a defined audience and outcome.
- Instructions and constraints that apply consistently across conversations.
- Curated knowledge sources for grounding.
- Actions, skills, connectors, or MCP-based capabilities selected for the scenario.
- Conversation starters and metadata that help users understand what the agent does.

For example, an employee-support agent can use approved organizational knowledge to answer common questions. A customer-support agent can combine instructions and knowledge with an external capability that retrieves current order information.

[![A diagram that shows two scenarios of declarative agents mentioned in the article.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agent-scenarios.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agent-scenarios.png#lightbox)

An agent might not be the right component when:

- Users already work in a supported experience that can use the required capability directly.
- An existing approved agent meets the outcome and can be configured or extended.
- The solution requires complete control of the orchestration, model, hosting, or user interface. In that case, compare [declarative and custom engine agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-overview).

For detailed fit and limitation guidance, see [Declarative agent architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-architecture).

## Understand what the agent contributes

A declarative agent is defined by configuration that describes:

- **Identity and behavior**: The agent's name, purpose, instructions, conversation starters, constraints, and visual representation.
- **Knowledge**: The approved information sources that ground responses.
- **Capabilities**: The actions, skills, connectors, or tools the agent can use.
- **Host and distribution metadata**: The information required to surface the agent in supported Microsoft experiences.

Users engage with declarative agents in Microsoft 365 Copilot and supported Microsoft 365 apps.

[![Screenshots that show declarative agents running in Microsoft 365 Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agent-showcase.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agent-showcase.png#lightbox)

## Decide whether to build or reuse

Before you build an agent:

- Review agents that are already approved for the target users and experiences.
- Determine whether an existing agent can be reused, copied, configured, or extended.
- Confirm who owns the agent instructions, knowledge, connections, and support.
- Identify any gaps that require a new agent.

If you reuse an agent, confirm that its owner supports the intended users, data, capabilities, sharing scope, and lifecycle.

## Record agent dependencies

As you decide whether to build or reuse an agent, note:

- Target users, outcome, and Microsoft experiences.
- Instructions, knowledge sources, and conversation requirements.
- Required skills, connectors, actions, or MCP-based capabilities.
- Identity, permissions, consent, and data boundaries.
- Availability, language, licensing, and environment requirements.
- Owner, support contact, and success measures.

After you decide to build or reuse an agent, [choose development tools](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools).

## National cloud support

Declarative agent support for [Microsoft 365 Government](https://www.microsoft.com/microsoft-365/government) tenants varies by cloud:

- **Government Community Cloud \(GCC\)**: Full declarative agent support is available.
- **Government Community Cloud High \(GCCH\)**: Pro-code agents built with Microsoft 365 Agents Toolkit are supported. Agent Builder is also now available in GCCH.
- **Department of Defense \(DoD\)**: Limited support - only pro-code agents built with Microsoft 365 Agents Toolkit are supported. Agent Builder isn't available for declarative agents in DoD.

## Related content

- [Choose capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-components)
- [Agents in the Microsoft 365 ecosystem](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/ecosystem)
- [Declarative agent architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-architecture)
- [Declarative agents FAQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/transparency-faq-declarative-agent)
- [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools)
- [Build agents with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents)
- [Build agents with Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context)
- [Responsible AI validation checks](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/rai-validation)
