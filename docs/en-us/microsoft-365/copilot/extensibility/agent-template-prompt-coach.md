<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-prompt-coach -->
<!-- Sitemap-Last-Modified: 2026-01-07 -->

# Use the Prompt Coach template to build an agent

You can use the Prompt Coach template in Microsoft 365 Copilot to build agents that help new Copilot users create effective prompts. Acting as a supportive teacher, these agents guide users through prompt generation, analysis, and improvement. Key features include helping users create well-structured prompts, providing feedback, ensuring compliance with Responsible AI guidelines, troubleshooting, and suggesting examples. The goal is to help users articulate requests clearly for optimal Copilot responses.

To try Prompt Coach, [Install the Prompt Coach agent](https://teams.microsoft.com/l/app/90680790-0a82-47bf-bab3-6c60c4221d1d?source=share-app-dialog).

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Agents built on this template provide:

- Interactive prompt guidance to help users develop well-structured prompts through an iterative feedback process that help clarify user goals, context, and expectations.
- Detailed prompt analysis that evaluates and helps refine user prompts to ensure clarity, optimal phrasing, and compliance with Responsible AI guidelines.
- Concrete prompt examples, with step-by-step explanations, to help users understand and apply AI prompt engineering best practices.

## Use cases

Prompt Coach agents are optimized for the following tasks.

| **Task** | **Description** |
| --- | --- |
| Prompt creation | Helps users create effective prompts. |
| Prompt analysis | Evaluates user prompts and offers detailed suggestions for improvement. |
| Prompt Compliance | Checks to determine whether prompts follow Responsible AI guidelines. |
| Prompt Correction | Analyzes and fixes problematic prompts, providing more context for better results. |
| Prompt Examples | Provides well-structured prompt examples and explains their purpose, context, sources, and expectations to help users learn to improve their own prompts. |
| Prompt Engineering | Helps tailor prompts to accomplish a particular task by iterating over a prompt and making incremental changes. |

## Extension opportunities

You can further enhance your Prompt Coach agents with integrations such as the following:

- **Contextual resources:** Connect your Prompt Coach to SharePoint or other document repositories that contain domain information, prompt guidelines, and your organization's best practices for Responsible AI.
- **Prompt libraries:** Add connectors to pull from prompt repositories across your organization to enable and encourage prompt sharing and collaborative learning about how to write more effective prompts.

Note

Adding connections typically requires collaboration with the service owners and IT admins. Some functionality might be available only for users in tenants with metered usage or users with Microsoft 365 Copilot licenses.

## Limitations

The following limitations apply to this template:

- **Interacting with the agent:** Agents created with this template are designed to answer one question at time. For best results, users shouldn't ask multiple or compound questions in a single prompt.
- **Handling sensitive information:** When you create agents with this template, it's your responsibility to ensure that any personal or sensitive information used in the agent is handled according to your organization's data privacy policies.
- **Incorrect or harmful responses:** Although agents based on this template are designed to prevent the output of incorrect and harmful content, these agents use generative AI technology, which can sometimes make mistakes. A disclaimer is included to remind users to verify accuracy before making decisions, especially financial decisions. Customers are responsible for conducting due diligence on AI-generated content. You can edit the disclaimer to align with your organization's policies, but we don't recommend removing it. For more information, review the [supplemental terms](https://www.microsoft.com/business-applications/legal/supp-powerplatform-preview/).

## Related content

- [Agent Builder in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder)
- [Build agents with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents)
- [Publish and manage agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents)
