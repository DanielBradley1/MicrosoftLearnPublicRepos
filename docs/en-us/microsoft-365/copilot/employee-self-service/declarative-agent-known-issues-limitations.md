<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-known-issues-limitations -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Known issues and limitations for Employee Self-Service declarative agents

This article describes known issues, current limitations, and available workarounds for Employee Self-Service declarative agents in Microsoft 365 Copilot.

For information about Employee Self-Service custom engine agents, see [Known issues and limitations for Employee Self-Service Custom Engine Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations).

Note

Access to Employee Self-Service declarative agents is rolling out in waves. Work with your Microsoft account team to determine availability for your organization.

## Before you deploy

The following considerations can affect how you configure and deploy Employee Self-Service declarative agents.

### Moving from private preview to general availability

Important

Employee Self-Service declarative agents created during private preview aren't automatically upgraded or migrated to the general available version.

Once your tenant has been enabled for access, follow these steps to get started with the latest Employee Self-Service declarative agent templates:

1. Open Copilot Studio. If you're using the new Copilot Studio experience, select the **More options \(...\)** menu in the lower-left corner, then select **Open classic experience**.
2. In classic Copilot Studio, select **Agents** from the left navigation.
3. Under **Start with an agent template**, locate the Employee Self-Service templates, such as **Employee Self-Service** and **Employee Self-Service \(HR\)**.
4. Select the generally available agent template you want to deploy, then configure and your knowledge sources and integrations before rolling out to employees.

Important

**Start with Q&A.** We recommend beginning with HR or IT questions using content you already have, such as policies, FAQs, and how-to guides. Q&A accounts for over 70% of Employee Self-Service conversations, making it a great place to deliver value quickly while keeping your initial deployment simple. You can expand into more advanced workflows and tasks over time.

### Identity provider and single sign-on

Employee Self-Service declarative agents don't support direct single sign-on \(SSO\) with third-party identity providers \(IdPs\).

**What to do:** Use a supported Microsoft Entra ID authentication configuration. If your organization requires federation with a third-party identity provider, contact your Microsoft account team to discuss your requirements and available options.

### Supported experiences

Employee Self-Service declarative agents are supported in Microsoft 365 Copilot on desktop and web.

Microsoft Teams and mobile experiences aren't supported in this release.

**What to do:** Use Microsoft 365 Copilot on desktop or web for your initial deployment.

### Workday connection setup

Configuring Workday connections directly through the Copilot Studio user interface isn't supported in this release.

**What to do:** Use the Agent Developer Kit \(ADK\) `/connect workday` skill to integrate Workday with your Employee Self-Service HR agent.

Makers using ADK must have the required GitHub Copilot licenses assigned before setup and configuration.

For step-by-step instructions, see [Integrate Workday with Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday).

For more information about ADK, see [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview).

## Known issues

The following issues can occur when configuring, publishing, or managing Employee Self-Service declarative agents.

| Area | Known issue | Workaround or guidance |
| --- | --- | --- |
| Agent icon | After an agent is published and added to Microsoft 365 Copilot, the agent loads correctly, but its icon might not appear. | Agent functionality isn't affected. |
| Copilot Studio experience | Employee Self-Service declarative agents appear in the agent list in classic Copilot Studio but not in the new experience. The new experience lists custom agents only. Dataverse is also enabled the first time a maker visits the new experience. | Use classic Copilot Studio to find and manage Employee Self-Service declarative agents. |
| ServiceNow connection propagation | If ServiceNow is configured in the Development environment after the agent has already been deployed to Test, redeploying doesn't propagate the connection. The ServiceNow connection reference in Test has no connection ID. | Configure ServiceNow in Development before the first deployment to Test. If the agent was already deployed, configure the ServiceNow connection directly in Test. |
| Dataverse provisioning | When a user with only maker privileges signs in to a new Power Platform environment without Dataverse, a Dataverse setup error appears. | Use an environment with Dataverse provisioned, or have an administrator provision Dataverse before makers sign in. |

