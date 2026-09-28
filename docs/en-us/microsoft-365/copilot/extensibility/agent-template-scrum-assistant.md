<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-scrum-assistant -->
<!-- Sitemap-Last-Modified: 2026-01-07 -->

# Use the Scrum Assistant template to build an agent

You can use the Scrum Assistant template in Microsoft 365 Copilot to build agents that support scrum masters and Agile teams by providing real-time guidance on scrum ceremonies, backlog management, and Agile best practices. Agents based on this template apply trusted scrum resources, analyze team artifacts \(sprint reports, retrospective notes\), and offer data-driven recommendations to enhance team performance, collaboration, and operational efficiency.

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents with Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Scrum Assistants support multiple languages and can:

- Provide real-time guidance on scrum ceremonies, backlog management, and best practices for Agile development.
- Use trusted scrum resources and team artifacts to offer data-driven recommendations.
- Help teams improve performance, collaboration, and efficiency.

## Use cases

Scrum Assistant agents are useful in the following scenarios.

| **Scenario** | **Description** |
| --- | --- |
| Improve operational efficiency | Helps reduce inefficiencies and support continuous improvement with suggestions for streamlining scrum ceremonies and improving sprint execution. |
| Boost productivity | Fetches relevant scrum insights automatically to enable teams to focus on their deliverables. |

## Extension opportunities

You can enhance the functionality of your Scrum Assistant agents by:

- **Referencing company-specific Agile practices:** Connect a SharePoint site or files that contain company-specific Agile practices that are stored internally to align guidance with your organizational standards.
- **Linking with your learning materials:** Use Microsoft 365 Copilot connectors or APIs to index data about your team's Azure DevOps work items. This way, you can allow your Scrum Assistant to provide more contextual advice and guidance.

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
