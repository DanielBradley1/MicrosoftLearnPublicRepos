<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-setup -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Set up Microsoft Copilot and assign licenses

As part of your [Microsoft Copilot adoption](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-enablement-resources), the next step is to enable security features, configure the update channel, and assign Copilot licenses to users. This article provides guidance for IT administrators on how to prepare your organization for Microsoft Copilot. It covers foundational implementation and readiness activities, licensing, and steps to ensure a secure and compliant deployment.

[![Diagram that shows the setup and assign license step to adopt and enable Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-enablement-resources/setup-m365-copilot-assign-licenses.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-enablement-resources/setup-m365-copilot-assign-licenses.png#lightbox)

## Prerequisites

### Admin center roles

This article uses the following admin centers. These admin centers require a specific role to complete the tasks in the article.

- [**Microsoft 365 admin center**](https://admin.microsoft.com): Different roles are available depending on the task you need to complete. For more information about roles, see [Commonly used Microsoft 365 admin center roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles).
- [**SharePoint admin center**](https://go.microsoft.com/fwlink/?linkid=2185219): Sign in as the [SharePoint administrator](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role).
- [**Microsoft Purview portal**](https://purview.microsoft.com): Different roles are available depending on the task you need to complete. For more information, see [Permissions in the Microsoft Purview portal](https://learn.microsoft.com/en-us/purview/purview-permissions).

### Licensing

To purchase Microsoft Copilot, make sure you have an appropriate subscription plan. Microsoft Copilot is included as part of the Microsoft 365 E7 subscription plan. Microsoft Copilot licenses are available as an add-on to other licensing plans. For more information, see [Microsoft Copilot license options](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing).

You can purchase Microsoft Copilot licenses through the [Microsoft 365 admin center marketplace](https://admin.microsoft.com/adminportal/home#/catalog), Microsoft partners, or your Microsoft account team.

You might need more licenses to use some of the features described in this article, like [Microsoft Purview](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description) and [Microsoft SharePoint Premium - SharePoint Advanced Management overview](https://learn.microsoft.com/en-us/sharepoint/advanced-management#licensing).

## Readiness activities

To ensure a smooth transition to Microsoft Copilot, use the following readiness checklist:

- **Set up a test environment**: To validate configurations and test scenarios, establish a test environment with necessary licenses.
- **Conduct pilot testing**: To identify any issues and gather feedback, do pilot testing with a select group of users.
- **Develop a communication plan**: Create a communication plan to inform users about the upcoming changes and provide them with the necessary resources and support.
- **Review conditional access policies**: Make sure that you appropriately configure conditional access policies. Microsoft Copilot supports tenant-level conditional access policies in SharePoint. For more information, see [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).
- **Review SharePoint Search and Advanced Management Policies**: Use SharePoint Advanced Management to control access to content, prevent oversharing, and manage content lifecycle. For more information, see [Get ready for Microsoft Copilot with SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/get-ready-copilot-sharepoint-advanced-management).

  Additionally, consider implementing restricted SharePoint search to limit the discoverability of sensitive content. For more information, see [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance).
- **Ensure network compliance**: Make sure that your network meets the requirements for Microsoft Copilot services. For more information, see [Microsoft Copilot network requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

## Security measures

To ensure a secure and compliant environment for Microsoft Copilot, it's crucial to implement robust security measures. Some key components are multifactor authentication, audit logging, and restricting sensitive information. These measures help protect against unauthorized access and provide visibility into user and admin activities.

### Multifactor authentication \(MFA\)

Multifactor authentication is a critical security measure that requires users to provide two or more verification factors to access a resource such as an application or online account. When you implement MFA, it helps protect against unauthorized access and enhances the security of your organization's data. For more information, see [Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks).

Steps to implement MFA:

- **Enable MFA for all users**: Use the Microsoft 365 admin center to enable MFA for all users in your organization. For more information, see [Set up multifactor authentication for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/security-and-compliance/set-up-multi-factor-authentication).
- **Configure conditional access policies**: Set up conditional access policies to enforce MFA based on user risk, location, and device compliance. For a tutorial, see [Secure user sign-in events with Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa).
- **Educate users**: Provide training and resources to help users understand the importance of MFA and how to use it effectively.

### Audit logging

Audit logging is essential for tracking and monitoring activities within your Microsoft 365 environment. It helps you detect and respond to potential security incidents and ensures compliance with regulatory requirements. For more information, see [Audit logging and monitoring overview](https://learn.microsoft.com/en-us/compliance/assurance/assurance-audit-logging).

Steps to implement audit logging:

- **Enable unified audit logging**: To capture all user and admin activities, turn on unified audit logging in the Microsoft Purview portal.
- **Configure audit log retention**: Set up retention policies to ensure that audit logs are retained for the required period based on your organization's compliance needs.
- **Monitor and review logs**: Regularly monitor and review audit logs to identify any suspicious activities or potential security threats.

### Restrict sensitive info from Copilot

To protect sensitive information during the deployment and use of Microsoft Copilot, follow these steps to identify, assess, and mitigate oversharing risks. These measures help maintain data security and compliance within your organization.

- **Identify most popular sites and assess oversharing**: Export the top 100 most used sites from the SharePoint admin center and run the SharePoint Advanced Management permission state report. For more information, see [Secure by default with Microsoft Purview](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-securebydefault-intro).
- **Grant Copilot access to popular, low-risk sites**: Cross-reference the report results from SharePoint Advanced Management and the Microsoft Purview Data Security Posture Management \(DSPM\) oversharing posture assessment with the top 100 used sites.
- **Turn on proactive audit and protection**: Disable **everyone except external users \(EEEU\)** at the tenant level and enable Purview Audit to monitor Copilot interaction activity. For more information, see [Protect your sensitive data with Microsoft Purview](https://learn.microsoft.com/en-us/purview/information-protection).
- **Implement access controls and labeling**: Start a SharePoint Advanced Management Access Review for all sites that are overshared. Then apply restricted access control on business-critical sites. For more information, see [Get ready for Microsoft Copilot with SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/get-ready-copilot-sharepoint-advanced-management).

For detailed steps, see [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance).

## Get started and deploy

### Step 1: Update channels

✅ **Use the Current Channel or Monthly Enterprise Channel to update apps**

Microsoft Copilot follows the Microsoft 365 Apps standard practice for deployment and updates. It's available in all update channels, *except* for Semi-Annual Enterprise Channel.

Your options:

- **Production** channels:

  - **Current Channel** provides your users with the newest Microsoft 365 app features as soon as they're ready. It provides the best experience for a fast-moving product, like Copilot.
  - **Monthly Enterprise Channel** is more predictable for when Microsoft releases these new Microsoft 365 app features each month. It's a good option for organizations that want to validate the new features before they're released to the Current Channel.

- **Preview** channels include **Current Channel \(Preview\)** and **Beta Channel**.

  Preview channels are a great option to validate the product before rolling out to the rest of organization. For more information, see [Overview of update channels for Microsoft 365 Apps](https://learn.microsoft.com/en-us/microsoft-365-apps/updates/overview-update-channels) and [Compare Microsoft 365 Insider channels](https://learn.microsoft.com/en-us/microsoft-365-apps/insider/compare-channels).

You can manage channels for user devices in multiple ways. For more information, see [Change update channel of Microsoft 365 to enable Copilot](https://learn.microsoft.com/en-us/microsoft-365-apps/updates/change-channel-for-copilot).

### Step 2: Provision Microsoft Copilot licenses

✅ **Assign Copilot licenses by using the Microsoft 365 admin center**

Before you assign Copilot licenses, make sure that you provision users and assign Microsoft 365 licenses to users in your tenant. Your options:

- Use the [Microsoft Copilot setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=learndocs#/modernonboarding/microsoft365copilotsetupguide)
- Use the Microsoft 365 admin center features to [Add users and assign licenses](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/add-users).
- [Use PowerShell to assign Microsoft 365 licenses](https://learn.microsoft.com/en-us/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell).

Next, assign Copilot licenses so users can start using it. You can manage Microsoft Copilot licenses in the Microsoft 365 admin center. You can assign to individual users or to groups of users, and also reassign licenses to other users.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and go to **Billing** > **Licenses**.
2. Select **Microsoft Copilot**.
3. In the product details page, assign licenses to users and manage their access to Copilot and other apps and services.
4. To check if a user is added, go to **Users** > **Active Users**. This page shows all users and any active licenses.

When you assign licenses, Copilot shows up in Microsoft 365 apps, like Word and Excel. For some apps, users might need to wait up to 24 hours for Copilot to appear. They might also need to restart or refresh the app. Once enabled, Copilot appears across the apps.

To use Copilot, users sign into the app with their work or school account and the file must be editable, not read-only. In some experiences like Word, a Copilot dialog shows when you create a new document. In other experiences, Copilot is accessible on the ribbon.

Note

Chat experiences in Word, Excel, PowerPoint vary depending on your tenant configuration and license. Learn more in [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview#copilot-features-in-microsoft-365-apps). If you'd like to enable users with priority access to these capabilities, learn more about [Microsoft Copilot](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise).

Note

- It's not supported to assign Copilot licenses to cross-tenant users, including guests.
- For education customers, the Copilot license is listed under **Microsoft 365 A3 Extra Features for faculty** or **Microsoft 365 A5 Extra Features for faculty**.

You can also manage licenses from the Copilot page in the Microsoft 365 admin center. For more information, see [Microsoft 365 reports in the admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-usage).

For more information, see [Assign Microsoft 365 licenses to users](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users).

### Step 3: Configure settings for Copilot

✅ **Configure more Copilot features**

You can manage settings by using Copilot controls. They provide centralized access to admin features and capabilities that benefit your organization.

To access these settings, go to the [Microsoft 365 admin center](https://admin.microsoft.com)> **Copilot**.

With Copilot controls, you can:

- View the status of Copilot license assignments.
- Access the latest information on Copilot.
- Manage data security and compliance controls.
- Submit feedback on behalf of users.
- Configure plugins and permissions.
- Enable the use of web data as grounding data in Copilot.

For more information, see [Manage Microsoft Copilot scenarios](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-page) and [configure the Microsoft Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-admin-settings).

### Step 4 - Deploy to some users and measure adoption

When you're ready to assign Copilot licenses to your users, follow these three phases:

1. **Pilot**: To test the deployment and gather feedback, assign licenses to a small group of users.
2. **Deploy**: Assign licenses to a larger group of users.
3. **Operate**: Monitor usage and adoption, and make adjustments as needed.

For more information about these phases, and possible actions you can take in each phase, see the [Microsoft deployment blueprint to address oversharing in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#committed-to-responsible-ai).

#### Pilot

✅ **Create a group of early adopters**

There are many uses of Microsoft Copilot across the various Microsoft 365 productivity apps. Users can find value in different ways.

To help drive adoption, create a group of early adopters. This group can help you understand how users are using Copilot and how it's valuable to them.

1. Identify users across various business groups in your organization, ideally with high usage of existing Microsoft 365 features. You can identify these users by [reviewing usage metrics](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft365-apps-usage-ww) in the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Assign these users Microsoft Copilot licenses and onboard them to Copilot. For more resources to help at this stage, see the [user engagement tools and templates](https://adoption.microsoft.com/copilot/user-engagement-tools-and-templates/) in the Microsoft Copilot adoption hub.
3. As these users get more comfortable with using Copilot, they can speak to how they use it best, and where it's most valuable for them. This information provides you with product champions that can help other users adopt and use Copilot across your organization.

   With your established community of early adopters or champions, they can better speak to their peers within their organization. These champions can contextualize the value of Copilot to best suit their needs. This framework also provides your IT department with a scalable way to handle questions through champions, developing a team of experts across your organization.

For more information about driving adoption, visit the [Microsoft Copilot adoption hub](https://adoption.microsoft.com/Copilot/).

#### Deploy

✅ **Fully deploy Copilot licenses to all users in your organization**

To deploy Copilot licenses to all users in your organization, follow these steps:

1. Use the Microsoft 365 admin center to assign licenses to individual users or groups of users, depending on your needs.
2. Before users begin using Copilot, make sure that you assign the appropriate licenses to them. This step makes sure that everyone has access to the features they need and can participate fully in the Copilot experience.

During this phase, also include the following activities:

- Focus on preventing oversharing by limiting external sharing, restricting access to certain files or folders, and setting up alerts to notify you of any unusual activity.
- Use sensitivity labels to classify and protect sensitive information. These labels allow you to automatically encrypt files containing sensitive data or restrict access to files marked as "confidential."

For more information on these important data security steps, see [Copilot controls security and governance](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/security-governance).

#### Operate

✅ **Get insights and user sentiment**

To measure the impact of Copilot on your organization, use the [Copilot Dashboard from Viva Insights](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard), and the [Microsoft 365 usage reports in the admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports). These tools provide organizational leaders and IT decision makers with insights into readiness, adoption, impact, and user sentiment.

For more information, see the following articles:

- [Copilot controls measurement and reporting](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/measurement-reporting)
- [Open the Microsoft Copilot Dashboard from Viva Insights](https://aka.ms/copilotdashboard)
- [Learn more about the Microsoft Copilot Dashboard from Viva Insights](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard)
- [Microsoft 365 reports in the admin center - Microsoft Copilot usage](https://learn.microsoft.com/en-us/microsoft-365/admin//activity-reports/microsoft-365-copilot-usage)
- [Microsoft 365 reports in the admin center - Microsoft Copilot readiness](https://learn.microsoft.com/en-us/microsoft-365/admin//activity-reports/microsoft-365-copilot-readiness)

## Related content

- [Copilot controls overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/overview)
- [Microsoft Copilot setup guide in the Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?Q=learndocs#/modernonboarding/microsoft365copilotsetupguide)
- [Microsoft Copilot help and learning for end users](https://support.microsoft.com/microsoft-365-copilot)
- [Microsoft Copilot discussions in the Microsoft Community](https://techcommunity.microsoft.com/category/Microsoft365Copilot)

Tip

We recommend using the [Copilot License Details](https://aka.ms/CopilotLicenseDetails) diagnostic to verify that a specific user account meets the necessary requirements to access Copilot features.
