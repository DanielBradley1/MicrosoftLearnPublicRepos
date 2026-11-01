<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-copilot-advanced-package-uploads -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Manage advanced package uploads

## Overview

You can control who in your organization can upload advanced agent and plugin packages in Microsoft Copilot. An advanced agent is a package that uses either a Declarative Agent with actions or an MCP server. All other packages are considered basic. Basic packages include Declarative Agents with instructions only \(no actions\). Basic package uploads remain allowed and aren't impacted. This setting only applies to user-uploaded packages by members of your organization and doesn't relate to Microsoft or third-party built agents.

This setting strengthens enterprise governance and manageability by allowing you to limit advanced package uploads to specific users or Microsoft Entra ID groups, while maintaining flexibility if your organization requires broader access. The details page shows the components of the package.

## Prerequisites

To access and manage the Copilot advanced package uploads setting, you need access to the Microsoft 365 admin center and the following administrator role:

- **Edit sharing settings:** AI Admin

For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Select who can upload advanced packages

To select who can upload advanced packages:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), select **Copilot** > **Settings** > **All settings** > **Advanced package uploads**. The **Advanced package uploads** pane is displayed.
2. Select who can upload advanced packages by choosing one of the following options:

   - **All users**: All users can upload advanced agent and plugin packages.
   - **No users**: No users can upload advanced agent and plugin packages.
   - **Specific users or groups**: Only selected users or groups can upload advanced agent and plugin packages.

3. Select **Save**.

## Related content

- [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)
- [Learn about sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels)
