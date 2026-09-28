<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-career-coach -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Use the Career Coach template to build an agent

You can use the Career Coach template in Microsoft 365 Copilot to build an agent that provides personalized suggestions and action plans to help users advance in their careers. The career coach offers tailored advice on skill development, learning opportunities, and career transitions based on the user's current role, experience, and available learning opportunities.

The Career Coach uses a professional and supportive tone to make interactions contextually relevant and encouraging.

To try a Career Coach, [install the Career Coach agent](https://teams.microsoft.com/l/app/89b7d7a3-fae0-47d7-8140-a38efe34510f?source=share-app-dialog).

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents with Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Agents built on the Career Coach template can offer:

- Personalized career roadmapping that includes detailed career development plans and actionable advice based on the user's role, skills, and career aspirations.
- Comprehensive skill gap analysis to identify target areas for growth and recommendations for tailored learning opportunities.
- Holistic career support, including guidance on career transitions, performance improvement, and strategic networking.

## Use cases

Career Coach agents are useful for the following tasks.

| Task | Description |
| :--- | :--- |
| Career development plans | Helps create detailed plans based on your current role and your career goals. |
| Skill gap analysis | Identifies gaps between your current skills and your career goals and then suggests ways to address them. |
| Learning opportunities | Recommends courses, certifications, and workshops to help you grow. |
| Career transition advice | Provides guidance for successfully changing careers. |
| Networking strategies | Offers tips for growing and making the most of your professional network. |
| Performance improvement | Provides advice about how to improve your performance in your current role. |

## Extension opportunities

You can enhance the functionality of your Career Coach agents by connecting to additional resources via Microsoft 365 Copilot connectors, Power Platform connectors, or API plugins, depending on the source system in use.

Suggestions for such connections include:

- **Linking with a Learning Management System \(LMS\):** Link with your preferred LMS to provide robust support for both recommending and registering for relevant courses, certifications, and workshops based on the user's role, experience, and aspirations.
- **Integrating with your HR and Talent Management Systems:** Provide more helpful and personalized responses by connecting the agent to internal HR databases or talent management systems.

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
