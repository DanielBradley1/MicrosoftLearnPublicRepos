<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-customer-insight -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Use the Customer Insight Assistant template to build an agent

You can use the Customer Insight Assistant template in Microsoft 365 Copilot to build agents that help teams understand their customers by providing relevant information and insights. Agents based on this template deliver detailed customer profiles, including the customer's main industry, top products or services, corporate ethos, key priorities, main business units, senior leadership, main competitors, and industry trends. If the customer is publicly traded, the agent provides the stock symbol and stock price over the past year.

## Prerequisites

Before you work with the template, make sure that you have:

- A working knowledge of how to [build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents).
- An understanding of how to [write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

## Capabilities

The Customer Insights agent is designed to provide the information you need to help you better engage with your customers. Agents built on this template deliver detailed customer profiles that include the customer's:

- Industry
- Top products or services
- Mission and vision
- Key priorities
- Primary business units
- Senior leadership
- Chief competitors
- Industry trends
- Stock symbol and stock price over the past year

## Use cases

A Customer Insight agent can be useful for the following scenarios.

| **Scenario** | **Description** |
| --- | --- |
| Customer insights | Provides detailed insights about customers, including industry trends and competitive analysis. |
| Customer initiatives | Identifies a customer's key initiatives. |
| Partnering | Suggests ideas for engaging customers through partnership opportunities. |
| Regional insights | Provides a breakdown of the number of employees a customer has in each region. |
| Customer feedback | Compares how your customers feel about your company relative to your competitors. |
| Customer support | Offers suggestions on how to better support customers. |

## Extension opportunities

You can enhance the functionality of your Customer Insights Assistant agents in a number of ways. For example, you can:

- **Target relevant enterprise data:** Connect the agent to a SharePoint document library that contains information on how to engage with customers and that provides best practices on how to move the relationship forward.
- **Connect to your \(CRM\) solution:** Use a Power Platform Connector an API plugin to provide your agent access to details about your key account and customer contacts as well as to relevant products and projects. \(Typically, CRM integration requires collaboration with your organizations service owners and IT department.\)
- **Simplify creating customer materials:** Integrate the Customer Insight agent in Word and PowerPoint to help create targeted presentations, marketing materials, etc.

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
