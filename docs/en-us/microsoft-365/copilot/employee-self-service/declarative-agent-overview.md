<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Introduction to Employee Self-Service Declarative Agents

Employee Self-Service declarative agents bring HR and IT self-service directly into Microsoft 365 Copilot. They provides prebuilt Copilot declarative agent templates that organizations can configure and extend to help employees find trusted information and complete supported tasks through connected enterprise systems.

Employee Self-Service declarative agents combine knowledge retrieval with workflows for employee actions. Organizations can start with Microsoft-provided scenarios and extend the agents to support additional employee-service needs.

Note

Access to Employee Self-Service declarative agents is rolling out in waves. Work with your Microsoft account team to determine availability for your organization.

## Technical architecture

Employee Self-Service is implemented as declarative agents that run within the Microsoft 365 Copilot experience. Learn more about [declarative agent architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-architecture).

The agents use Microsoft 365 Copilot orchestration and reasoning while connecting to organizational knowledge and enterprise systems for employee self-service scenarios.

The solution is designed so organizations can configure Employee Self-Service declarative agents for their environment without needing to build the core employee self-service experience from scratch.

At a high level, Employee Self-Service declarative agents bring together:

- Copilot Studio declarative agent templates
- Organizational knowledge sources
- Preconfigured employee-service scenarios
- Connections to supported enterprise systems
- Tools and samples for configuration and extensibility
- Response quality evaluation, diagnostics, and troubleshooting capabilities

## Knowledge and integration capabilities

Employee Self-Service declarative agents can use organizational knowledge and connect to supported enterprise systems.

**Knowledge sources**

- **SharePoint:** Organizational HR and IT knowledge.
- **ServiceNow knowledge:** ServiceNow knowledge base articles made available through the Microsoft 365 Copilot Graph connector. Learn more about [configuring ServiceNow knowledge](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-knowledge).

**Preconfigured employee-service scenarios**

Employee Self-Service declarative agents also include preconfigured scenarios for:

- **Workday:** Supported HR self-service workflows. Learn more about [integrating Workday](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday).
- **ServiceNow HRSD and ITSM:** Supported ServiceNow actions, including getting, creating, and updating cases, without requiring the Power Automate flows used in the Employee Self-Service custom engine agents. Learn more about [configuring ServiceNow HR and IT](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it).

