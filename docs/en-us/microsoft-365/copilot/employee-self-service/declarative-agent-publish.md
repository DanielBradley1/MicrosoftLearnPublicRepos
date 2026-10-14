<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-publish -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Publish the Employee Self-Service declarative agent to your organization

Publish the Employee Self-Service declarative agent, obtain administrator approval, and assign the intended audience before you roll it out to employees in Microsoft 365 Copilot Chat. Publishing in Copilot Studio and making the agent available through your organization's catalog are separate steps.

This article applies to the Employee Self-Service HR, Employee Self-Service IT, and Employee Self-Service Hub declarative agent templates. Complete configuration and validation before submitting the production agent for organization approval. For custom engine agents, see [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish).

| Role | Activities to perform | Configuration area |
| --- | --- | --- |
| Copilot Studio maker or agent owner | Publish changes in Dev, validate in Test, promote the approved version to Prod, and submit the production agent for admin approval. | Microsoft Copilot Studio. |
| Microsoft 365 administrator | Review the agent, approve the request, and assign the pilot audience. | Microsoft 365 admin center. |
| Business stakeholders and pilot champions | Approve the supported scenarios, identify pilot employees, and validate the employee experience. | Your organization's release and adoption process. |

## Promote the declarative agent to Prod

Use [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent) to prepare the version you intend to release. Dev, Test, and Prod are quality gates in the same Power Platform environment, not separate Power Platform environments.

Important

Author all agent configuration in Dev, and carry the validated configuration unchanged through Test to Prod. ALM doesn't provide built-in approval flows, and rollback isn't currently supported.

