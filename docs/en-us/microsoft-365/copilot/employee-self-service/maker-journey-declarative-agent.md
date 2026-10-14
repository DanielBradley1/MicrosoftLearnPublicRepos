<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Deploy Employee Self-Service declarative agents

Use this guide to take an Employee Self-Service declarative agent from installation in Microsoft Copilot Studio to submission for organization catalog approval. The guide covers the Employee Self-Service Hub, Employee Self-Service HR, and Employee Self-Service IT templates and links to the Copilot Studio documentation for platform procedures.

The Employee Self-Service templates are starting points. Before you make an agent available to employees, configure it for your organization's knowledge, identity, external systems, security requirements, and support processes.

## Choose an Employee Self-Service template

Choose the template that fits the employee experience you want to provide. Each template is installed and managed as an agent.

| Template | Use it to | Typical packaged capabilities |
| --- | --- | --- |
| **Employee Self-Service HR** | Provide HR policy and process answers and support employee HR tasks. | SharePoint and ServiceNow Knowledge Base sources; packaged Workday employee lookups and updates to personal email and phone; ServiceNow HR service scenarios. |
| **Employee Self-Service IT** | Help employees troubleshoot IT issues and manage support requests. | SharePoint and Microsoft Self-Help knowledge sources; ServiceNow IT ticket retrieval, creation, and updates. |
| **Employee Self-Service Hub** | Offer one entry point that routes employee requests to HR and IT agents, and other declarative agents. | Connected-agent routing to the Employee Self-Service HR and Employee Self-Service IT agents, and other declarative agents. Install and configure the HR and IT agents in the same environment before you set up the Hub. |

Capabilities and integrations can vary by template version and availability in your environment. Review the template details and the Employee Self-Service integration guides before you plan a production rollout. For the current Employee Self-Service overview, see [Introduction to Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview).

## Before you install

Coordinate with your Power Platform administrator, Copilot Studio administrator, HR and IT service owners, and security or privacy reviewers before you begin.

- Confirm that you have access to Copilot Studio and the Power Platform environment where you plan to install the agents.
- Confirm licensing, capacity, and user access requirements for makers and employees. See [Copilot Studio licensing and subscriptions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing-subscriptions).
- Confirm that the required connectors are allowed by your organization's data loss prevention \(DLP\) and governance policies. See [Copilot Studio security and governance](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance).
- Identify the knowledge sources and external systems you intend to use, and arrange for their owners to provide access, connection, and authentication details.
- Define a pilot audience and representative HR and IT scenarios. Include an employee account with the correct permissions for testing user-specific information and actions.
- If you plan to use Employee Self-Service Hub, install both domain agents in the same environment and plan to validate each agent and the handoff between them.

For environment setup and role guidance, see [Work with environments in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/environments-first-run-experience).

## Install an Employee Self-Service agent template

Install each Employee Self-Service agent template in the Power Platform environment where you intend to configure and test it. The Hub depends on the HR and IT agents, so install the domain agents before the Hub.

1. Sign in to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com) and select the intended environment.

   Note

   Employee Self-Service DA agents appear in the classic Copilot Studio experience, not the new experience's agent list. If you sign in to an environment without a Dataverse database, the new experience might show a Dataverse setup warning. Select **Open classic experience** from the three-dot menu next to your signed-in account at the bottom left to manage the Employee Self-Service templates.
2. Go to **Agents** and open the agent template catalog from the **Start with an agent template** section.
3. Select the Employee Self-Service agent template you want to install: **Employee Self-Service HR**, **Employee Self-Service IT**, or **Employee Self-Service Hub**.
4. When installation completes, select **Open** and confirm the agent appears on the **Agents** page.
5. Repeat the steps for the other Employee Self-Service agent templates you need.

The available agent templates can vary by environment and rollout. If an Employee Self-Service template isn't listed, contact your Copilot Studio or Power Platform administrator or your Employee Self-Service onboarding contact.

## Promote the agent through ALM

Before you configure, enable ALM to promote and validate the production version of each agent you plan to release. Employee Self-Service Hub, Employee Self-Service HR, and Employee Self-Service IT each have their own ALM lifecycle; Hub also depends on the versions of HR and IT that it connects to.

