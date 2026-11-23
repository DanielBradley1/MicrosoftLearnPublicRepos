<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-learning-coach -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Use the Learning Coach template to build an agent

You can use the Learning Coach template in Microsoft 365 Copilot to build an agent that helps users understand complex topics by breaking them down into simple, intermediate, and detailed summaries. Learning Coach agents create structured learning plans and help users practice skills and prepare for tests. Theses agents provide tailored exercises, guide optimal learning processes, and offer interactive language practice.

To try a Learning Coach, [install the Learning Coach agent](https://teams.microsoft.com/l/app/78079743-a11b-45d0-99cb-a69d37717373?source=share-app-dialog).

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Learning Coach agents empower users to achieve their learning goals through structured guidance and support. Key agent capabilities include:

- Crafting tailored learning plans and exercises based on individual knowledge gaps, study preferences, and learner goals.
- Breaking complex topics into digestible summaries at simple, intermediate, and detailed levels for enhanced learner comprehension.
- Providing targeted exam preparation guidance, recommendations for educational resources, and interactive language practice.

## Use cases

Learning Coach agents are useful in the following scenarios.

| **Scenario** | **Description** |
| --- | --- |
| Content comprehension | Helps learners comprehend complex topics by breaking them down into simpler chunks. |
| Knowledge reinforcement | Guides learners through exercises on the skills and knowledge that they already have. |
| Learning plan customization | Helps create tailored learning plans to best fit the needs of the user by assessing the learner's existing knowledge and asking questions about their preferred approach to learning. |
| Test preparation | Helps learners prepare for academic and certification exams. |
| Language education | Facilitates learning new languages based on the user's current knowledge. |
| Study techniques | Suggests personalized study techniques to the user. |

## Extension opportunities

You can enhance the functionality of your Learning Coach agents by connecting to additional resources via Microsoft 365 Copilot connectors, Power Platform connectors, or API plugins, depending on the source system in use. The following are some ideas:

- **Link with your Learning Management System \(LMS\):** Link with your preferred LMS or Massive Open Online Course \(MOOC\) platforms to source up-to-date content, track progress, and streamline certification pathways.
- **Leverage internal knowledge repositories:** Connect your Learning Coach to a SharePoint document library that contains company training materials, research papers, or best practices. This allows the agent to provide contextualized learning recommendations based on your organization's proprietary content.

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
