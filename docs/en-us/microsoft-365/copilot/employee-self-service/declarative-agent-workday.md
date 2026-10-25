<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Integrate Workday with the Employee Self-Service declarative agent

The Employee Self-Service HR declarative agent connects to Workday on behalf of the signed-in employee, with single sign-on \(SSO\) through Microsoft Entra ID. Employees can view their Workday information and update selected details directly from Microsoft 365 Copilot.

You set up the integration by running the `/connect workday` skill in the [Employee Self-Service Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview). The skill guides you and the required administrators through each phase, validates the values that administrators return, and configures the agent for you.

Important

Workday integration is supported only for the Employee Self-Service **HR** declarative agent. If you use the Employee Self-Service custom engine agent, see [Set up the simplified Workday integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-simplified-setup).

## Setup at a glance

1. Run `/connect workday` for your development \(Dev\) environment.
2. Complete all six phases, including the maker validation in the Copilot Studio test pane.
3. Promote the agent to Test.
4. Run `/connect workday` again for Test, and complete the Test connections, runtime configuration, and maker validation.
5. Promote the agent to Production.
6. Run `/connect workday` again for Production, and complete the same steps.
7. Publish the Production agent.
8. Have an employee who isn't the maker connect to Workday in Microsoft 365 Copilot and try a supported scenario in each environment.

You configure Microsoft Entra ID and Workday only once. In Test and Production, the skill reuses that configuration and sets up only what's specific to each environment. For steps 3 to 7, see [ALM for the Workday package](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#alm-for-the-workday-package).

## How the Workday integration works

The integration has two parts:

- **Workday topics** in the ESS HR agent, which handle employee requests.
- **The Workday runtime package**, a managed Power Platform solution that contains the cloud flows the topics use to call Workday.

The runtime package calls Workday through a **Workday** connection that uses **Microsoft Entra ID Integrated** authentication. Calls to both the Workday REST and SOAP APIs run as the signed-in employee, so employees see only the data that Workday security allows them to see. You don't need an integration system user \(ISU\).

### Supported scenarios

| Topic | What employees can do |
| --- | --- |
| Workday Get BaseCompensation | View their base compensation. |
| Workday Get Certifications | View their certifications. |
| Workday Get CompanyCode | View their company code. |
| Workday Get CostCenter | View their cost center. |
| Workday Get EmergencyContact | View their emergency contacts. |
| Workday Get EmployeeId | View their employee ID. |
| Workday Get EmploymentInformation | View their employment details. |
| Workday Get LanguageInformation | View their language skills. |
| Workday Get NationalIDs | View their national IDs. |
| Workday Get Passports | View their passports. |
| Workday Get ServiceAnniversary | View their service anniversary. |
| Workday Get Visas | View their visas. |
| Workday Update Email | Update their email address. |
| Workday Update PhoneNumber | Update their phone number. |

The agent also includes Workday system topics that these topics depend on. Don't edit, turn off, or delete them. For the list, see [System topics](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference#system-topics).

## Before you begin

### Prerequisites

