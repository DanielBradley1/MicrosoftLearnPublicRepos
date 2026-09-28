<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-meeting-coach -->
<!-- Sitemap-Last-Modified: 2026-01-07 -->

# Use the Meeting Coach template to build an agent

You can use the Meeting Coach template in Microsoft 365 Copilot to build agents that help meeting organizers create and run effective meetings. Agents based on the Meeting Coach template can help users:

- Set clear objectives
- Create structured agendas
- Assign meeting roles
- Prepare meeting invitations
- Keep meetings on track
- Encourage participation
- Assign action items

Agents built from this template help ensure that meetings are productive, engaging, and well organized.

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents with Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

Agents built on the Meeting Coach template can help meeting organizers:

- Create agendas.
- Prepare invite emails.
- Assign meeting roles.
- Prepare invite emails.
- Take meeting notes.

Organizers can also use these agents during meetings to keep them on track and encourage participation.

## Use cases

Meeting Coach agents are useful for the following types of meetings.

| **Meeting type** | **Purpose** |
| --- | --- |
| Strategic planning | Define an organization's strategic direction. |
| Stakeholder engagement | Gather stakeholder input and make critical organizational decisions. |
| Innovation workshops | Brainstorm new ideas and innovative strategies. |
| Review sessions | Ensure open and honest communication about successes and areas of improvement, even for challenging topics. |
| Sales pitches | Present an organization's products and services to make sales. |

## Extension opportunities

You can enhance the functionality of your Interview Question Assistant agents by connecting to additional resources via Microsoft 365 Copilot connectors, Power Platform connectors, or API plugins, depending on the source system in use. The following are some ideas:

- **Connect to your \(CRM\) solution:** Use a Power Platform Connector an API plugin to give your agent access to details about your key accounts and customer contacts as well as to relevant products and projects.
- **Increase customer engagement:** Connect your agents to SharePoint sites that include meeting materials \(sales pitches, customer information, etc.\) you can create an agent specialized for customer follow-up.
- **Standardize meetings across teams:** By connecting SharePoint sites that include template files \(agendas, meeting minutes, etc.\), you can standardize how meetings are organized. You can also standardize how action items and results are recorded and reported at the end of the meeting.

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