## Known limitations

### Application lifecycle management limitations

The following limitations apply when deploying and managing Employee Self-Service declarative agents across environments.

#### Connection parameter sharing

Connection parameter sharing behaves differently depending on the connector.

- **Workday:** Connection parameter sharing must be explicitly enabled on the associated connection references.
- **ServiceNow:** Connection parameter sharing is enabled by default.

**What to do:** Before deploying an agent that uses Workday, enable connection parameter sharing on the Workday connection references. No additional setup is required for ServiceNow.

#### Connection provisioning across environments

Connection provisioning differs when moving agents between Development, Test, and Production environments.

- **ServiceNow:** Connections are established automatically in Test and Production based on the Development configuration once the agent is published.
- **Workday:** Connections aren't established automatically in target environments.

**What to do:** After deploying to Test or Production, manually configure the Workday connection in each target environment and verify its status in connection settings.

For more information, see [Application lifecycle management for Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent).

### Agent Developer Kit limitations

The following limitations apply to the Agent Developer Kit \(ADK\) when creating, configuring, testing, and troubleshooting Employee Self-Service declarative agents.

#### Topic authoring

The `/create` and `/update` commands don't support topic creation or updates. Both commands stop topic requests without changing files.

**Workaround or guidance:** No workaround is available through ADK for these topic operations.

#### Workflow deployment

Workflows created or updated in ADK are saved locally. The `/push` command can't deploy them to the agent.

**Workaround or guidance:** Keep workflow files as drafts. Tests against the deployed agent don't include these local changes.

#### Component deletion

The `/delete` command doesn't delete components from native declarative agents. Local and deployed components remain unchanged.

**Workaround or guidance:** No workaround is available through this command.

#### Evaluation methods and test-set size

ADK evaluations support the Compare Meaning method only, with 1 to 100 single-response test cases per set.

Multi-turn tests and other grading methods aren't supported.

**Workaround or guidance:** Provide an expected response for each prompt. Split larger test sets into smaller sets. Separate single-response tests don't validate a multi-turn conversation.

#### Generated evaluations

Generating a test set doesn't verify that its scenarios are configured in your agent or that its expected responses match your organization's policies.

**Workaround or guidance:** Check each expected response against authoritative knowledge sources and agent configuration. A test-set quality score doesn't measure the agent's accuracy.

#### Evaluation review status

Evaluation review requests and completion status remain in the local ADK workspace. Uploading a test set doesn't share its review status.

**Workaround or guidance:** Track review status in the local workspace. A successful upload doesn't confirm reviewer access or approval.

#### Evaluation updates

Deploying changed evaluation content creates a new test-set copy. Earlier copies remain, including cases removed from the revised set.

**Workaround or guidance:** Run the revised set using the test-set ID returned by ADK. If only review status changes, ADK can reuse the existing copy.

#### Runtime diagnostics

The `/test` command supports browser testing of deployed topics, but not workflow testing or server-side diagnostics.

Integration troubleshooting through `/troubleshoot` isn't available.

**Workaround or guidance:** Use `/test` for deployed-topic behavior and `/flightcheck` for readiness checks. These checks don't test unpublished workflows in the running agent.

#### Agent name and icon

The `/landing-page` command can't change the agent's name or icon.

**Workaround or guidance:** Change the agent details and applicable channel branding in classic Copilot Studio, then republish.

For more information, see [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview) and [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference).

## Related documentation

For more information, see:

- [Introduction to Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)
- [Employee Self-Service declarative agent deployment playbook](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deployment-playbook-declarative-agent)
- [Integrate Workday with Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday)
- [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview)
- [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference)
- [Employee Self-Service declarative agent evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations)
- [Application lifecycle management](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent)
- [ServiceNow knowledge integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-knowledge)
- [ServiceNow HR and IT integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it)
- [Customize Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize)
