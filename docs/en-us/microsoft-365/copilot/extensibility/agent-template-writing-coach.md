<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-writing-coach -->
<!-- Sitemap-Last-Modified: 2026-01-07 -->

# Use the Writing Coach template to build an agent

You can use the Writing Coach template in Microsoft 365 Copilot to build agents that help users improve their writing skills and complete various writing tasks. Acting as a supportive coach, agents based on the Writing Coach template provide detailed feedback on clarity, coherence, grammar, and tone. These agents help users modify the nuance and tone of messages, translate text, and guide users through writing instructions, stories, and whitepapers.

To try a Writing Coach, [install the Writing Coach agent](https://teams.microsoft.com/l/app/f72d7797-c6ee-4fd3-9454-028d0095068b?source=share-app-dialog).

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents with Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Writing Coach agents can:

- Provide detailed feedback on clarity, coherence, grammar, and tone to elevate overall writing quality.
- Help transform casual text and narratives into formal documents, such as instructions and whitepapers.
- Offer specific suggestions to help adjust the tone or style of a document, or make it easier to translate a document into other languages.

## Use cases

Writing Coach agents can provide helpful guidance for the following types of tasks.

| **Type of guidance** | **Description** |
| --- | --- |
| Writing refinement | Provides a wide range of suggestions to help users refine their writing. Suggestions can include: ways to improve grammar, clarity, coherence, and key concepts and details to focus on. |
| Audience targeting | Suggests ways to tailor the voice and tone, and details of a document to your target audience. The agent provides examples of the suggested changes. |
| Writing for a global audience | Identifies wording that might be culturally sensitive and offers alternatives. |
| Descriptive and procedural | Provides feature descriptions as well as clear and concise instructions for using products and services. |
| Customer story writing | Asks for customer details and story goals, then provides suggestions for structuring the story with a clear beginning, middle, and end. |
| Creating whitepapers | Provides assistance in identifying the audience, generating topics, and structuring the document. |

## Extension opportunities

You can further enhance your Writing Coach agents with integration. For example:

- **Contextual content integration:** Connect your Writing Coach to SharePoint or other document repositories containing internal style guides, best practices, and historical writing examples. Doing this allows the agent to provide more personalized and context-aware recommendations.
- **Application integration:** Customize and configure your Word and PowerPoint implementations to let users access your Writing Coach from within those applications.

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
