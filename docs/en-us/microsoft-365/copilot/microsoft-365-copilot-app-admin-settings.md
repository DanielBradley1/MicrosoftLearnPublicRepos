<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-admin-settings -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Microsoft Copilot app features that admins can control

The [Microsoft Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview) is an everyday AI productivity app for work or school. IT administrators configure Microsoft Copilot app settings to customize the experience for their organization. It includes settings and features for pinning Microsoft Copilot Chat, allowing or blocking agents, and more.

This article lists and describes the different settings that affect the Microsoft Copilot app. Follow the provided links for more information about how to configure each feature.

This article applies to:

- Microsoft Copilot

## Prerequisites

To use the features in this article, you need the **Office Apps admin** role-based access control \(RBAC\) role. This role can create the cloud policies for the Microsoft Copilot app.

Important

Use roles with the fewest permissions. Lower permissioned accounts help improve security for your organization. Global Administrator is a highly privileged role. Limit its use to emergency scenarios when you can't use an existing role. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Settings that configure the app experience

When users open the Microsoft Copilot app, they see a navigation bar. You can show or hide some features on the navigation bar, depending on your license.

Note

[Microsoft Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/get-started) for personal accounts is currently only available in the Microsoft Frontier program. You'll only see Cowork settings in the Microsoft 365 admin center from a Frontier-enabled tenant. To set up and configure Microsoft Cowork, set up and enroll users in the Frontier program. For more information, see [Get started with the Microsoft Copilot Frontier Program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier). Copilot Cowork for work or school accounts is generally available.

The following table lists the Copilot app settings that you can configure.

| Setting | Description | Related content |
| --- | --- | --- |
| Search | ✅ Turned on by default  <br>  <br>In the **[Microsoft 365 admin center](https://admin.microsoft.com)** > **Settings** > **Search & intelligence**, you can turn on Microsoft Search in the Copilot app. By default, Microsoft Search is allowed and turned on.  <br>  <br>You can also enable **Item insights** and show recommended files. Users can turn off Item insights, but we recommend that it stays on. | - [Set up Microsoft Search](https://learn.microsoft.com/en-us/microsoftsearch/setup-microsoft-search)  <br>- [Item insights in Microsoft 365](https://learn.microsoft.com/en-us/graph/item-insights-overview) |
| Chat | ✅ Pinned by default, depending on license.  <br>  <br>Depending on your license, Microsoft Copilot Chat might be automatically pinned in the Copilot app. If not, you can pin Chat to the Copilot app. | [Pin Microsoft Copilot Chat to the navigation bar](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-chat-navbar).  <br>  <br>There are Chat features you can configure that affect the Chat experience in the Copilot app, like allowing web searches. To learn more, see [Manage Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage). |
| Agents | ✅ Built-in agents turned on by default  <br>  <br>In the **[Microsoft 365 admin center](https://admin.microsoft.com)** > **Settings** > **Integrated Apps**, admins can deploy or block agents from showing in the Copilot app. End users can also add agents to their Copilot app experience. | [Manage agents for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) |
| Pages | ✅ Allowed by default  <br>  <br>Use Cloud Policy to allow users to create and view Copilot Pages in the Copilot app. | [Admin policies for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration) |
| Notebooks | ✅ Allowed by default  <br>  <br>Use Cloud Policy to allow users to create and view Copilot Notebooks in the Copilot app. | [Admin policies for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration) |
| Create | ✅ Built-in.  <br>  <br>The built-in features aren't configurable.  <br>  <br>You can use Cloud Policy to set up and publish organization brand kits that are shown when users select **Create**. | [Create enterprise brand manager policy and allow organizational asset library \(OAL\) access](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-brand-manager) |
| Copilot Key and Windows + C shortcut | ✅ Configured by default  <br>  <br>Admins can map the Copilot key to the Microsoft Copilot app. End users can also manually configure. | [Policy CSPs to manage the Copilot key](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot#policies-to-manage-the-copilot-key)  <br>  <br>You can also use the [Microsoft Intune settings catalog](https://learn.microsoft.com/en-us/intune/intune-service/configuration/settings-catalog) \(Windows AI category\) to configure the hardware key on the keyboard. |

## Related content

- [What is the Microsoft Copilot app?](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview)
- [Updated Windows and Microsoft Copilot Chat experience](https://learn.microsoft.com/en-us/windows/client-management/manage-windows-copilot)
