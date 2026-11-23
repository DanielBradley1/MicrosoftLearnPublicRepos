<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-skills -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Skills as plugin capabilities

During **Prepare**, choose a skill when you need instructions and resources for a repeatable task. This page helps you select the implementation for the experience where the task runs. You finish with a skill design, the applicable product procedure, and the dependencies to carry into **Build or reuse**.

A skill uses a required `SKILL.md` file and can include supporting resources or scripts. The target product determines which files, execution behavior, packaging, and distribution methods it supports. A shared file format doesn't establish cross-agent reuse or cross-host support.

Important

Skill availability, sharing, automatic use, and host support vary by Microsoft experience. Skills can be used directly in Copilot Chat, distributed through supported plugins, or attached to declarative agents. Follow the guidance for the authoring experience and target host; their packaging requirements and limits aren't interchangeable.

## Choose the target experience

| Target | Start with |
| --- | --- |
| A skill used directly in Microsoft 365 Copilot Chat, including a skill distributed in a plugin | [Build skills for Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-copilot-chat-skills) |
| A skill in a Copilot Cowork plugin | [Build plugins for Copilot Cowork](https://learn.microsoft.com/en-us/copilot/cowork/cowork-plugin-development) |
| A skill attached to a declarative agent | [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills) |

## Decide whether you need a skill

Choose a skill when you can define the job, expected inputs, output, and boundaries as task-specific instructions. Keep those instructions separate from the agent's general behavior.

Choose a different capability when you primarily need:

- A complete conversational experience: consider a [declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent).
- External organizational content: compare [Copilot connectors \(synced or federated\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-connectors).
- Remotely hosted tools: consider an [MCP server](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-type-mcp-servers).

Don't assume a skill script can access the network, install packages, or call authenticated services. Check the runtime rules for the selected product before designing its dependencies.

## Choose the skill implementation

| Where the task runs | Product guidance | What to decide here |
| --- | --- | --- |
| A declarative agent in Microsoft 365 Copilot | [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills) | Choose [Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills) or [Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills), then use that route's file and package limits. |
| Copilot Cowork | [Build plugins for Copilot Cowork](https://learn.microsoft.com/en-us/copilot/cowork/cowork-plugin-development) and its [companion file limits](https://learn.microsoft.com/en-us/copilot/cowork/cowork-plugin-development#companion-file-limits) | Use the Cowork skill and plugin requirements, not declarative-agent limits. |
| A new source-controlled plugin | [Build a plugin with Work IQ Dev Tools](https://microsoft.github.io/wiqd/getting-started/build-a-plugin/) and the [plugin authoring reference](https://microsoft.github.io/wiqd/getting-started/plugin-reference/) | Distinguish a top-level plugin skill from a skill added to an existing declarative-agent project. Verify the intended product's runtime separately. |

The [declarative-agent support matrix](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#support-matrix) lists **Reuse across agents: Not supported** for Agent Builder and Agents Toolkit. Don't plan to attach one agent's skill to another as a supported reuse workflow.

Excel custom skills are stored in OneDrive, not in the plugin registry. These are separate product routes; don't infer registry distribution or other hosts' storage and availability from the use of `SKILL.md`.

For declarative-agent skills, the product reference also owns the [script sandbox rules](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#script-execution-sandbox), storage, sensitivity behavior, and file limits. Use the Cowork reference for Cowork constraints instead of applying those rules across products.

## Record the design and dependencies

Before handing off to the product's build steps, record:

- The job, inputs, expected output, and representative success and failure cases.
- The intended agent or product, authoring tool, and supported skill format.
- The resources and scripts needed, and whether the target runtime supports them.
- Any Copilot connector \(synced or federated\), remote MCP tool, or Power Platform connector dependency, using the precise type.
- Required authentication, permissions, data, and external services.
- The content owner, version, support contact, review requirements, and test plan.
- The supported publishing route for the exact artifact.

Independent software vendors can submit declarative agents that include skills through Partner Center, as described in [Publish your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills#publish-your-agent). That published route doesn't establish eligibility for every standalone skill or composed plugin package.

## Next step

Finish **Prepare** by [choosing development tools](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools), then enter **Build or reuse** through the selected product's skill procedure above.
