<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-admin-settings -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Configure Microsoft Copilot settings in the Microsoft 365 admin center

As an administrator, you can manage many Microsoft Copilot settings from **Copilot** > **Settings** in the [Microsoft 365 admin center](https://admin.microsoft.com). Some settings you configure there, and others link to the admin center or policy service where you make the change.

This article describes settings for user access, data access, Copilot actions, and the Microsoft Copilot app experience. The settings you see depend on your organization's licenses, enabled features, and rollout status. A setting's location or availability might differ from what's described here.

Note

- If you're an end user on a work or school device, your IT admin configures Copilot for your organization. To help you get started, see the [Copilot prompt gallery](https://m365.cloud.microsoft/copilot-prompts).
- If you're an end user on a personal device, you might have Microsoft Copilot as part of your individual Microsoft 365 subscription. See [Microsoft Copilot for individuals](https://www.microsoft.com/microsoft-copilot/for-individuals) and [Get started with the Microsoft Copilot app](https://support.microsoft.com/microsoft-365-copilot/what-is-microsoft-copilot-app).

## Before you begin

**Check permissions for the task.** To manage Copilot settings in the Microsoft 365 admin center, use an appropriate admin role, such as **AI Administrator**. If you have the **Global Reader** role, you can view but not change settings. Controls that open another service require the permissions for that service. For example, creating Cloud Policy settings for Microsoft 365 apps requires the **Office Apps admin** role. Use the least-privileged role that lets you complete the task. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

**Check licensing and feature availability.** Copilot capabilities and the controls that are available to manage them vary by license and service. For help identifying the experience your organization uses, see [Compare Microsoft 365 Copilot licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-overview#compare-microsoft-365-copilot-licenses).

## Find a Copilot setting

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. In the left navigation, expand **Copilot**, and then select **Settings**.
3. Browse **User access**, **Data access**, **Copilot actions**, and **Other settings**. Select **View all** or **All settings** when a setting isn't shown in a category.

The following sections distinguish controls you configure in the Microsoft 365 admin center from links to another service. For a setting that opens another service, make the change in that service rather than on the Copilot settings page.

Some settings might or might not appear, depending on your particular tenant, location, license, or Microsoft 365 plan.

## Configure user access

| Setting | What you can manage | Where to make the change |
| --- | --- | --- |
| **Copilot Frontier** | Choose which users or groups can access eligible preview features. | **Copilot** > **Settings** > **View all** > **Copilot Frontier**. See [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier). |
| **Copilot in Bing, Edge, and Windows** | Review access guidance for Copilot Chat in these experiences. | The Copilot settings page provides information; it isn't the configuration location. See [Manage Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage) and [Windows and Microsoft Copilot Chat experience](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot). |
| **Copilot in Edge** | Configure applicable Copilot features in Microsoft Edge. | Follow the link to Microsoft Edge configuration policies, or go to **Settings** > **Microsoft Edge** > **Configuration policies**. See [Get started with Microsoft Edge configuration policies](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-management-service). |
| **Copilot pay-as-you-go billing** | Set up a billing policy for eligible Copilot Chat usage. | Open **Copilot pay-as-you-go billing**, then use **Billing & usage** > **Pay-as-you-go services**. See [Microsoft Copilot pay-as-you-go overview for IT admins](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/pay-as-you-go-overview). |
| **Microsoft Copilot in admin centers** | Manage whether eligible admins can use Copilot in supported admin centers. The Microsoft 365 Admin agent is an assistive, agentic experience that helps IT administrators operate Microsoft 365, Microsoft Copilot, and agents at AI scale. | **Copilot** > **Settings** > **User access** > **Microsoft Copilot in admin centers**. See [Use Microsoft 365 Admin agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-admin-agent). |
| **Microsoft Copilot self-service purchases** | Allow trials or purchases, allow trials only, or prevent self-service purchases. | **Copilot** > **Settings** > **User access** > **Microsoft Copilot self-service purchases**. See [Self-service purchase FAQ](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/self-service-purchase-faq). |
| **Pin the Microsoft Copilot app to the Windows taskbar** | Make the app easier for users to open from Windows. | Use the taskbar-pinning control in **Copilot** > **Settings** > **User access**. See [Pin Microsoft Copilot app to the Windows taskbar](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-taskbar). |
| **Pin Microsoft Copilot Chat** | Control whether Chat is pinned in supported app navigation. | **Copilot** > **Settings** > **User access** > **Pin Copilot Chat**. See [Pin Microsoft Copilot Chat in Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-chat-navbar). |

**Microsoft Security Copilot** is a separate service. If its entry appears in Copilot settings, it opens the [Security Copilot portal](https://securitycopilot.microsoft.com/); you don't configure that service on the Microsoft 365 Copilot settings page. For more information, see [Microsoft Security Copilot overview](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot).

## Configure data access

| Setting | What you can manage | Where to make the change |
| --- | --- | --- |
| **Agents** | Control access to agents and which agents users can install or use. | **Copilot** > **Settings** > **Data access** > **Agents**. For additional agent management, follow **Manage all agents**. See [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps). |
| **AI providers operating as independent processors** | Manage access to AI models from a third-party that processes data under its own data processing commitments, privacy, compliance, and enterprise terms. | **Copilot** > **Settings** > **Data access** > **AI providers operating as independent processors**. See [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview#ai-independent-processor). |
| **AI providers operating as Microsoft subprocessors** | Manage access to AI models from a third-party that handles data on Microsoft's behalf and under [Microsoft's Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802), [Product Terms](https://go.microsoft.com/fwlink/?linkid=2356100), and [enterprise safeguards](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). | **Copilot** > **Settings** > **View all** > **AI providers operating as Microsoft subprocessors**. See [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview#ai-subprocessor). |
| **Azure DevOps data in Microsoft 365 Copilot** | Choose which users can use the available Azure DevOps integration. | **Copilot** > **Settings** > **All settings** > **Azure DevOps data in Microsoft 365 Copilot**, where available. Review the data-sharing information in the setting before enabling access. See [Set up the remote Azure DevOps MCP Server](https://learn.microsoft.com/en-us/azure/devops/mcp-server/remote-mcp-server). |
| **Copilot in Power Platform and Dynamics 365** | Manage product-specific Copilot and agent settings. | Follow the shortcut to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/copilot). See [Copilot features in Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/copilot/copilot-hub). |
| **Data security and compliance** | Configure applicable security, governance, and compliance protections. | Follow the shortcuts to the [Microsoft Purview portal](https://purview.microsoft.com/). See [Microsoft Purview protections for generative AI apps](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview) and [Configure a secure and governed data foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot). |
| **People Skills in Microsoft Copilot** | Set up and manage People Skills. | Follow the link from **Copilot** > **Settings** > **Data access** > **People Skills in Microsoft Copilot**, or go to **Settings** > **Viva** > **Data management** > **People Skills**. See [Overview of People Skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview). |
| **Recommendations for Microsoft Copilot licensing** | Manage licensing recommendations based on eligible Microsoft 365 activity. Use the Microsoft Copilot readiness report to view the recommendations. | **Copilot** > **Settings** > **Data access** > **Recommendations for Microsoft Copilot licensing**. Viewing recommendations also requires permissions to manage user licenses. See [Microsoft Copilot readiness report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-readiness). |
| **Web search for Microsoft Copilot and Microsoft Copilot Chat** | Control whether Copilot can use public web content in supported experiences. | Follow the link from Copilot settings to create an **Allow web search in Copilot** cloud policy in the [Microsoft 365 Apps admin center](https://config.office.com/officeSettings/officePolicies). See [Data, privacy, and security for web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access). |

## Configure Copilot actions

| Setting | What you can manage | Where to make the change |
| --- | --- | --- |
| **Copilot image generation** | Allow or prevent supported image-generation experiences. | **Copilot** > **Settings** > **Copilot actions** > **Copilot image generation**. |
| **Screen and camera sharing** | Manage Vision in Microsoft Copilot. | **Copilot** > **Settings** > **Copilot actions** > **Screen and camera sharing**. Turning off this setting doesn't turn off voice. See [How vision in Microsoft Copilot works](https://support.microsoft.com/microsoft-365-copilot/how-vision-microsoft-365-works). |
| **Copilot in Teams meetings** | Manage Copilot behavior for Teams meetings and calls. | Follow the shortcut to the [Teams admin center](https://admin.teams.microsoft.com). See [Microsoft Copilot in Teams meetings and events](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-transcription) and [Manage Microsoft Copilot in Teams calls](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-calling-transcription). |

## Configure other settings

- **Copilot custom dictionary:** Go to **Copilot** > **Settings** > **Other settings** > **Copilot custom dictionary** to manage organization-specific vocabulary used in supported Teams experiences. See [Manage custom dictionaries for Microsoft Teams meetings and events](https://learn.microsoft.com/en-us/microsoftteams/copilot-custom-dictionary).
- **Copilot diagnostics logs:** Go to **Copilot** > **Settings** > **Other settings** > **Copilot diagnostics logs** to submit diagnostic information to Microsoft on behalf of users who can't submit feedback themselves. Submissions can include Copilot prompts and responses, relevant content samples, and log files to help Microsoft investigate issues and improve Copilot experiences. This process temporarily overrides user-level feedback policies. Review the information before submitting it. For more information, see [Manage Microsoft feedback for your organization](https://learn.microsoft.com/en-us/privacy/microsoft-365/feedback/feedback-manage).

  Note

  For information on how Copilot diagnostic logs and feedback are handled in Microsoft 365 US government environments \(GCC, GCC High, and DoD\), see [Feedback policies in United States government environments](https://learn.microsoft.com/en-us/privacy/microsoft-365/feedback/feedback-manage#feedback-policies-in-united-states-government-environments).

## Configure the Microsoft Copilot app experience

Some controls that affect what users see in the Microsoft Copilot app are managed outside **Copilot** > **Settings**. Use the appropriate service or policy for each feature.

| App feature | How to manage it |
| --- | --- |
| **Search** | Configure Microsoft Search under **Settings** > **Search & intelligence** in the Microsoft 365 admin center. You can also manage applicable item-insights settings. See [Set up Microsoft Search](https://learn.microsoft.com/en-us/microsoftsearch/setup-microsoft-search) and [Item insights in Microsoft 365](https://learn.microsoft.com/en-us/graph/item-insights-overview). |
| **Chat** | Use **Pin Copilot Chat** to manage supported navigation placement. For other Chat controls, including web search, see [Manage Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage). |
| **Agents** | Use the **Agents** controls described under **Data access**. Additional deployment and blocking controls are available under **Settings** > **Integrated apps**. See [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps). |
| **Pages and Notebooks** | Use the applicable Cloud Policy settings to manage whether users can create and view Copilot Pages and Copilot Notebooks. See [Admin policies for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration). |
| **Create** | Built-in Create features aren't configured individually. To make organization brand kits available in Create, set up the applicable Cloud Policy. See [Configure brand kit governance and organizational assets](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-brand-kit-governance-organizational-assets). |
| **Copilot key** | Use supported Windows policies or the Microsoft Intune settings catalog to manage the keyboard's Copilot key. See [Policies to manage the Copilot key](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot#policies-to-manage-the-copilot-key). |

## Related content

- [What is the Microsoft Copilot app?](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-app-overview)
- [Optimize Microsoft Copilot configuration settings](https://learn.microsoft.com/en-us/microsoft-365/copilot/optimize-copilot-configuration-settings)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Remove or prevent installation of the Copilot app](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot#remove-or-prevent-installation-of-the-copilot-app)
