<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Get started with the Microsoft Copilot Frontier Program

The Microsoft Frontier program gives organizations early access to innovative and emerging AI capabilities in Microsoft 365 before those features reach general availability \(GA\). By opting in to Frontier, IT administrators can evaluate new Microsoft Copilot agents and AI-powered experiences, determine readiness for broader deployment across their tenant, and provide feedback about Frontier feature capabilities to Microsoft.

Important

Frontier is managed at the tenant level. Production tenants can safely enroll users into the Frontier program to allow your organization access to Frontier features. IT admins have explicit control which users have access to which Frontier features.

Frontier features are preview and subject to change.

Microsoft's audience-based release model helps IT admins control how features are delivered to different user groups. This release model includes:

- **Frontier** \(opt-in\) is designed for early adopters who want pre-release access to features to evaluate and prepare.
- **Standard release** is the default release experience where users receive new features as soon as they're generally available.
- **Deferred release** is for audiences in more complex environments that need additional time to validate changes before deployment.

To learn more about the audience-based release model, see [Configure modern release options for Microsoft 365 features](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options).

Access to Frontier program experiences vary depending on your organization's subscription and user roles.

Joining the Frontier program requires a Microsoft Copilot license.

Frontier features are preview and subject to change.

To learn more about the Microsoft Frontier program, what's new, and how to try what's next in AI, see [Microsoft Frontier program](https://www.microsoft.com/microsoft-365-copilot/frontier-program).

## Prerequisites

Review the following requirements and recommendations:

- Verify your admin role. You need an account that includes one of the following roles: **AI Admin**, **Security Admin**, **Office Apps Admin**.
- Verify that Microsoft Copilot licenses are assigned to users who you want to access Frontier features.

  - From the Microsoft 365 admin center, go to **Billing** > **Licenses** > **Microsoft Copilot** and confirm the assignments.
  - Users without a Microsoft Copilot license aren't presented with Frontier features.

- Verify that your own admin account has a Microsoft Copilot license. Some Frontier settings and agents in the Microsoft 365 admin center might not appear.

## Enroll users in Frontier

You can manage Frontier settings in the Microsoft 365 admin center.

To turn on Frontier preview experiences for your users, do the following steps:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Go to **Copilot** > **Settings**.
3. Select the **View all** tab.
4. In the **Search all Copilot settings** search bar, type "Frontier".
5. Select **Copilot Frontier**.
6. Choose how Frontier access is assigned in your organization:

   - **No access** \(default\)
   - **All users**
   - **Specific users**

After you turn on Frontier experiences for your organization, eligible users can access supported preview features as they're released. It might take three hours for Frontier features and agents to be available to users.

Note

Starting March 29, 2026, newly published Frontier agents are available only to Frontier-enrolled users. Frontier agents published before this date continue to be accessible to all users with a Microsoft Copilot license.

Note

Some Microsoft 365 AI features across platforms \(Windows, Mac, iOS, and Android\) are currently released as a part of the Microsoft 365 Insider program. Learn more about the [Microsoft 365 Insider Program for Business](https://aka.ms/msft365insiderbusiness).

### Allow access to Frontier agents

Before your users can access Frontier agents, make sure that agent types are approved for use.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Agent** > **Settings** > **Agent and plugin access**.
2. Verify that **Allow agents and plugins built by Microsoft** is checked. This setting allows the use of Microsoft Frontier agents.

For more information about managing access to specific agents for specific users or groups, see [Agent settings in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings).

For information about managing agents that show up in the Agent Store, see [Set up Agent Store in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-agent-store).

Note

The Frontier admin control doesn't override the settings configured in the Agent section of the admin center. If an admin turned off a Frontier agent in the Agent view, that agent isn't available to users, regardless of a user's Frontier enrollment.

Important

After you enroll users in the Frontier program, **Frontier agents** are available to them from the Agent store in Microsoft Copilot. Search for "Built by Microsoft", and Frontier program agents are displayed with **\(Frontier\)** in the name. It might take up to three hours for Frontier agents to appear in the store.

### Deploy agents to your users directly

You can install and pin specific agents to select users or groups directly rather than users needing to search the Agent store. This method helps users start using Frontier agents more quickly.

1. Go to **Agents** > **All agents**.
2. Select the agent you want to install.
3. In the **Users** tab, add the specific users or security groups that you want to use this agent.

   - Use a Microsoft Entra ID security group to target specific users who can access Frontier agents. This approach helps you validate experiences with a small group before broad rollout.

4. In the agent flyout, select **Install**. To help users find the agent, you can select **Pin for users**. The agent appears in the Microsoft Copilot app.

### Manage AI provider large language models

Some Frontier features and agents require access to large language models from AI providers, such as Anthropic. Review the requirements and understand the implications for each large language model you want to use.

To allow access to other models, use the Microsoft 365 admin center to explicitly approve each model. For more information, see [Manage AI provider settings in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-anthropic-apps#manage-the-setting-in-the-microsoft-365-admin-center).

### Configure AI-enabled Cloud PCs for Frontier

To use AI-enabled Cloud PCs during Frontier preview, you must meet the Cloud PC specifications and turn on AI-enabled features to Cloud PCs in Microsoft Intune.

To learn more about AI-enabled Cloud PCs, including minimum requirements that must be met before setup, see [AI-enabled Cloud PC \(Frontier Preview\)](https://learn.microsoft.com/en-us/windows-365/enterprise/manage-ai-enabled-features). After meeting these requirements, follow the instructions in [Manage AI-enabled features \(Frontier Preview\)](https://learn.microsoft.com/en-us/windows-365/enterprise/manage-ai-enabled-features) to set up AI-enabled Cloud PCs for your users.

Important

Frontier experiences are governed by your existing customer agreements, including the Product Terms and Microsoft Data Protection Addendum \(DPA\). Frontier experiences are preview features that allow for personal data processing, as described in the DPA. As preview features, Frontier experiences may be modified, suspended, or discontinued, may not be covered by standard support commitments or service level agreements, and may be subject to additional Frontier-specific preview terms where applicable. HIPAA Business Associate Agreement coverage is not included for Frontier experiences. Certain Frontier experiences may only be available on a paid basis. Copilot credit consumption requirements are described in the [Microsoft Copilot Credits Guide](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/ai/Microsoft-Copilot-Credits-Guide.pdf).

## Related articles

[Microsoft Frontier program](https://www.microsoft.com/microsoft-365-copilot/frontier-program)

[Modern change management for Microsoft 365 - Overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/plan-for-change-management?view=o365-worldwide)

[Configure modern release options for Microsoft 365 features](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/configure-release-options?view=o365-worldwide)
