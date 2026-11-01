<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-best-practices -->
<!-- Sitemap-Last-Modified: 2026-10-27 -->

# Best practices for building declarative agents

Declarative agents customize Microsoft 365 Copilot for specific business scenarios through instructions, knowledge sources, and supported capabilities. Use these practices to keep an agent focused, configure its actions safely, and evaluate its behavior as it evolves.

Start with a defined audience, user task, and expected outcome. For the boundary between the managed runtime and the services you operate, see [Declarative agent architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-architecture).

Note

This article covers declarative agents, which use Copilot's managed runtime. If you're building a custom engine agent that retrieves Microsoft 365 grounding data, follow the [Retrieval API best practices](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview#best-practices) and [permissions and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview#known-limitations). That guidance is separate from configuring a declarative agent's knowledge sources.

## Declarative agent components

Choose each component to support the agent's intended tasks. Follow the limits in the selected [authoring tool](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents#use-the-configure-tab-to-create-your-agent-manually) and [manifest schema](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.9).

| Component | Best practice |
| --- | --- |
| Name | Use a distinct name that conveys the agent's purpose. Agent Builder allows up to 30 characters; the declarative agent manifest allows up to 100. |
| Description | Summarize the tasks and domain in a few precise sentences, within the 1,000-character limit. Keep detailed behavioral instructions in the instructions field. |
| Instructions | Define the agent's purpose, supported tasks, source and tool use, output format, and failure behavior within the 8,000-character limit. |
| Knowledge sources | Add relevant sources for the intended questions. Confirm their supported scope, freshness, permissions, and licensing. |
| Built-in capabilities | Enable capabilities such as [code interpreter](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter) or [image generator](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/image-generator) only when they support the intended tasks. |
| Custom skills \(preview\) | Use [skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills) for modular task instructions, resources, or scripts. Reference configured skills at a high level rather than duplicating their detailed instructions. |
| Actions | Use [MCP or API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-plugins) for supported interactions with external services. Describe each tool's purpose, inputs, outputs, and failure conditions. |
| Conversation starters | Provide representative prompts that demonstrate supported tasks. No minimum number is required. Test each prompt and follow the selected tool's limits. |

## Best practices for agent instructions

Use instructions to define how the agent should approach the intended tasks:

- **State the outcome and boundaries.** Describe what the agent helps users accomplish, what information it needs, and how it should respond to unsupported requests.
- **Make source and tool use explicit.** Identify which configured source, capability, or action applies to each task. Ask for missing inputs instead of guessing.
- **Separate steps from presentation.** Use clear task steps where order matters, and specify the expected tone, structure, and level of detail for responses.
- **Plan for missing information and failures.** Describe how to handle unavailable sources, incomplete results, denied access, and unsuccessful actions without claiming success.
- **Keep instructions separate from knowledge.** Don't put behavioral instructions in SharePoint documents or other knowledge sources to work around instruction limits. Retrieved content isn't trusted maker-authored instruction content.

For detailed patterns, examples, and guidance on model changes, see [Write effective instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions). For tasks that combine knowledge with API calls, see [Write instructions for agents with API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/instructions-api-plugins).

## Choose the right knowledge sources

Select [knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources) based on the questions the agent must answer:

- **Prefer relevance over quantity.** Scope sources to the files, sites, chats, or other content needed for the task. For SharePoint and embedded files, follow [Optimize content retrieval](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/optimize-content-retrieval).
- **Match retrieval to freshness requirements.** Review source content and ownership regularly. Scoped web search uses Bing-indexed content, not a direct query of the underlying data. For current structured data, evaluate a supported API or MCP action instead. See [Web search grounding and dynamic content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources#web-search-grounding-and-dynamic-content).
- **Confirm access before sharing.** Test with users who represent the intended audience and permissions. Review [embedded-file sharing behavior](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#sharing-an-agent-with-embedded-files) separately from access to the original files.
- **Check capability and licensing support.** Sources and scoping options differ by authoring tool and tenant configuration. Follow the [knowledge-source support matrix](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources) and [licensing guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#agent-capabilities-and-licensing-models).
- **Evaluate grounding, not just answer fluency.** Test questions with known answers and check that responses and citations match the intended sources. Include questions whose answers aren't available.

Adding sources doesn't by itself prevent the agent from using built-in model knowledge. When the scenario requires source-grounded responses, set `behavior_overrides.special_instructions.discourage_model_knowledge` to `true` and reinforce the intended source use in the instructions. This control isn't a guarantee that responses use only configured sources. Continue to evaluate source attribution and behavior when evidence is missing. See [Ground responses to configured knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions#ground-responses-to-configured-knowledge-sources) and the [special instructions reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.9#special-instructions-object).

## Design safe actions

Use actions for supported interactions with external services, and distinguish them from knowledge sources. A Copilot connector used for grounding isn't interchangeable with an API or MCP tool that changes external data.

- **Describe operations precisely.** Explain when a tool should be used, its required parameters, and its expected results and errors. For REST APIs, follow [OpenAPI document guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/openapi-document-guidance).
- **Configure confirmations for the integration.** For API plugins, use the OpenAPI extension `x-openai-isConsequential`, not `isConsequential`, and mark operations with side effects as consequential. For MCP tools, use `readOnlyHint` only for tools that are read-only. Follow [Confirmation prompts for MCP and API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-confirmation-prompts) for the supported settings and behavior.
- **Enforce access in the service.** Use the supported [authentication method](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication) and validate authorization and inputs in the external service. Instructions and confirmation prompts don't replace those checks.
- **Design for failure and repeated requests.** Test denied confirmations, expired authentication, invalid inputs, and service errors. For operations that change data, ensure that retries don't unintentionally repeat the change.

Use [Plan data, privacy, and security](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/data-privacy-security) to identify the data flows, permissions, and human-oversight requirements for each action.

## Test and iterate

Define expected behavior before changing the agent, and keep a repeatable set of test cases. Use the authoring tool's test experience for early feedback, then validate the deployed agent in its intended hosts.

| Test area | What to verify |
| --- | --- |
| Supported tasks | Conversation starters, realistic user phrasing, and follow-up questions produce the intended outcomes. |
| Missing or unsupported information | The agent asks for required inputs, explains unavailable evidence, and doesn't invent facts or claim unsuccessful actions completed. |
| Grounding and permissions | Answers and citations match the intended sources. Test users with different access, and confirm that restricted information isn't exposed. |
| Actions and failures | Check the actual external result as well as the response. Test confirmations, cancellations, authentication failures, service errors, and repeated requests. |
| Host experience | Test each supported app you intend to deploy to. Check document context, response presentation, and available capabilities rather than assuming identical behavior across all apps. |
| Performance and changes | Measure response times and rerun regression cases after changes to instructions, knowledge, tools, skills, or platform behavior. |

Include users who didn't write the instructions so that tests capture unexpected phrasing and assumptions. Turn reproducible user-reported problems into regression cases.

For test-case design, assertions, and repeatable evaluation, see [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview). For release checks, see [Responsible AI validation](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/rai-validation) and [Validate and test your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin).

## Related content

- [Build agents with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents)
- [Build agents with Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools#microsoft-365-agents-toolkit)
- [Write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions)
- [Add knowledge sources to your declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/knowledge-sources)
- [Confirmation prompts for MCP and API plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-confirmation-prompts)
- [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview)
- [Validation guidelines for agents](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/review-copilot-validation-guidelines)
