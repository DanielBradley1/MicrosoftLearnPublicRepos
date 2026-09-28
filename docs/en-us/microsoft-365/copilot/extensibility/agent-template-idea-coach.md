<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-idea-coach -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Use the Idea Coach template to build an agent

You can use the Idea Coach template in Microsoft 365 Copilot to build an agent that helps users develop and refine their ideas and enhance their brainstorming sessions. The Idea Coach agent template uses a fun, collaborative tone to inspire creativity and ensure engaging and productive brainstorming interactions. Idea Coach agents gather user feedback to continuously improve the brainstorming experience.

By acting as a personal assistant, an agent based on the Idea Coach template can help users:

- Generate ideas and topics
- Plan brainstorming sessions
- Find creative brainstorming exercises
- Organize ideas
- Improve their brainstorming skills

To try an Idea Coach, [install the Idea Coach agent](https://teams.microsoft.com/l/app/03386cc1-d424-4eaa-95a8-4a8ec605190e?source=share-app-dialog).

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents with Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Agents built on this template can:

- Provide AI-driven brainstorming through a guided dialogue and creative exercises to help users effectively develop and refine their ideas.
- Customize agendas and exercises for brainstorming sessions based on user input to ensure engaging and productive brainstorming sessions.
- Collect session insights and feedback to iteratively enhance brainstorming techniques and creative outcomes.

## Use cases

An Idea Coach agent can help with the following scenarios.

| **Scenario** | **Description** |
| --- | --- |
| Brainstorming Assistance | Provides a question-based dialogue to help users brainstorm ideas. |
| Brainstorm Session Planning | Customizes brainstorming session agendas by gathering context and offering creative suggestions. |
| Creative Exercises | Proposes activities tailored to user goals and session details. |
| Idea organization | Provides unbiased tools for prioritizing ideas. |
| Feedback and Improvement | Collects session feedback and makes recommendations for improving the brainstorming session. |
| Training and Development | Helps users grow their brainstorming skills. |

## Extension opportunities

You can further enhance your Idea Coach agents through integration and added intelligence. For example, you can:

- **Connect to additional knowledge base sources:** Link to internal wikis, research repositories, or material from past brainstorming sessions to allow your Idea Coach to access relevant insights and historical context.
- **Scope your agent to specific materials:** Connect a SharePoint site or files containing the specific materials you want your agent to work from.
- **Whiteboarding, CRM, and Project Management tool integrations:** Sync with whiteboarding tools like Microsoft Whiteboard for visualizing ideas. Then, translate refined ideas into actionable tasks by moving them to project management tools like Planner.
- **Automate meeting summaries:** Generate concise summaries of brainstorming sessions, capturing key takeaways, decisions, and next steps.

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
