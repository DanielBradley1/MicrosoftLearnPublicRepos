<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/rai-faq -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Responsible AI FAQ for the Employee Self-Service agent

This FAQ covers the Employee Self-Service custom engine agent and declarative agent experiences. Their architecture, templates, configuration, and supported capabilities differ. A statement about one experience doesn't automatically apply to the other. For Microsoft platform-wide information, see [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy) and [Responsible AI FAQs for Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/responsible-ai-overview).

## What is Employee Self-Service intended to do?

Employee Self-Service helps employees find organization-specific HR and IT information and complete supported employee-service tasks. The available knowledge sources, actions, and integrations depend on the experience, template, product availability, and the configuration enabled by the organization.

- [Introduction to the Employee Self-Service Custom Engine Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/overview)
- [Introduction to Employee Self-Service Declarative Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)

Employee Self-Service isn't a substitute for decisions by HR, IT, legal, or other qualified personnel. Organizations should define a path to a qualified person for requests that require human judgment or fall outside the agent's configured scope.

## What can Employee Self-Service do?

Employee Self-Service can retrieve information from configured knowledge sources and support tasks provided by the selected experience and enabled integrations. The custom engine agent and declarative agent templates don't necessarily have the same features or configuration options. Review the documentation for the experience and template you're deploying instead of assuming a capability is available in both.

- For the custom engine agent, see [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations).
- For the declarative agent, see [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent).

## How was Employee Self-Service evaluated?

The published custom engine agent guidance reports that Microsoft manually red-teamed more than 200 prompts for discrimination, harassment, abuse, and other sensitive scenarios, with zero defects identified in the tested configuration. The stated conditions include the default Employee Self-Service configuration and the sensitive-topic behavior enabled.

This result describes only the configuration and scenarios stated in that evaluation report. It isn't evidence for the declarative agent, an organization-customized configuration, every supported scenario, or a later product version. Organizations should validate the experience and scenarios they configure. For custom engine agent evaluation guidance, see [Response quality evaluations for the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations). For declarative agent evaluation guidance, see [Agent evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations).

## How does the sensitive-topic behavior work?

The published sensitive-topic description applies to the custom engine agent starter. It describes a customizable topic that is disabled by default and responds to certain sensitive requests with a predetermined response. Verify the topic and its enabled state in the package you're using; don't assume the same topic or default behavior exists in a declarative agent template.

For configuration guidance, see [Customize the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/customize) for the custom engine agent or [Customize Employee Self-Service](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize) for the declarative agent.

## How does the emotional-intelligence topic work?

The published description of the **Seek emotional intelligence** topic applies to the custom engine agent starter. It describes a customizable topic intended to make responses more empathetic and says that the topic doesn't infer mental health conditions, store emotional states, or profile users. Confirm whether the topic is present and enabled in the package you're deploying. Its behavior isn't a substitute for human care or decision-making.

Don't assume the custom engine agent topic or its behavior is present in declarative agents. Review the current declarative agent template and configuration guidance for the experience you're deploying.

## What are the limitations of Employee Self-Service?

AI-generated responses can be incomplete or inaccurate. Results also depend on the quality and availability of configured knowledge, the selected template, the user's access, and the setup of connected systems. Verify important policy or personal-data answers with the authoritative source or a qualified person, and provide a human support path for requests the agent can't resolve.

Copilot Studio platform behavior and limitations also affect agents built with it. Review [Responsible AI FAQs for Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/responsible-ai-overview) and the known issues for the Employee Self-Service experience you're using.

## What data can Employee Self-Service access?

Data access depends on the knowledge sources, connectors, actions, identity configuration, and permissions used by the selected experience. Configure access using the permissions model for each source and integration, and test with representative employee identities to confirm that the agent can access only the intended information and actions.

For the custom engine agent, the published Employee Self-Service guidance describes SharePoint permissions applying to SharePoint knowledge sources and external-system access depending on tenant configuration and the permissions granted to users. For the declarative agent, review the configuration and permissions for its knowledge sources, connections, and connected agents. Don't infer declarative agent access behavior from custom engine agent documentation.

See [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy), [Prepare to deploy the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prepare), and [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent).

## How can organizations use Employee Self-Service responsibly?

Organizations should select supported scenarios, keep authoritative content current, review source and connector permissions, and test representative questions and tasks before making the agent available to employees. Include ambiguous, sensitive, and out-of-scope requests in validation. Establish support and escalation paths for issues that need human judgment.

Publishing or installing an agent doesn't verify that its sources, instructions, permissions, integrations, or support process are appropriate for an organization's use.

## How do employees provide feedback?

Employees can use the feedback controls available with their Microsoft Copilot results. Organizations should define who reviews feedback and how validated issues are routed to the owners of the agent, its knowledge, or its integrations. For custom engine agent feedback guidance, see [Review user feedback](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/feedback).

## Related information

- [Microsoft AI principles](https://www.microsoft.com/ai/responsible-ai)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Responsible AI FAQs for Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/responsible-ai-overview)
- [Introduction to the Employee Self-Service Custom Engine Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/overview)
- [Introduction to Employee Self-Service Declarative Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)
