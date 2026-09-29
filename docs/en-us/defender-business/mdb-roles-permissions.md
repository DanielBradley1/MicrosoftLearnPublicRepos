<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-roles-permissions -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Assign security roles and permissions in Microsoft Defender for Business

This article describes how to assign security roles and permissions in Defender for Business.

![Visual depicting step 3 - assign security roles and permissions in Defender for Business.](https://learn.microsoft.com/en-us/defender-business/media/mdb-setup-step3.png)

Your organization's security team needs certain permissions to perform tasks, such as

- Configuring Defender for Business
- Onboarding \(or removing\) devices
- Viewing reports about devices and threat detections
- Viewing incidents and alerts
- Taking response actions on detected threats

Permissions are granted through certain roles in the [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal). These roles can be assigned in the Microsoft 365 admin center or in the Microsoft Entra admin center.

## Choose where to assign roles and permissions

Use the following links to learn about Defender for Business roles, manage assignments, and continue to the next steps:

1. [Learn about roles in Defender for Business](#roles-in-defender-for-business).
2. [View or edit role assignments for your security team](#view-and-edit-role-assignments).
3. [Proceed to your next steps](#next-steps).

## Roles in Defender for Business

The following table describes the main roles that are assigned in Defender for Business.

| Permission level | Description |
| --- | --- |
| **Security Administrator** | Security Administrators can perform the following tasks:<br><br>- View and manage security policies<br>- View, respond to, and manage alerts<br>- Take response actions on devices with detected threats<br>- View security information and reports<br><br>  <br>In general, security admins use the [Microsoft Defender portal](https://security.microsoft.com) to perform security tasks. |
| **Security Reader** | Security Readers can perform the following tasks:<br><br>- View a list of onboarded devices<br>- View security policies<br>- View alerts and detected threats<br>- View security information and reports<br><br>  <br>Security readers can't add or edit security policies, nor can they onboard devices. |

For more information about roles, see the following articles:

- [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles)
- [Security guidelines for assigning roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles#security-guidelines-for-assigning-roles)

## View and edit role assignments

Important

Microsoft recommends that you grant people access to only what they need to perform their tasks. We call this concept *least privilege* for permissions. To learn more, see [Best practices for least-privileged access for applications](https://learn.microsoft.com/en-us/entra/identity-platform/secure-least-privileged-access).

You can use the Microsoft 365 admin center or the Microsoft Entra admin center to view and edit role assignments.

- [**Microsoft 365 admin center**](#tabpanel_1_M365Admin)
- [**Microsoft Entra admin center**](#tabpanel_1_Entra)

Use the following steps to open a user account in the Microsoft 365 admin center and manage role assignments:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com) and sign in.
2. In the navigation pane, go to **Users** > **Active users**.
3. Select a user account to open their flyout pane.
4. On the **Account** tab, under **Roles**, select **Manage roles**.
5. To add or remove a role, use one of the following procedures:
   | Task | Procedure |
   | --- | --- |
   | Add a role to a user account | 1. Select **Admin center access**, scroll down, and then expand **Show all by category**.<br>2. Select one of the following roles:<br><br>   - Security Administrator \(listed under **Security & Compliance**\)<br>   - Security Reader \(listed under **Read-only**\)<br>   - Select **Save changes**. |
   | Remove a role from a user account | 1. Either select **User \(no admin center access\)** to remove *all* admin roles, or clear the checkbox next to one or more of the assigned roles.<br>2. Select **Save changes**. |

Use the following steps in the Microsoft Entra admin center to open a user account and manage assigned roles:

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com/) and sign in.
2. In the navigation pane, go to **Users** > **All users**.
3. Open a user profile by selecting the user account.
4. To add or remove a role, use one of the following procedures:
   | Task | Procedure |
   | --- | --- |
   | Add a role to a user account | 1. Under **Manage**, select **Assigned roles**, and then choose **+ Add assignments**.  <br>  <br>2. Search for one of the following roles, select it, and then choose **Add** to assign that role to the user account.  <br>  <br>- Security Administrator  <br>- Security Reader |
   | Remove a role from a user account | 1. Under **Manage**, select **Assigned roles**.  <br>  <br>2. Select one or more administrative roles, and then select **X Remove assignments**. |

## Next steps

After you assign roles and permissions, continue with the remaining Defender for Business setup steps:

- [Set up email notifications for your security team](https://learn.microsoft.com/en-us/defender-business/mdb-email-notifications). Configure email notifications so your security team receives alerts about new threats and vulnerabilities.
- [Onboard devices to Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices). Enroll your organization's devices so they're protected by Defender for Business.
