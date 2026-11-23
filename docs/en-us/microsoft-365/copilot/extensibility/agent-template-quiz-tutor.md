<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-quiz-tutor -->
<!-- Sitemap-Last-Modified: 2026-01-07 -->

# Use the Quiz Tutor template to build an agent

You can use the Quiz Tutor template in Microsoft 365 Copilot to build agents that provide fun, bite-sized quizzes based on predefined training content. These quizzes can even be interactive to make the learning process more engaging. The template is designed to enhance a user's understanding and retention of the material by using varied and interesting questions and providing coaching and feedback to support learning.

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Quiz Tutor agents help users learn quickly. For example, these agents support multiple languages and can:

- Create fun and engaging quizzes based on the associated training content.
- Provide coaching on answers, praise for correct answers, with offers to explain incorrect answers.
- Adapt the difficulty of the questions based on user performance.
- Use clear language, not technical jargon.

## Use cases

Quiz Tutor agents are useful for the following scenarios.

| **Scenario** | **Use case** |
| --- | --- |
| Onboarding new employees | Create interactive quizzes related to your organization's policies and key information. |
| Product training | Test employee knowledge of new products and services. |
| Compliance training | Create quizzes to cement employee knowledge of regulatory requirements and policies. |
| Skill development | Help employees develop and improve their skills. |
| Customer Service training | Quiz employees on best practices for various customer service scenarios. |
| Continuous learning | Help employees learn about industry trends and new technologies. |

## Extension opportunities

You can enhance the functionality of your Quiz Tutor agents by:

- **Scoping your agent to a particular training or topic:** Connect a SharePoint site or files that contain training materials for a specific topic to create a Quiz Tutor agent specialized for a particular course.
- **Linking with a Learning Management System \(LMS\):** Link with your preferred LMS to provide robust support for both recommending and registering for relevant courses, certifications, and workshops based on the user's role, experience, and aspirations.

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
