<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-checklist -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Microsoft 365 agents deployment checklist

This checklist is intended to assist admins with the successful deployment of Copilot agent governance. This checklist provides a comprehensive guide to help you understand, set up, manage, and deploy agents.

**Required administrators for the engagement**:

- **Microsoft 365 admin** - Setup Copilot agent and connectors settings.
- **Microsoft Power Platform admin** - Setup Copilot Studio policies and settings.
- **Microsoft 365 Search admin** - Setup Microsoft 365 Graph connector configurations.
- **Microsoft Azure admin** - Setup Azure subscription configurations.

**Deployment phases**:

[![Diagram of the Copilot agent deployment phases.](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/media/m365-agents-checklist/agent-deployment-phases.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/media/m365-agents-checklist/agent-deployment-phases.png#lightbox)

**Downloadable resources**:

- [Agents blueprint for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-blueprint)
- [Agents visual guide for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-visual-map)

## Manage Microsoft Copilot agent access and availability policies

Agent policies refer to the tenant settings you can make as an administrator in Copilot controls within Microsoft 365 admin center. Agent policies relate to the available settings for all agents in your tenant.

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Manage access to agents in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json#manage-access-to-copilot-agents) | Control how your users interact with agents:<br><br>- Choose who can access agents<br>- Choose which type of agents users are allowed to install | Copilot administrator, SharePoint administrator, Copilot Studio administrator |
| 2 | [Share and publish agents in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) | Agent sharing methods:<br><br>- [Sideload agents for personal use](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-policies/agent-sideload)<br>- [Shared agent with others](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-shared-agents?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json)<br>- [Publish custom agents to your organization](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json#publish-agents)<br>- [Submit agents to the marketplace](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-policies/agent-submit-marketplace) | Copilot administrator, SharePoint administrator, Copilot Studio administrator |

## Choose the right Copilot Studio experience

As an admin, you can configure and deploy out-of-the-box agents without having to create and publish a new agent. However, when your organization needs to customize Copilot functionality, members of your organization can create agents. Understand the different types of agents that can be created, shared, and deployed at your organization based on the method your organization uses to create agents.

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Choose the right Copilot Studio experience](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-experience) | Agent development tools:<br><br>- [Create SharePoint agents](https://support.microsoft.com/office/create-a-sharepoint-agent-d16c6ca1-a8e3-4096-af49-67e1cfdddd42)<br>- [Use Agent Builder to create declarative agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite)<br>- [Use Copilot Studio to create agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions?context=%2Fmicrosoft-365-copilot%2Fextensibility%2Fcontext)<br>- [Use Microsoft 365 Agents Toolkit to create agents](https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json) | Copilot administrator, SharePoint administrator, Copilot Studio administrator |
| 2 | [Plan your agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/planning-guide) | Define your objectives, technical requirements, costs, RAI considerations, and development approach. |  |
| 3 | [Consider licensing and cost options](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/cost-considerations) | Before you create an agent, consider the associated licensing and consumption costs. |  |
| 4 | [Set up your development environment](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/prerequisites) | If your creating a custom agent, consider how you set up your development environment. | Copilot administrator, SharePoint administrator, Copilot Studio administrator, Teams Administrator |

## Create agents in Agent Builder

Members of your organization can create declarative agents that they can share across your organization using Agent Builder. For more information, see [Create agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview).

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Understand Agent Builder creation process](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-build) | Quickly build declarative agents using natural language or by configuring the agent. | Copilot administrator, Microsoft 365 administrator |
| 2 | [Add knowledge sources to an agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-build#add-knowledge-sources) | Agent Builder allows end users to configure knowledge sources for the agent to reference. | Copilot administrator, Microsoft 365 administrator |
| 3 | [Add capabilities to an agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-build#add-capabilities) | Agent Builder allows end users to add and configure capabilities, such as the Code interpreter and Image generator. | Copilot administrator, Microsoft 365 administrator |
| 4 | [Share and manage agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-share-manage-agent) | End users can share and manage agents they create using Agent Builder. |  |
| 5 | [Download agent ZIP file and provide to admin](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-share-manage-agent#deploy-an-agent-via-zip-package) | Agent Builder provides an option to download a Zip file for manual deployment. | Copilot administrator, Microsoft 365 administrator |

## Understand application lifecycle management with Copilot Studio

Application lifecycle management \(ALM\) is the lifecycle management of applications and agents, which includes governance development and maintenance. You can implement ALM using Power Apps, Power Automate, Power Pages, Microsoft Copilot Studio, and Microsoft Dataverse. Key areas of ALM include governance, application development, and maintenance. For more information, see [Application lifecycle management \(ALM\) with Microsoft Power Platform](https://learn.microsoft.com/en-us/power-platform/alm/).

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Plan your environment strategy for your agent](https://learn.microsoft.com/en-us/power-platform/alm/environment-strategy-alm) | Understand environment principles related to ALM. | Microsoft Power Platform admin |
| 2 | [Understand solution concepts related to your agent](https://learn.microsoft.com/en-us/power-platform/alm/solution-concepts-alm) | Understand solution concepts related to ALM. | Microsoft Power Platform admin |
| 3 | Consider agent related change management and versioning | Understand agent related version control, changelog, and rollback procedures for agent deployments. | Microsoft Power Platform admin |
| 4 | [Understand key concepts for Copilot Studio security and governance](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance) | Understand security and governance controls and processes. | Microsoft Power Platform admin |
| 5 | [Understand key Copilot Studio configuration settings](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/sec-gov-config-settings) | Review tenant-level, environment-level, and agent-level settings in Copilot Studio. | Microsoft Power Platform admin |

## Create agents in Copilot Studio

When you need to provide powerful AI assistants that retrieve real-time insights and act on behalf of users, as well as create specialized workflows, you can use Copilot Studio to create custom agents.

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Understand how to extend Microsoft Copilot with agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions?context=%2Fmicrosoft-365-copilot%2Fextensibility%2Fcontext) | Learn how to create and configure a custom agent using Copilot Studio. | Copilot administrator, Microsoft 365 administrator |
| 2 | [Add knowledge sources](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio) | Knowledge sources allow your agents to provide relevant information and insights for your customers. | Copilot administrator, Microsoft 365 administrator |
| 3 | [Add tools](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-plugin-actions) | Tools expand the functionality of your agent, allowing it to perform various actions in response to user requests or autonomous triggers. | Copilot administrator, Microsoft 365 administrator |
| 4 | [Add other agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-add-other-agents) | Copilot Studio lets you enhance your agents by connecting them to other agents, allowing them to hand off user interactions or respond to autonomous triggers. | Copilot administrator, Microsoft 365 administrator |
| 5 | [Add topics](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-edit-topics) | A topic defines how an agent conversation progresses. | Copilot administrator, Microsoft 365 administrator |
| 6 | [Add triggers](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about) | Event triggers allow your agent to act autonomously in response to the defined event occurring. | Copilot administrator, Microsoft 365 administrator |
| 7 | [Publish an agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels) | You can publish agents to engage with your customers on multiple platforms or channels, such as live websites, mobile apps, Microsoft Copilot or messaging platforms like Teams and Facebook. | Copilot administrator, Microsoft 365 administrator |

## Manage Microsoft Copilot agent inventory and lifecycle

You can manage your organization's available agents by using Copilot controls within Microsoft 365 admin center.

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | [Setup Role-Based Access Control \(RBAC\) to manage Agents in M365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-agents-permissions) | Understand types of [admin permissions](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-prerequisites) to consider related to Copilot agents. | Copilot administrator, Microsoft 365 administrator |
| 2 | [Manage agent inventory for declarative agents created with Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) | You can manage your organization's available agents by using Copilot controls within Microsoft 365 admin center.<br><br>Actions include:<br><br>- [Manage shared agent](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-shared-agents)<br>- [Pin agents](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-pinning-agents) | Copilot administrator, Microsoft 365 administrator |
| 3 | Manage agent inventory for declarative and custom agents created with Copilot Studio | Your organization can manage agents created with Copilot Studio.<br><br>Actions include:<br><br>- [Manage requested agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-copilot-studio-requested)<br>- [Upload custom agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-upload-agents)<br>- [Manage agent inventory](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps#agent-inventory) | AI administrator, Global administrator, Global reader \(view-only, no edit\) |
| 4 | [Manage Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector) | Microsoft 365 Copilot connectors provide a platform for you to ingest your unstructured, line-of-business data into Microsoft Graph, so that Microsoft Copilot can reason over the entirety of your enterprise content.<br><br>Additional information:<br><br>- [Copilot connectors requirements](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector#requirements-for-copilot-connectors)<br>- [Set up Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector)<br>- [Staged rollout for Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoftsearch/staged-rollout-for-graph-connectors)<br>- [Customize connector configuration](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#step-4-customize-connector-configuration-optional) | Copilot administrator, Microsoft 365 administrator |
| 5 | Assign and deploy an agent | For more information, see [Manage agent inventory](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps#agent-inventory). | Copilot administrator, Microsoft 365 administrator |

## Manage Data Access - Data security, compliance, and governance

Effective governance and security are essential for managing Copilot agents across your enterprise. For more information see, [Governance and security best practices overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/sec-gov-intro).

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | Manage agent access to third-party systems | Managing agent access to third-party systems include the following:<br><br>- [M365 Copilot connectors usage](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector)<br>- [Power Platform connectors](https://learn.microsoft.com/en-us/connectors/overview)<br>- [Microsoft Graph connector agent for on-premises data](https://learn.microsoft.com/en-us/microsoftsearch/graph-connector-agent) | GCA machine administrator, Search administrator, or Copilot administrator |
| 2 | Manage oversharing of SharePoint content | Understand oversharing by reviewing the following resources:<br><br>- [Microsoft Copilot with SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/get-ready-copilot-sharepoint-advanced-management)<br>- [Microsoft Purview Data Security Posture Management \(DSPM\) for AI](https://learn.microsoft.com/en-us/purview/dspm-for-ai?tabs=m365)<br>- [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance) | Microsoft Entra ID Compliance administrator, Microsoft Entra ID Global administrator, Microsoft Purview Compliance administrator, SharePoint Online administrator |
| 3 | Manage auditing and reporting | Understand auditing and reporting by reviewing the following resources:<br><br>- [Audit log for Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-logging-copilot-studio)<br>- [Use Microsoft Purview Data Security Posture Management \(DSPM\) for AI](https://learn.microsoft.com/en-us/purview/data-security-posture-management-get-started)<br>- [Configure Microsoft Sentinel to ingest the audit logs](https://learn.microsoft.com/en-us/azure/sentinel/relate-alerts-to-incidents?toc=/copilot/microsoft-365) | Security administrator |
| 4 | Manage data security | Understand data security by reviewing the following resources:<br><br>- [Information Protection](https://learn.microsoft.com/en-us/purview/information-protection)<br>- [Data loss prevention \(DLP\)](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) | Security administrator |
| 5 | Manage data compliance | Understand data compliance by reviewing the following resources:<br><br>- [Compliance Manager](https://learn.microsoft.com/en-us/purview/compliance-manager)<br>- [Communication Compliance](https://learn.microsoft.com/en-us/purview/communication-compliance-copilot)<br>- Search Copilot and agent data<br><br>  - [eDiscovery](https://learn.microsoft.com/en-us/purview/ediscovery-search-and-delete-copilot-data)<br>  - [Audit Log](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-logging-copilot-studio)<br>  - [Purview DSPM for AI](https://learn.microsoft.com/en-us/purview/data-security-posture-management-get-started)<br><br>- [Retention policy support for Copilot](https://learn.microsoft.com/en-us/purview/retention?tabs=table-overriden) | Security administrator, Communication Compliance administrator, Communication Compliance investigators, Communication Compliance analysts |

## Manage pay-as-you-go billing and Copilot Capacity Pack

The Microsoft Copilot pay-as-you-go plan offers a flexible and cost-effective way for organizations to access Copilot services.

| Step | Task | Description | Administrator |
| --- | --- | --- | --- |
| 1 | Understand Copilot licensing | As part of your Microsoft Copilot adoption, make sure you have the right Microsoft 365 subscription plan. For more information, see the following resources:<br><br>- [Microsoft Copilot license options](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing)<br>- [Copilot Studio license options](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing) |  |
| 2 | [Understand Microsoft Copilot pay-as-you-go plan](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview) | The Microsoft Copilot pay-as-you-go service offers a usage-based option for organizations to access Copilot services, like Microsoft Copilot Chat. For more information, see the following resources:<br><br>- [Set up pay-as-you-go for Microsoft Copilot services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup)<br>- [Use Copilot Studio prepaid capacity packs for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs)<br>- [View costs and billing for Microsoft Copilot pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/view-cost) | Global administrator, Billing administrator, AI administrator |
| 3 | [Understand Copilot Studio billing rates and management](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management) | There are rates for the different features and capabilities used in agents. For more information, see the following resources:<br><br>- [Set up Copilot Studio pay-as-you-go consumptive meter](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management#set-up-pay-as-you-go-consumptive-meter)<br>- [View Copilot Credit consumption](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management#view-copilot-credit-consumption)<br>- [Copilot Studio Agent Consumption Estimator](https://microsoft.github.io/copilot-studio-estimator/)<br>- [Understand Copilot Credit event scenarios](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management#copilot-credits-and-events-scenarios) |  |
| 4 | [Microsoft Copilot agent usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-agents) | You can view the adoption of agents in Microsoft Copilot in your organization using Microsoft 365 reports in the admin center. |  |
