<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-manage-content-sharing -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# Manage content sharing for Microsoft Copilot

## Overview

Note

**The Microsoft 365 Copilot app is now called Microsoft Copilot**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

Session and response sharing in Microsoft Copilot lets users share Copilot work with others through a link. Users can share either a full Copilot conversation or a single Copilot response.

As an admin, you can manage whether users in your organization can share Copilot sessions and responses.

These settings apply to Copilot sharing in the Microsoft Copilot app and Microsoft 365 apps. Copilot sharing is turned on by default.

Note

Sharing a Copilot session or response doesn't give recipients access to files, emails, chats, meetings, or other Microsoft 365 content referenced in the conversation. Existing Microsoft 365 permissions still apply.

## Prerequisites

To access and manage Copilot sharing settings, you need access to the Microsoft 365 admin center and one of the following administrator roles:

- **View sharing settings:** AI Reader
- **Edit sharing settings:** AI Admin

For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Understand session and response sharing

Microsoft Copilot supports two sharing experiences:

- **Session sharing** lets users share an entire Copilot conversation, including all prompts and responses. When a recipient opens a shared session, they see a snapshot of the conversation as it existed when it was shared. If the recipient continues the conversation, Copilot creates a separate copy in their chat history.
- **Response sharing** lets users share a single Copilot response along with the prompt that generated it. Like session sharing, a recipient can continue working from the shared response. Copilot creates a separate copy in the recipient's chat history.

For user-facing instructions, see [Share conversations and responses in Microsoft Copilot](https://support.microsoft.com/microsoft-365-copilot/share-conversations-responses-in-microsoft-copilot).

## Understand Copilot sharing settings

Copilot sharing includes one primary sharing control.

| Setting | What it controls |
| --- | --- |
| **Allow users to share Copilot responses** | Manages Copilot session and response sharing for your entire organization. This setting also controls whether users can share content with lower-sensitivity labels, such as General or Public, or no sensitivity label. |

If **Allow users to share Copilot responses** is turned off, users can't create new sharing links.

## Turn Copilot sharing on or off

Use the primary sharing setting to control whether users can share Copilot sessions and responses.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), expand **Copilot**, and then select **Settings**.
2. Select **Copilot sharing**.
3. Select or clear **Allow users to share Copilot responses**.
4. Select **Save**.

When Copilot sharing is turned off:

- Users can't create new session or response sharing links.
- The **Share** option doesn't appear in Copilot or Microsoft 365 apps, including the **More options** menu for a meeting.

New settings apply to new sharing attempts after you select **Save**. Allow some time for a settings change to take effect across your organization.

## How sharing settings affect users

| Configuration | User experience |
| --- | --- |
| Copilot sharing is on | Users can create sharing links for Copilot sessions and responses. |
| Copilot sharing is off | Users can't create new sharing links, and the **Share** option doesn't appear in Copilot. |
| Settings are changed | Changes apply to new sharing attempts after you save the settings. Existing recipient copies aren't affected. |

If a recipient already continued from a shared session or response, that copy remains a separate conversation in their chat history.

## Monitor sharing activity

Microsoft Purview records Copilot sharing activity, including sharing events, link access, and blocked sharing attempts.

Use audit logs to:

- Review who shared content.
- Review when shared links were opened.
- Review when a share attempt was blocked by policy.
- Verify sharing settings are working as expected.
- Investigate sharing activity for compliance and governance reviews.

To learn more about Microsoft Purview audit logs, see [Access the Security Copilot audit log](https://learn.microsoft.com/en-us/copilot/security/audit-log).

## Related content

- [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)
- [Learn about sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels)
