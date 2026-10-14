<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Troubleshoot the Employee Self-Service agent

Use this article to find the next diagnostic for a problem with Employee Self-Service. Employee Self-Service is available as a custom engine agent and as declarative agent templates. The experiences have different setup, configuration, and integration paths, so use the guidance for the experience you're troubleshooting.

## Choose where to start

| Symptom | Start here |
| --- | --- |
| You can't find or install the agent template | For the custom engine agent, confirm the selected environment and follow [Install the Employee Self-Service Custom Engine Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install). For the declarative agent, confirm the environment, then follow [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent#before-you-install). |
| The Agent Developer Kit \(ADK\) doesn't open, commands are missing, or setup can't connect | Follow [Troubleshoot getting started with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started). Use the [ADK commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference) to confirm which commands support your agent family. |
| The agent doesn't find expected information or the answer is incomplete | Confirm that the expected knowledge source is configured, available, current, and accessible to the test identity. For the custom engine agent, see [Optimize SharePoint knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/optimization-sharepoint). For the declarative agent, see [Configure ServiceNow Knowledge for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-knowledge) when the issue involves that source, or follow the knowledge-source setup in [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent). |
| The answer appears incorrect, out of date, or unrelated | Check the answer against the authoritative source, then review the configured knowledge, instructions, and scenario. Test with representative questions and employee identities. For custom engine agent evaluation guidance, see [Response quality evaluations for the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations). For the declarative agent, see the testing steps in [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent) and [Agent evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations). |
| A connected system or action fails | Check that the integration is configured for the correct Employee Self-Service experience, its connection is available, and the test identity has the required permissions. Then use the integration-specific setup article and the relevant platform known-issues guidance. Don't apply custom engine agent connector steps to a declarative agent connection or the reverse. |
| The agent works in the maker experience but isn't available to employees | Confirm that the agent was published, submitted for any required organization approval, and made available to the intended audience. For the custom engine agent, see [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish). For the declarative agent, see [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent) and [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent). |
| You see a known product issue or platform error | For the custom engine agent, check [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations). For Copilot Studio or Power Platform issues, check the platform's known-issues and support guidance. |

## Check ADK command support

ADK commands don't all support the same agent families. Before running a command, check the [ADK commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference) for current availability and limitations. In particular, don't assume that an ADK command available for the custom engine agent is available for the declarative agent.

For setup or workspace issues with the toolkit, use [Troubleshoot getting started with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started). The ADK troubleshooting article is for the developer toolkit, not a replacement for troubleshooting an Employee Self-Service agent's runtime, knowledge, connections, or employee access.

## Collect details before asking for help

Record the details that help the relevant administrator or support team reproduce the issue:

- Employee Self-Service experience and template \(custom engine agent, Employee Self-Service HR, Employee Self-Service IT, or Employee Self-Service Hub\), environment, and when the issue began.
- The employee or maker scenario, expected result, actual result, and exact error text.
- The identity and permissions used for the test, without including passwords, tokens, or other secrets.
- Recent changes to knowledge sources, instructions, topics, connections, permissions, or deployment.
- The relevant test result or supported diagnostic output, if available.

Review conversation snapshots and diagnostic evidence for personal or sensitive information before sharing them. Handle them according to your organization's data-protection requirements.

For toolkit defects, follow the support guidance in the [Agent Developer Kit repository](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/issues). For Employee Self-Service product, Copilot Studio, environment, or integration issues that the linked documentation doesn't resolve, work with your Microsoft 365 or Power Platform administrator to open a support request through your organization's support channel.

## Related content

- [Install the Employee Self-Service Custom Engine Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install)
- [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent)
- [ADK commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference)
- [Troubleshoot getting started with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started)
- [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations)
- [Responsible AI FAQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/rai-faq)