- The **ESS HR declarative agent** is installed in a Power Platform development environment, and you can edit it in Copilot Studio. For more information, see [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent).
- Your Workday tenant uses SSO with Microsoft Entra ID as the identity provider \(IdP\). Third-party IdPs, including third-party IdPs federated with Microsoft Entra ID, aren't currently supported. Basic authentication isn't supported. If your organization already uses Microsoft Entra SSO for Workday, the setup reuses it.
- **Visual Studio Code** and an active **GitHub Copilot** subscription, to run the Agent Developer Kit.
- Your network allows Power Platform to reach the Workday REST and SOAP endpoints. For more information, see [Network requirements](#network-requirements).

### Roles you need

Line up these administrators before you start. The skill pauses at each administrator handoff, and you can resume later without repeating completed phases.

| Role | Phase | Responsibilities |
| --- | --- | --- |
| Power Platform Environment Maker | 1, 4, 5, 6 | Runs the skill, approves the Workday package installation, creates connections, and validates the agent. |
| Application Administrator or Cloud Application Administrator | 2 | Configures the Workday enterprise application and app registration in Microsoft Entra ID. |
| Workday administrator | 3 | Configures SAML, the signing certificate, tenant security, the API client, domain security, and authentication policies. |
| Dataverse System Administrator | 5 | Authorizes the agent to run the Workday flows. |
| Network or security team | 3 | Allows Power Platform traffic to the Workday REST and SOAP endpoints. |

## Install the Agent Developer Kit

1. Install the Agent Developer Kit. For an overview of the kit and the installation options, see [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview). You can also follow the instructions in the [GitHub repository](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit).
2. Open the ESS maker skills workspace in Visual Studio Code.
3. In GitHub Copilot Chat, run `/setup`, and connect the workspace to your ESS HR agent in the Dev environment.

Note

Your GitHub account for GitHub Copilot is separate from your Microsoft work account. When the skill asks you to sign in to Power Platform or Copilot Studio, use the work account that can edit the ESS HR agent.

## Run /connect workday in Dev

In GitHub Copilot Chat, run `/connect workday`. The skill starts with a readiness summary, and then guides you through six phases.

| Phase | Who | What happens |
| --- | --- | --- |
| 1. Preflight | Maker | The skill checks the agent, environment, account, and Workday package. It doesn't change anything. |
| 2. Microsoft Entra | Entra administrator | The skill generates a handoff. The administrator completes it and returns the worksheet. |
| 3. Workday | Workday administrator | The skill generates a handoff. The administrator completes it and returns the worksheet. |
| 4. Connections | Maker | The skill installs the Workday runtime package. You create the Dataverse and Workday connections. |
| 5. Runtime configuration | Maker and Dataverse administrator | The skill configures the runtime. You connect the agent's Workday connection references. |
| 6. Maker validation | Maker | You test the agent in the Copilot Studio test pane. |

Important

The skill never asks for passwords, client secrets, tokens, certificate contents, or private keys. Don't paste them into the chat.

You're asked to sign in several times during setup, because the Power Platform CLI, Dataverse, the Workday connector, and Copilot Studio each authenticate separately.

### Phase 1: Preflight

The skill confirms that you're signed in with the right account, that it can reach the ESS HR agent and the Dev environment, and which Workday package to use.

### Phase 2 and Phase 3: Administrator handoffs

For each administrator phase, the skill generates a handoff with the values for your tenant. Forward it to the administrator through your organization's approved channel. The administrator completes the tasks, fills in the **Your tenant values** column of the worksheet, and returns it. Paste the completed worksheet back into the chat in one response. If any values are missing or invalid, the skill asks only for those values.

- **Phase 2: Microsoft Entra ID.** The administrator configures SAML SSO for the Workday enterprise application, transfers the signing certificate to the Workday administrator, and authorizes the Power Platform Workday connector on the app registration.
- **Phase 3: Workday.** The Workday administrator adds the Microsoft Entra signing certificate, configures tenant security and an API client, grants domain security to the rollout population, and activates authentication policies.

For the full task lists and worksheets, see the [Microsoft Entra and Workday administrator reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference).

### Phase 4: Create connections

1. When the skill asks, approve the installation of the Workday runtime package.
2. Create the **Microsoft Dataverse** connection, and confirm that its status is **Connected**.
3. Create the **Workday** connection from the link that the skill provides, using the following values.
   | Field | Value |
   | --- | --- |
   | Authentication type | **Microsoft Entra ID Integrated** |
   | Microsoft Entra resource URL \(Application ID URI\) | `http://www.workday.com/<tenant>`. This value is the Workday SAML Service Provider ID, not the `api://` Application ID URI. |
   | Workday OAuth token URL | The token endpoint from the Workday worksheet. |
   | Workday OAuth client ID | The Workday API client ID, not the Microsoft Entra Application ID. |
   | SOAP base URL | `https://<host>/ccx/service/` |
   | REST base URL | `https://<host>/ccx/api` |
   | Tenant name | Your Workday tenant name. |
4. Select **Create**, complete the sign-in, and confirm that the connection status is **Connected**.

### Phase 5: Configure the runtime

After you approve, the skill binds the connection references, turns on the Workday flows, authorizes the agent to run them, turns on the Workday topics, sets the runtime template configurations, and connects user context. A Dataverse System Administrator is needed to authorize the flows.

Then point the agent's Workday connection references to your Workday connection:

1. Open the ESS HR agent in the classic Copilot Studio experience, signed in with the same maker account that you used in the skill.
2. Go to **Settings** > **Connection Settings**. Two Workday connection references show as **Not connected**:

   - **ESS Workday Runtime**
   - **ESS Workday Runtime REST Execution**

3. For each connection reference, select the Workday connection that you created in Phase 4.
4. For each connection reference, select **See details**, open the **Connection parameters** tab, turn on **Allow permission to share parameters**, and then select **Save**.
5. Refresh Copilot Studio, go to **Topics**, and confirm that every Workday topic shows **On**.

### Phase 6: Validate in the test pane

1. In the classic Copilot Studio experience, start a new conversation in the **Test** pane. You don't need to publish the agent.
2. Ask, "What's my employee ID?"
3. Confirm that the agent returns your Workday employee ID without repeatedly asking you to sign in.
4. Report the result to the skill to complete setup for the Dev environment.

## Promote to Test and Production

After Dev validation succeeds, promote the agent to Test. Then return to the Agent Developer Kit and tell the skill that you promoted the agent to Test, or run `/connect workday` again. The skill reuses the Microsoft Entra and Workday configuration, and guides you through connections, runtime configuration, and maker validation for Test. Repeat the same steps after you promote to Production.

For details, see [ALM for the Workday package](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent#alm-for-the-workday-package).

## Publish and roll out to employees

1. Publish the Production agent and submit it for approval. For more information, see [Publish and submit for organization approval](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent#publish-and-submit-for-organization-approval).
2. Ask an employee who isn't the maker to open the agent in Microsoft 365 Copilot and ask, "What's my employee ID?"
3. The first time an employee uses a Workday scenario, the agent asks them to connect to Workday. The employee signs in, and the agent creates a Workday connection for that employee. After that, the agent returns the employee's own data.

## Network requirements

Work with your security team to allow traffic from the Power Platform environment that hosts the agent to both the Workday REST and SOAP endpoints. Most existing SOAP firewall rules also cover the REST endpoint, but some organizations might need a separate review.

- [Power Platform URLs and IP address ranges](https://learn.microsoft.com/en-us/power-platform/admin/online-requirements)
- [Managed connectors outbound IP addresses](https://learn.microsoft.com/en-us/connectors/common/outbound-ip-addresses#power-platform)

## Troubleshooting

| Symptom | Likely cause | Resolution |
| --- | --- | --- |
| An employee gets a "Task not authorized" error. | The employee's security group doesn't have the required Workday domain permissions. | Grant **Get** access on **Worker Data: Public Worker Reports** and **Integration Permissions** to the employee's security group. See [Workday task 5](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference#workday-task-5-configure-domain-security-for-your-rollout). |
| Sign-in fails or loops. | The Workday SAML settings don't match Microsoft Entra ID. | Confirm that the **Service Provider ID**, **Issuer**, and identity provider SSO service URL in Workday match the Microsoft Entra values. See [Workday tasks](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference#workday-tasks). |
| The Workday connection can't authenticate. | The Microsoft Entra resource URL is set to an `api://` value, or the client ID is the Microsoft Entra Application ID. | Set the resource URL to `http://www.workday.com/<tenant>`, and use the Workday API client ID. |
| SOAP requests fail. | The SOAP base URL includes the tenant name. | Set the SOAP base URL to end in `/ccx/service/`. To find the value, see [Workday task 6](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference#workday-task-6-collect-the-api-client-values). |
| The agent works in the test pane, but employees are repeatedly asked to sign in. | Parameter sharing is turned off. | Turn on **Allow permission to share parameters** for both **ESS Workday Runtime** and **ESS Workday Runtime REST Execution**. |
| The agent doesn't answer Workday questions. | The Workday topics or flows are turned off. | Run `/connect workday` again. The skill resumes and repairs the runtime configuration. |
| The agent works in Dev but not in Test or Production. | Workday isn't set up in the target environment. | Run `/connect workday` for that environment. See [Promote to Test and Production](#promote-to-test-and-production). |
| A list returns no results, or an update returns `Invalid_Reference_ID`. | The reference data doesn't match your Workday tenant. | See [Customize Workday reference data](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference#customize-workday-reference-data). |

## Limitations

- Workday integration is supported only for the ESS HR declarative agent.
- Only employee records are supported. External staff and other non-employee workers aren't supported.
- Workday must use SSO with Microsoft Entra ID as the identity provider. Third-party identity providers, including those federated with Microsoft Entra ID, aren't currently supported.
- Each Dev, Test, and Production environment needs its own Workday connections.

## Related content

- [Microsoft Entra and Workday administrator reference for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference)
- [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent)
- [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent)
- [Employee Self-Service Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview)
- [Microsoft Entra SSO integration with Workday](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workday-tutorial)
