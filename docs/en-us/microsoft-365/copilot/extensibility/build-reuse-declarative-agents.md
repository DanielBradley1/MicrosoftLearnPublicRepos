<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-declarative-agents -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Build a declarative agent

Use the agent decision from your component plan to create a working goal-directed conversational experience. The agent should have the required identity, instructions, knowledge, capabilities, and connections before you package the plugin.

## Reuse or extend an agent

Before you create an agent:

1. Confirm that the existing agent supports the intended users and Microsoft experiences.
2. Review its instructions, knowledge, capabilities, connections, permissions, and known limitations.
3. Confirm whether you can use it as-is, configure it, copy it, or extend it.
4. Agree on ownership, versioning, support, and change management with the agent owner.
5. Test the reused agent against the requirements in the solution brief.

You can also [start with an agent template](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-templates-overview) or [copy an Agent Builder agent to Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copy-agent-to-copilot-studio) when the supported workflow fits the development plan.

## Choose the implementation path

Use the development tool that you chose in [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools).

| Development tool | Start with |
| --- | --- |
| Agent Builder | [Agent Builder overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder) and [build an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents) |
| Work IQ Dev Tools | [Work IQ Dev Tools quickstart](https://microsoft.github.io/wiqd/getting-started/quickstart/) |
| Copilot Studio | [Build agents with Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions?context=/microsoft-365/copilot/extensibility/context) |
| Microsoft 365 Agents Toolkit | [Microsoft 365 Agents Toolkit overview](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context), using [TypeSpec](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-typespec) or [JSON](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) as supported |

### Work IQ Dev Tools

Use `wiqd agent create` to scaffold a source-controlled declarative-agent project. During the build stage, edit the project, add supported OpenAPI or remote MCP actions with `wiqd agent add action`, and run offline static validation with `wiqd agent validate`.

`wiqd agent add skill` adds a skill to an existing declarative-agent project. This capability is behind the `agent-skills` preview flag, which is off by default. Confirm the current flag, schema, and lifecycle requirements in the [WIQD command reference](https://microsoft.github.io/wiqd/cli/reference/#wiqd-agent-add-skill).

You can enter commands directly or drive the documented workflow conversationally through Copilot CLI with the `wiqd:wiqd` agent. WIQD targets declarative agents, not custom engine agents.

GitHub Copilot can assist with project files, instructions, configuration, code, and tests. It doesn't replace the authoring tool, runtime, or component-specific requirements.

## Implement the agent

Complete the applicable work:

1. Define or confirm the agent's name, description, purpose, audience, and conversation starters.
2. Write instructions that define its behavior, boundaries, and use of knowledge and actions.
3. Add the required knowledge sources.
4. Add built-in capabilities, skills, connectors, MCP-based tools, or API actions.
5. Configure identities, authentication, permissions, consent, and connections.
6. Configure environments and versions when the development workflow supports them.
7. Test representative prompts, tool selection, responses, errors, and unsupported requests.

Use the following guidance to configure the agent:

- [Write effective instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions)
- [Add knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources)
- [MCP and API actions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins)
- [Manage environments and versions for declarative agents with Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agents-multi-environment)

For background and design guidance, see [Best practices for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-best-practices) and [How the Copilot orchestrator chooses actions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/orchestrator).

After the required behavior works, you can optionally [enable user feedback](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-enable-feedback) and [optimize content retrieval](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/optimize-content-retrieval).

## Confirm that the agent is working

The agent is ready for integration when:

- Its identity and purpose are clear to the intended users.
- Instructions produce the expected behavior for representative scenarios.
- Required knowledge is available and permission-trimmed.
- Skills, connectors, actions, and MCP-based tools can be selected and invoked.
- Authentication, consent, confirmations, and failure behavior work as intended.
- The agent works in every development or test experience required by the plan.
- The owner, version, dependencies, limitations, and test evidence are recorded.

Continue with any other components in the plan. When they are complete, [integrate and test your components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components).

## Related content

- [Declarative agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Debug agents using Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-copilot-studio)
- [Debug agents using Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-vscode)
