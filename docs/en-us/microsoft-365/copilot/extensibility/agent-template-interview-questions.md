<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-interview-questions -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Use the Interview Question Assistant template to build an agent

You can use the Interview Question Assistant template in Microsoft 365 Copilot to build an agent that supports hiring managers and interviewers by streamlining the process of drafting high-quality interview questions. This agent helps you quickly create effective interview questions.

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

The Interview Question Assistant supports multiple languages and can:

- Help create effective and relevant interview questions that are:

  - Tailored to specific roles and job descriptions.
  - Clear, concise, and aligned to the given job requirements.

- Adapt the complexity of suggested interview questions based on the level of the specified position.
- Generate both questions and sample answers based on the job descriptions the user provides.
- Provide guidance on best practices for interviewing, such as offering tips on how to frame questions to assess various competencies and skills.

## Use cases

Interview Question Assistant agents are useful for the following scenarios.

| **Scenario** | **Description** |
| --- | --- |
| General interview preparation | Offers guidance on what makes a good interview question and how to create interview questions. |
| Role-specific interview preparation | Provides tailored interview questions and sample answers for specific roles, such as software developer positions or sales jobs. |
| Template-based question generation | Uses existing templates to create interview questions for a variety of roles. |
| Team coordination | Helps interview teams coordinate and align their questions. |
| Interviewer training | Helps new interviewers understand best practices and guidelines for conducting interviews. |
| Continuous improvement | Provides feedback and suggestions for improving interview questions based on past interviews and outcomes. |

## Extension opportunities

You can enhance the functionality of your Interview Question Assistant agents by connecting to additional resources via Microsoft 365 Copilot connectors, Power Platform connectors, or API plugins, depending on the source system in use. The following are some ideas:

- **Scope your agent to a particular topic:** Connect a SharePoint site or files containing content relevant to the topic to create specialized Interview Assistant agents.
- **Link to your interview training materials:** To expand your Interview Assistant's knowledge base and increase its usefulness, connect your Interview Assistant to your interview training tools.

Note

Adding connections typically requires collaboration with the service owners and IT admins. Some functionality might be available only for users in tenants with metered usage or users with Microsoft 365 Copilot licenses.

## Limitations

The following limitations apply to this template:

- **Interacting with the agent:** Agents created with this template are designed to answer one question at time. For best results, users shouldn't ask multiple or compound questions in a single prompt.
- **Handling sensitive information:** When you create agents with this template, it's your responsibility to ensure that any personal or sensitive information used in the agent is handled according to your organization's data privacy policies.
- **Incorrect or harmful responses:** Although agents based on this template are designed to prevent the output of incorrect and harmful content, these agents use generative AI technology, which can sometimes make mistakes. A disclaimer is included to remind users to verify accuracy before making decisions, especially financial decisions. Customers are responsible for conducting due diligence on AI-generated content. You can edit the disclaimer to align with your organization's policies, but we don't recommend removing it. For more information, review the [supplemental terms](https://www.microsoft.com/business-applications/legal/supp-powerplatform-preview/).

- This agent doesn't provide interview advice. The answers provided are based on configured knowledge sources or general knowledge and don't reflect the opinions of Microsoft.
- While the agent can generate questions based on templates and job descriptions, it might not fully capture the unique nuances of every role. Customize questions as needed.
- Ensure that the interview questions generated comply with local labor laws and regulations.

## Related content

- [Agent Builder in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder)
- [Build agents with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents)
- [Publish and manage agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents)
