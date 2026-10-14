<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install-declarative-agent -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Install an Employee Self-Service declarative agent

Use this article to install the Employee Self-Service HR, Employee Self-Service IT, or Employee Self-Service Hub declarative agent template in a Power Platform environment. Installation creates an agent that you can configure and test. It doesn't publish the agent or make it available to employees.

## Before you install

Before you begin:

- Confirm your organization has access to Employee Self-Service agent templates. Availability is rolling out in waves. If you don't see an Employee Self-Service template, contact your Copilot Studio or Power Platform administrator, your Employee Self-Service onboarding contact, or your Microsoft account team.
- Confirm you can access Copilot Studio and have the required permissions for the intended Power Platform environment.

- Select the environment where you will install and configure the agent. For environment strategy and access guidance, see [Prepare to deploy the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prepare).
- Choose the template that matches the employee experience you plan to configure:

  - **Employee Self-Service HR** for HR knowledge and supported HR scenarios.
  - **Employee Self-Service IT** for IT knowledge and supported IT scenarios.
  - **Employee Self-Service Hub** to route between Employee Self-Service HR, Employee Self-Service IT, and other declarative agents.

Install the domain agents in the same environment before installing Employee Self-Service Hub. If you plan to use Agent Lifecycle Management \(ALM\), review [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent) before you configure or publish.

## Install a template

1. Sign in to [Microsoft Copilot Studio](https://copilotstudio.microsoft.com) and select the Power Platform environment where you want to install the template.

   Note

   Employee Self-Service agent templates appear in the classic Copilot Studio experience. If the new experience shows a Dataverse setup warning or doesn't list the templates, select **Open classic experience** from the three-dot menu next to your signed-in account.
2. In **Agents**, open the template catalog in **Start with an agent template**.
3. Select **Employee Self-Service HR**, **Employee Self-Service IT**, or **Employee Self-Service Hub**, and then select **Install**.
4. When installation completes, select **Open** and confirm the agent appears in the selected environment.
5. If you're installing Employee Self-Service Hub, install Employee Self-Service HR and Employee Self-Service IT in the same environment first, then install the Hub.

## Verify installation and continue setup

Confirm the agent appears in the selected environment and opens in Copilot Studio. Then continue with [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent) to configure knowledge, integrations, instructions, and scenarios; test the agent; and publish and submit it for organization approval.

The [Agent Developer Kit \(ADK\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview) is an optional maker toolkit for guided configuration and validation. It isn't required to install the ESS agent template.

## Troubleshoot installation

- **The Employee Self-Service template isn't listed.** Template availability can vary by organization and rollout. Confirm access with your Copilot Studio or Power Platform administrator or Employee Self-Service onboarding contact.
- **You can't select or open the intended environment.** Confirm your account has access to that environment and the required maker or administrator role.
- **You see a Dataverse setup warning in the new Copilot Studio experience.** Open the classic experience to manage Employee Self-Service declarative agent templates.
- **The template installs but doesn't appear for employees.** Installation doesn't publish or deploy the agent. Continue through configuration, testing, publishing, and organization approval in the [deployment guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent).

## Related content

- [Introduction to Employee Self-Service Declarative Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-overview)
- [Deploy Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/maker-journey-declarative-agent)
- [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent)