1. Open the Employee Self-Service agent in the classic Copilot Studio experience. If you're in the new experience, use the account menu to select **Open classic experience**.
2. Confirm that the template is enrolled in ALM. Review the [enrollment requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#before-you-enroll-an-employee-self-service-template-in-alm) before enrolling a new template. Enrollment can't be undone.
3. In Dev, finish the [declarative agent customizations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize), including the agent's name, icon, descriptions, instructions, knowledge, and connections. Confirm that required privacy and terms of use details are accurate.
4. Publish the changes in Dev. Unpublished changes aren't included in the next deployment.
5. [Deploy from Dev to Test](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#deploy-from-dev-to-test), and validate the supported scenarios, citations, user permissions, connections, and actions. Use your [Employee Self-Service evaluation cases](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations) and organizational release criteria.
6. Complete the release review, then [deploy the validated Test version to Prod](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#deploy-from-test-to-prod).
7. Open the agent in Prod and confirm the expected version and configuration. If you find a defect, correct it in Dev, publish, validate in Test, and promote again.

For Employee Self-Service Hub, publish and promote the HR and IT agents it connects to before the Hub at each quality gate. Follow the [hub agent setup guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub-declarative-agents), and validate routing and connected-agent access before rollout.

External-system dependencies need separate verification. Workday connections aren't automatically established in Test and Prod; provision or reconnect them at each gate and verify the Dataverse-backed package, flow permissions, and connection parameter sharing. For ServiceNow, verify the connection at each gate, especially if you configured it after an initial deployment. See [ALM for the Workday package](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#alm-for-the-workday-package), [Integrating Workday](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday), and [Configure ServiceNow HR and IT for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-servicenow-hr-it). Connection provisioning doesn't authorize configuration changes in Test or Prod.

Note

If you update or replace a ServiceNow connection, make the agent configuration changes in Dev, publish, and deploy to Test again. Verify employee sign-in and the enabled ServiceNow actions before promoting the validated release to Prod, then verify the connection in Prod. If you first deployed without ServiceNow configured and added it later in Dev, a subsequent deployment might leave the Test connection's `connectionId` empty. Complete any required connection provisioning before validation; don't change the promoted agent configuration in Test or Prod. See [Deploy from Dev to Test](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#deploy-from-dev-to-test).

## Verify declarative agent authentication

Before you submit the production agent, verify authentication and data access with representative employee accounts, not only maker or administrator accounts.

1. Confirm that employees can sign in to Microsoft 365 Copilot with their organizational account and have the required [licenses and access](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites).
2. Verify access to each enabled knowledge source. Check that answers and citation links respect the employee's source permissions. See [Configure knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-knowledge-sources).
3. For enabled external-system actions, verify the supported user-delegated authentication, identity mapping, and source-system permissions. Confirm that an employee can access only their permitted data and actions.
4. If an enabled connector prompts for first-use consent, verify the employee onboarding experience and explain the required consent to pilot users. Resolve authentication or consent failures with the identity and external-system administrators before rollout.

## Publish the Employee Self-Service declarative agent

Publishing the changes in Dev and promoting them to Prod prepares the production release. Submitting that production agent for admin approval requests catalog availability; it doesn't by itself grant access to everyone in your tenant.

1. Open the promoted agent in Prod in the classic Copilot Studio experience.
2. Review the promoted agent details and confirm that the version matches the release approved in Test. Make any required corrections in Dev and repeat promotion rather than editing Prod.
3. Open the agent's publishing and sharing options, and select **Show to everyone in my org**.
4. Review the submission requirements, then select **Submit for admin approval**.
5. Confirm the submission and check its status in Copilot Studio.
6. Coordinate with your Microsoft 365 administrator to approve the request and restrict the initial rollout to the pilot audience. Don't reduce the agent's access setting while the submission is pending.

Repeat the submission for each Employee Self-Service agent you intend to distribute. For an Employee Self-Service Hub deployment, coordinate approval and access for its connected domain agents before releasing the Hub.

## Approve the declarative agent as an admin

Use the Microsoft 365 admin center to review the submitted agent and control who can install or receive it.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a role that can manage agents.
2. Select **Agents** > **All agents** > **Requests**.
3. Select the submitted Employee Self-Service agent. Review its owner, descriptions, capabilities, knowledge sources, data access, requested permissions, and actions.
4. Select **Publish to store** to open the publishing wizard.
5. Select the users or groups that can install the agent. Start with a small pilot audience. If appropriate, also select the users or groups who receive the agent preinstalled.
6. Apply the required policy template, review permissions, and grant admin consent only when appropriate.
7. Review the selection and select **Publish**.

Your tenant might still expose agent management under **Settings** > **Integrated apps**. Use the approval and audience controls available in your tenant. See [Agent requests](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-requests) and [Manage agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

Approval and audience assignment determine who can discover and use the agent. Knowledge-source and external-system permissions still apply; catalog approval doesn't grant access to restricted data.

## Troubleshoot declarative agent availability

If a pilot employee can't find or use the agent after approval:

1. Check the submission status in Copilot Studio and the request status in the Microsoft 365 admin center. Confirm that the correct production agent was approved.
2. Confirm the employee is in the assigned audience and has the required license and access. Check whether an organizational policy blocks the agent.
3. Verify the agent in Microsoft 365 Copilot Chat after deployment propagation. Don't use standalone Teams as the declarative agent validation surface.
4. If the agent opens but a scenario fails, check source permissions, connector sign-in and consent, and any connected-agent access. Verify the source-system outcome for enabled transactions.
5. If the agent loads but its icon doesn't render, verify the functional experience separately. An icon issue isn't evidence that publishing failed.

If the issue persists, work with your Microsoft 365 and Copilot Studio administrators or contact support.

## Declarative agent publishing checklist

| Role | Verification steps |
| --- | --- |
| Maker or agent owner | Confirm the approved Test version is promoted to Prod, required connections work, and the correct production agent is submitted. |
| Microsoft 365 administrator | Confirm catalog approval, audience assignment, policy settings, and appropriate permission consent. |
| Pilot employee | Find and open the agent in Microsoft 365 Copilot Chat. Verify expected branding, knowledge answers, working citations, permitted actions, and first-use authentication. |
| Employee Self-Service Hub owner, if applicable | Confirm the Hub reaches the intended HR and IT agents and that pilot employees can use each connected scenario. |
| Release owner | Confirm employees outside the assigned audience can't access the pilot agent and that support and monitoring owners are ready. |

Resolve failed checks before expanding access. For configuration defects, return to Dev and repeat validation and promotion. Repeat catalog submission or approval when required for changes to the agent's catalog details.

## Manage declarative agent availability

Use the Microsoft 365 admin center's agent management controls to manage the approved audience, preinstallation, and access policies. Expand the audience only after the pilot meets your release criteria. See [Agent registry](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry).

If you need to stop employee access, use the available administrative controls to block the agent or restrict its audience. Coordinate changes for the Hub and connected agents so employees don't encounter unavailable dependencies.

For subsequent releases, make and publish changes in Dev, validate in Test, and promote the approved version unchanged to Prod. After rollout, review employee feedback and operational issues with your service owners.

## Related content

- [Introduction to Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview).
- [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent).
- [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent).
- [Configure knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-knowledge-sources).
- [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize).
- [Set up the Employee Self-Service hub for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub-declarative-agents).
- [Agent Developer Kit for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview).
- [Agent evaluations for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations).