Author configuration in Dev and deploy it through Test to Prod to baseline response quality. On redeployment, select **Copy from Dev** for Test and **Copy from Test** for Prod to refresh the target configuration from its source quality gate. Don't introduce independent configuration overrides in Test or Prod.

For enrollment, deployment steps, and connector-specific considerations, see [Agent lifecycle management](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent).

Note

A ServiceNow connection added after the first deployment, or a change to an existing connection, might not propagate to the next quality gate. After deployment, copy only the intended source `connectionId` into the corresponding Test or Prod entry when needed, then validate authentication and required actions. See [ServiceNow connection ID workaround](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#servicenow-connection-id-workaround). Workday connections require separate target-gate provisioning; see [ALM for the Workday package](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#alm-for-the-workday-package).

## Configure the agents for your organization

Configure the agent in Copilot Studio and complete required setup in the connected systems. For ALM, author the production-intended knowledge sources, endpoints, and connection configuration in Dev. Promote that configuration through Test to Prod to baseline response quality. Don't customize content, topics, endpoints, or other settings in Test or Prod; the documented ServiceNow connection-ID synchronization is the only configuration exception.

In Dev, open **Topics** and enable the scenario topics required for the capabilities you plan to offer.

Note

Keep all system topics enabled, including the system topics used by the required Power Platform connectors. In **Topics**, use the **All** or **System** filter and set their **Enabled** toggles to **On**.

Work with your administrators and data owners to ensure that access to production knowledge sources and systems from Dev is approved and secured. Use test identities and data that are appropriate for your validation scenarios. Use production employee data only when your organization explicitly authorizes it and the required access controls are in place.

Note

Changing a SharePoint or ServiceNow Knowledge source in Dev after deployment requires publishing Dev, deploying to Test once, and then deploying again to Test with **Copy from Dev** > **Save** > **Deploy**. After validating Test and completing release reviews, deploy Test to Prod once, then deploy again to Prod with **Copy from Test** > **Save** > **Deploy**. Validate the intended knowledge sources at each gate. See [Knowledge-source updates after deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#knowledge-source-updates-after-deployment).

### Configure Employee Self-Service HR

1. Add or verify the HR knowledge sources your employees are allowed to use, such as approved SharePoint content or ServiceNow Knowledge Base content. Review [Add knowledge to an agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio) and [Configure ServiceNow Knowledge for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-knowledge).
2. Configure the Workday and ServiceNow connections and packaged scenarios that your organization plans to enable. Work with the Workday and ServiceNow administrators to configure authentication and permissions. See [Configure ServiceNow HR and IT for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it).
3. Review the agent's topics, instructions, starter prompts, and escalation behavior. Make sure HR content is current and that sensitive or employee-specific requests follow your organization's approved process. See [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize) and [Craft declarative agent instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-instructions).
4. Validate that the test identity can access only the employee data and actions permitted for that identity.

The Workday package used by Employee Self-Service HR remains Dataverse-backed and has ALM considerations that differ from the declarative agent templates. Complete the Workday-specific setup with your Power Platform administrator.

Note

Enable connection parameter sharing explicitly on the Workday connection references. Direct connections, such as ServiceNow, have connection parameter sharing enabled by default and don't require this additional setup. See [ALM for the Workday package](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#alm-for-the-workday-package) for target-gate connection provisioning considerations.

### Configure Employee Self-Service IT

1. Add or verify approved SharePoint and Microsoft Self-Help knowledge sources. Confirm content owners maintain the information employees will receive.
2. Configure ServiceNow connections and the IT ticket scenarios you intend to offer. See [Configure ServiceNow HR and IT for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it).
3. Review the troubleshooting instructions, topics, and handoff or escalation paths. Confirm the agent doesn't promise an action that isn't configured or authorized.
4. Test ticket operations with accounts and records approved for validation; confirm authentication, permissions, and resulting ticket state.

### Configure Employee Self-Service Hub

1. Confirm Employee Self-Service HR and Employee Self-Service IT are installed in the same environment and each is configured for the intended employee scenarios.
2. Configure the Hub's connections to the domain agents by following the available template setup prompts and the Copilot Studio guidance for [connecting to other agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-add-other-agents).
3. Review the Hub's instructions and routing so HR questions reach Employee Self-Service HR and IT questions reach Employee Self-Service IT. Set a clear fallback for requests that don't fit either domain.
4. Test the HR and IT agents directly before testing the corresponding Hub handoffs.

## Customize and test in Copilot Studio

Make only the changes your organization needs. Keep a record of the enabled scenarios, data sources, connections, and owners so testers and approvers can review the agent's behavior.

1. Customize the agent's name, description, icon, instructions, and starter prompts for your audience. See [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize).
2. Review topics and actions in Dev. Enable the required scenario topics and keep all system topics enabled, including those for the required Power Platform connectors. Disable only scenario topics you haven't configured or approved, and define how employees can get help when the agent can't safely complete a request.
3. Use the **Test** pane to run representative single-turn and multi-turn conversations. See [Test your agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-test-bot).
4. Validate knowledge answers and citations, access boundaries, connector authentication, read and write actions, error handling, and escalation behavior. For Employee Self-Service Hub, test the complete route to both domain agents.
5. Use an evaluation set or documented test cases to compare results after changes. Include common employee questions, ambiguous prompts, sensitive topics, out-of-scope requests, and failures of external connections. See [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations).
6. Resolve issues and repeat testing until the agent meets your organization's release criteria. Ask HR, IT, security, privacy, and support owners to review their areas.

Copilot Studio's test experience doesn't replace validation with the intended users, data permissions, and external systems.

## Publish and submit for organization approval

Publishing an agent in Copilot Studio makes its latest content available on Microsoft 365 chat. Submitting it for admin approval is a separate step that requests organization-wide catalog availability. See [Publish the Employee Self-Service declarative agent to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-publish).

Note

After a published agent is added to Microsoft 365 Copilot Chat, its icon might not render even though the agent loads successfully.

### Confirm the configuration

1. After the validated release has been promoted to the Prod quality gate by following the Employee Self-Service ALM process, open the agent at that gate and confirm the expected version is available. Don't make content or customization changes in Test or Prod. If agent details need changes, make them in Dev and promote the updated release.
2. Review the promoted agent name, icon, short and long descriptions, developer details, privacy statement, and terms of use. If any details need changes, update them in Dev, test, and promote the updated release before submitting. Descriptions should state whether the agent handles HR, IT, or both, and which actions it can perform.
3. Confirm the promoted agent's authentication and sharing settings meet your organization's requirements and the intended audience can access it.

For setup and branding details, see [Connect and configure an agent for Teams and Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams).

### Submit the agent for admin approval

Before submitting, confirm the production agent is release-ready, required reviews are complete, and the agent details are accurate.

1. Select **Show to everyone in my org** and review the submission requirements.
2. Select **Submit for admin approval**, review the confirmation, and submit the request.
3. Check the submission status in Copilot Studio. Coordinate with your Microsoft 365 administrator while the request is pending. Don't reduce the agent's access setting after submitting it.

The Microsoft 365 administrator reviews the agent's capabilities, knowledge sources, data access, and actions in the Microsoft 365 admin center. The administrator can publish the agent to the organization's Agent Store for a selected audience, apply policies, review requested permissions, or reject the request. For details, see [Agent Requests in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-requests).

After approval, the agent can appear in the **Built for your org** section of the Teams app store and, when configured for Microsoft 365 Copilot, the **Built by your org** section of the Microsoft 365 Agent Store. Admin approval and rollout determine which users can install or receive the agent; submitting a request alone doesn't make it available tenant-wide. Learn more about [managing agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

Repeat the publishing, review, and approval process for each Employee Self-Service template you want to offer in the organization catalog. For a Hub deployment, publish and submit the HR and IT agents it depends on as well as the Hub, and coordinate the rollout order with your administrator.

## Maintain the agent after approval

After approval, continue to own the agent's content, integrations, and response quality. Monitor feedback and analytics, review knowledge content and access, and retest important scenarios after changes. Make and publish content changes in Dev, then promote them through the Employee Self-Service ALM process. If you change the agent's catalog details, such as its icon or descriptions, make the changes in Dev, promote them, and follow the platform guidance to resubmit those details for approval.

## Related content

- [Introduction to Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)
- [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent)
- [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize)
- [Craft declarative agent instructions](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-instructions)
- [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations)
- [Publish the Employee Self-Service declarative agent to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-publish)
- [Configure ServiceNow HR and IT for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it)
