<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-security-wizard -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Discovery and insights \(preview\) for Microsoft Entra roles \(formerly Security Wizard\)

## Overview

If you're starting out using Privileged Identity Management \(PIM\) in Microsoft Entra ID to manage role assignments in your organization, you can use the **Discovery and insights \(preview\)** page to get started. This feature shows you who is assigned to privileged roles in your organization and how to use PIM to quickly change permanent role assignments into just-in-time assignments. You can view or make changes to your permanent privileged role assignments in **Discovery and insights \(preview\)**. It's an analysis tool and an action tool.

## Discovery and insights \(preview\)

Before your organization starts using Privileged Identity Management, all role assignments are permanent. Users are always in their assigned roles even when they don't need their privileges. Discovery and insights \(preview\), which replaces the former Security Wizard, shows you a list of privileged roles and how many users are currently in those roles. You can list out assignments for a role to learn more about the assigned users if one or more of them are unfamiliar.

✔️ Microsoft recommends that organizations have two cloud-only emergency access accounts permanently assigned the [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role. These accounts are highly privileged and aren't assigned to specific individuals. The accounts are limited to emergency or "break glass" scenarios where normal accounts can't be used or all other administrators are accidentally locked out. These accounts should be created following the [emergency access account recommendations](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).

Also, keep role assignments permanent if a user has a Microsoft account \(in other words, an account they use to sign in to Microsoft services like Skype, or Outlook.com\). If you require multifactor authentication for a user with a Microsoft account to activate a role assignment, the user is locked out.

## Open Discovery and insights \(preview\)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator).
2. Browse to **ID Governance** > **Privileged Identity Management** > **Microsoft Entra roles** > **Discovery and insights \(preview\)**.
3. Opening the page begins the discovery process to find relevant role assignments.

   ![Screenshot showing Microsoft Entra roles Discovery and insights page.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-preview-link.png)
4. Select **Reduce Global Administrators**.

   ![Screenshot that shows the Discovery and insights \(Preview\) with the Reduce Global Administrators action selected.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-preview-page.png)
5. Review the list of Global Administrator role assignments.

   ![Screenshot showing the Roles pane showing all Global Administrators.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-global-administrator-list.png)
6. Select **Next** to select the users or groups you want to make eligible, and then select **Make eligible** or **Remove assignment**.

   ![Screenshot showing how to convert members to eligible page with options to select members you want to make eligible for roles.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-global-administrator-buttons.png)
7. Optionally, require all Global Administrators to review their own access.

   ![Screenshot showing the Global Administrators page showing the access reviews section.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-global-administrator-access-review.png)
8. After you select any of these changes, you'll see an Azure notification.
9. Select **Eliminate standing access** or **Review service principals** to repeat the above steps on other privileged roles and on service principal role assignments. For service principal role assignments, you can only remove role assignments.

   ![Screenshot showing additional insights options to eliminate standing access and review service principals.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-security-wizard/new-preview-page-service-principals.png)

## Next steps

- [Assign Microsoft Entra roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-add-role-to-user)