Learn more about [Workday preconfigured scenarios](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday#supported-scenarios).

## Agent starter

Employee Self-Service agent starters are agent templates designed around specific domains, starting with HR and IT. Each starter gives you a ready-made foundation for a common set of employee scenarios, so you don't have to build an agent from scratch.

- **HR agent starter:** Helps employees quickly find answers and get guidance for common HR needs. Employees can look up policies, understand their benefits, and find relevant HR resources.
- **IT agent starter:** Helps employees solve common IT issues through guided troubleshooting and automated support. It can walk employees through tasks such as setting up a device, managing their account, and finding IT resources. The experience is designed to be clear and easy to follow while promoting safe practices that protect organizational data and systems.

- **Hub agent starter:** The Employee Self-Service Hub agent starter lets organizations bring together HR, IT, and other specialized agents into a single employee self-service experience. Employees can access capabilities from these agents through one central experience instead of having to find and interact with each agent separately.

  Learn more about [connecting multiple agents with the Hub agent starter](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub-declarative-agents).

## Billing and licensing requirements

Before you deploy Employee Self-Service declarative agents, verify that makers have access to Copilot Studio and that your organization meets the licensing and billing requirements for employee usage.

### Maker licensing requirements

To install, configure, and publish Employee Self-Service declarative agents, makers need access to Copilot Studio and the required permissions in the target Power Platform environment.

A Microsoft 365 Copilot license includes access to Copilot Studio to extend Microsoft 365 Copilot with agents. If your organization uses Copilot Studio user licenses instead, assign a **Copilot Studio User License** to each maker.

For license assignment instructions, see [Assign user licenses and manage access](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing). For other access options, see [Copilot Studio licensing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#get-started-in-copilot-studio).

### End-user licensing and billing requirements

Employee usage is billed based on the employee's Microsoft 365 Copilot license and the agent capabilities they use:

- **With a Microsoft 365 Copilot license:** Employee self-service agent usage is included in the license when the agent uses the authenticated employee's identity. Fair usage limits and exclusions apply.
- **Without a Microsoft 365 Copilot license:** Employee self-service agent usage consumes Copilot Credits. Configure pay-as-you-go billing or make Copilot Credit capacity available to the environment before you enable employee access.

Copilot Credit consumption depends on the capabilities used in each interaction. A single interaction can consume credits for more than one capability. For current rates, license inclusions, capacity limits, and usage monitoring, see [Billing rates and management](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-messages-management).

## Getting started

Before you get started, decide which Employee Self-Service agent starter you want to deploy first: HR or IT. You can use both starters as part of the same Employee Self-Service experience, but they must be deployed one at a time.

**Deployment:** Add the Employee Self-Service declarative agent package through Copilot Studio. We recommend starting in a sandbox environment so you can configure, test, and validate the agent before moving to production. When the agent is ready, use Copilot Studio to publish and deploy it to your users.

**Configuration:** The Employee Self-Service Agent Developer Kit \(ADK\) provides guided tools to help you set up, configure, validate, and troubleshoot your agent. ADK also includes FlightCheck, which can identify configuration issues early so you can address them before they block deployment. Learn more in the [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/developer-kit-overview).

**Security:** Employee Self-Service uses Microsoft enterprise security and identity capabilities to help protect your organization's data and control access. Organizations should review their identity, access, data, and compliance requirements as part of deployment.

Learn more about [security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/security-microsoft-365-copilot).

Use the following resources as you begin configuring and validating Employee Self-Service declarative agents.

- **Configure and troubleshoot with ADK:** Use the [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview) for setup, configuration, validation, and troubleshooting.
- **Plan your deployment:** Follow the [Employee Self-Service declarative agent deployment playbook](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deployment-playbook-declarative-agent) to plan your rollout and prepare for production.
- **Configure Workday:** Follow the [Workday integration guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday) to integrate Workday with the Employee Self-Service declarative agent.
- **Configure ServiceNow:** Follow the [ServiceNow knowledge setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-knowledge) and [ServiceNow HR and IT integration guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it) for supported ServiceNow scenarios.
- **Evaluate response quality:** Use the [Employee Self-Service declarative agent evaluation guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations) to build and run tests before moving into production pilot.
- **Monitor usage and feedback:** [Review usage and employee feedback in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-monitor-telemetry-feedback) after you publish your agent.

## Customization, scalability, and extensibility

Each agent starter comes with ready-to-use content and solution accelerators to help you get up and running faster. This includes:

- Agent name, logo, and description to give you a starting point for your agent.
- Instructions that define how the agent should respond and behave.
- Topics that help the agent handle specific types of employee questions and requests.
- Solution accelerators that make it easier to connect to external systems such as Workday.

Solution accelerators include prebuilt connectors and flows that help you integrate common business systems without starting from scratch.

The starters are also extensible in Copilot Studio, so you can customize the included experiences or add new scenarios based on your organization's needs.

Learn more about [customizing Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize).

## Language support

Employee Self-Service declarative agents use the native multilingual capabilities of Microsoft 365 Copilot. Organizations can configure additional languages for their agents.

English is currently the only language that has been formally validated for Employee Self-Service scenarios. If you plan to support additional languages, we recommend testing your knowledge sources, topics, and preconfigured actions in those languages before rolling out to employees.

## Use Employee Self-Service on mobile

Employee Self-Service is available on mobile through the Microsoft Copilot app on iOS and Android. This availability enables employees to access HR and IT support wherever they work.

If your organization enables Employee Self-Service on web, users can access Employee Self-Service on mobile by signing in to the Microsoft Copilot app and selecting the Employee Self-Service agent from the agent list.

No other configuration is required to enable mobile access.

Users should update to the latest version of the app if they're not able to see the Employee Self-Service agent.
