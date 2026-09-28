<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Manage Copilot Cowork for your organization

Learn how to manage plugins, models, browser use, security and compliance, and usage-based billing in Copilot Cowork.

Note

Cowork is now an *agentic system* \(different from an *agent*\). You can access it in the Microsoft 365 admin center by selecting **Agents** > **All Agents**, and then selecting **Cowork** from the dropdown menu to the right.

## Allow access to Cowork

To allow users to access Cowork, admins must enable usage-based billing. Learn how to set up and enable usage-based billing in [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

Important

- A spending policy is an access control, not only a budget. Any user in the scope of a spending policy that selects Cowork can use Cowork, regardless of how small the credit limit is. A policy with a limit of one credit still grants access. A very low limit doesn't prevent access; users can still open Cowork and start work until the limit is reached. To keep a user out of Cowork, don't include them in any spending policy that selects Cowork, rather than lowering their limit. Learn how access is determined across policies, discovery, and model settings in [How access to Copilot Cowork is determined](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-access).
- The agent-based access control from the Frontier and Preview versions is deprecated for access control. Copilot Cowork is generally available and is no longer managed by selecting **All Agents** > **Cowork** in the Microsoft 365 admin center. The **Cowork** agent entry is still visible under **Agents** > **All Agents**, but any configuration on it has no effect on who can use Cowork. Access is granted only through a spending policy that selects Cowork.

Learn about Copilot admin settings in [Microsoft Copilot app features that admins can control](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-admin-settings).

### Migrating from Frontier or Preview access control

If you managed Cowork access during the Frontier or Preview program, the control you used has changed.

- **What the agent control used to do**: In the Preview version, you allowed or blocked users by configuring the **Cowork** agent entry under **All Agents** in the Microsoft 365 admin center.
- **What replaced it**: At general availability, access is granted by the presence of a spending policy that includes the user and selects Cowork as a service. The agent entry no longer controls access.
- **How to re-express a previous allow list as a spending policy**:

  1. Put the users from your previous allow list into a security group in Microsoft Entra ID.
  2. In the Microsoft 365 admin center, go to **Copilot** > **Cost Management** > **Configuration** and select **+ Add spending policy**.
  3. On the **Scope user and group** step, choose **Specific groups** and select the security group.
  4. On the **Select agents and services** step, select **Cowork**.
  5. Set limits, choose a billing method, and create the policy.


  Users in the group's scope then have access to Cowork, and users outside every Cowork-selecting policy don't. Get the policy authoring steps in [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

## Make Cowork discoverable to end users

IT admins can control Cowork's discoverability for end users. Learn more in [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

If an admin makes Cowork discoverable to end users but doesn't enable usage-based billing, end users can request to access Cowork directly in the app. Admins need to review and approve requests based on policy, cost, and compliance.

## Manage plugins

Cowork supports plugins from the Microsoft 365 App Store that add skills and connectors to extend what Cowork can do. As an admin, you control which plugins are available, how they're deployed, and who can use them.

Get the admin guide on plugin deployment, availability controls, connector authentication, and monitoring in [Manage plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins) and [Manage plugins in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-tools-for-agent?view=o365-worldwide&preserve-view=true#developer-prerequisites).

## Manage models

Cowork ships with several models, which are described in [Choose a model for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models).

As an admin, you can turn off the Anthropic model family in the Microsoft 365 admin center under **Copilot Settings**. Learn more about managing models and data retention in [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

### Model availability versus access

Model settings control which models a user sees, not whether the user can use Cowork. The two are separate concerns:

- Turning off the Anthropic model family is a model control and has no effect on whether a user can access Cowork. Access is granted by a spending policy that selects Cowork. Learn more in [How access to Copilot Cowork is determined](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-access).
- The Anthropic enablement setting can be scoped to sets of users or groups.
- When the Anthropic family is off, users with Cowork access keep working with the non-Anthropic models your organization allows, such as the GPT models. **Auto** continues to select from the remaining available models, so users aren't blocked from Cowork by this setting.

Get the current list of models and model providers in [Choose a model for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models).

## Browser use

Cowork can complete web tasks for users in Microsoft Edge on their device, using their existing sign-ins and your organization's policies. Because the browser tab runs on the user's machine, browser tasks inherit the same conditional access, DLP, and tenant browsing policies you already apply to your users.

As an admin, you control:

- **Whether browser use is available to users**—The **Cowork Browsing** tenant setting in the Microsoft 365 admin center turns the capability on or off for your organization.
- **Which sites users can reach through Cowork**—Cowork respects any allowlist, blocklist, and view-only policies your organization applies to web browsing in Microsoft Edge.
- **Audit visibility**—Each browser task Cowork starts on behalf of a user is recorded in the unified audit log alongside other Cowork activity.

Learn about *admin* browser controls in [Admin control](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser#admin-control).

Learn about the *end-user* experience in [Use the local browser with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser).

## Usage-based billing

Cowork uses a usage-based billing model. Activities such as model responses, tool and skill calls, image generation, and browser tasks count toward your organization's consumption. Admins see usage in the Microsoft 365 admin center and can set per-user or per-group limits. Learn more about usage-based billing in [Microsoft 365 pay-as-you-go services](https://go.microsoft.com/fwlink/?LinkId=2368212).

Learn more about usage-based billing in the following links:

- [Set up and configure usage-based billing](https://go.microsoft.com/fwlink/?LinkId=2368211)
- [Understand how Copilot Credits are consumed and managed](https://aka.ms/CopilotCredits/LicensingGuide)
- [Set up Copilot Credits](https://go.microsoft.com/fwlink/?LinkId=2368211)
- [Estimate costs in the Cowork cost estimator](https://aka.ms/CustomerCoworkEstimator)
- [Gain visibility into how users engage with Cowork in the Cowork Usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/cowork-usage-report)
- [How to use the Consumption Dashboard in Insights—Cowork page](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/ai-cost-dashboard#cowork-page)

## Automated tasks

Users can create automated tasks that run without a person present: scheduled prompts that run at a set time, and event-driven tasks that run when a matching email or Teams message arrives. Cowork applies the same governance to these tasks that it applies to interactive conversations, with additional safeguards:

- **Runs with the user's permissions**—Each automated task runs as the user who created it. It sees only the data that user can see and acts only through the same governed, enterprise-compliant tools available in an interactive conversation.
- **Approval controls**—By default, Cowork asks the user for approval before an automated task sends an email, posts a message, or changes a shared system. Users can pre-authorize actions when they create a task. Learn more in [Set up event-driven tasks](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#set-up-event-driven-tasks).
- **Rate limits and loop protection**—Automated tasks have limits on how often they can run, and Cowork guards against tasks that trigger themselves in a loop.
- **Audit visibility**—Automated task activity is recorded in the unified audit log alongside other Cowork activity, and Microsoft Purview data security and compliance policies apply.

## Security and compliance

Microsoft Purview is available to secure and govern Cowork. Learn more in [Use Microsoft Purview to manage data security & compliance for Microsoft Copilot Cowork](https://learn.microsoft.com/en-us/purview/ai-copilot-cowork).

### Data residency

Copilot Cowork follows the same data residency model as Copilot. Learn more in [Data residency for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot).

### How Cowork processes user data during a task

When Cowork runs a user's task, it processes the user's files in a temporary, isolated environment inside the *Microsoft 365 service boundary*. Cowork uses the files only for the duration of the task and removes the temporary environment when the task finishes. Users can't view or access this environment.

The Microsoft 365 service boundary is the security and data-processing boundary of your Microsoft 365 tenant. Learn more in [Microsoft Copilot architecture and how it works](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture).

## Related content

- [How access to Copilot Cowork is determined](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-access)
- [Choose a model for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models)
- [Use the local browser with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser)
- [Manage plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins)
- [Microsoft Purview data security and compliance protections for Microsoft Copilot](https://learn.microsoft.com/en-us/purview/ai-m365-copilot)
- [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps)
- [Agent availability settings](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-availability)
- [Deploy agents in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-deploy)
- [Microsoft Copilot agent installation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-agent-install)
- [Agents admin guide for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-admin-guide)
- [Cowork network endpoints](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-network-endpoints)
-
