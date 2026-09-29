<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/user-tags-about -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# User tags in Microsoft Defender for Office 365

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

*User tags* are identifiers for specific groups of users in [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about). There are two types of user tags:

- **System tags**: Currently, [Priority account](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts) is the only type of system tag.
- **Custom tags**: You create these types of tags.

If your organization has Defender for Office 365 \(included in your subscription or as an add-on\), you can create custom user tags in addition to using the Priority account tag:

- You can assign the Priority account tag to a maximum of 250 users.
- You can create a maximum of 500 custom user tags.
- You can assign a custom tag to a maximum of 10000 individual users.
- If you assign a custom user tag to a group, the tag is applied to the first 999 group members \(users\).

This article explains how to configure user tags in the Microsoft Defender portal. You can also apply or remove the Priority account tag using the *VIP* parameter on the [Set-User](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-user) cmdlet in [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell). No PowerShell cmdlets are available to manage custom user tags.

To see how user tags are part of the strategy to help protect high-impact user accounts, see [Security recommendations for priority accounts](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-security-recommendations).

## What do you need to know before you begin?

Before you begin, make sure you can access the Microsoft Defender portal and that you have the required permissions.

- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). To go directly to the **User tags** page, use [https://security.microsoft.com/securitysettings/userTags](https://security.microsoft.com/securitysettings/userTags).
- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Microsoft Defender XDR Unified role based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) \(If **Email & collaboration** > **Defender for Office 365** permissions is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **Active**. Affects the Defender portal only, not PowerShell\): **Authorization and settings/System settings/manage** or **Authorization and settings/System settings/Read-only**.
  - [Email & collaboration permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions):

    - *Create, modify, and delete custom user tags*: Membership in the **Organization Management** or **Security Administrator** role groups.
    - *Apply and remove the Priority account tag from users*: Membership in the **Security Administrator** and **Exchange Admin** role groups.
    - *Apply and remove existing custom user tags from users*: Membership in the **Organization Management** or **Security Administrator** role groups.


    Tip


    User tag management is controlled by the **Tag Reader** and **Tag Manager** roles in Email & collaboration permissions.

  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup> and **Security Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

Important

<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

- You can also manage and monitor the Priority account tag in the Microsoft 365 admin center. For instructions, see [Manage and monitor priority accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts).
- For information about securing *privileged accounts* \(admin accounts\), see [Privileged access management](https://learn.microsoft.com/en-us/purview/privileged-access-management).

## Use the Microsoft Defender portal to create user tags

Use the following steps to create a custom user tag in the Microsoft Defender portal:

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Settings** > **Email & collaboration** > **User tags**. Or, to go directly to the **User tags** page, use [https://security.microsoft.com/securitysettings/userTags](https://security.microsoft.com/securitysettings/userTags).
2. On the **User tags** page, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Create** to start the new tag wizard.
3. On the **Define tag** page, configure the following settings:

   - **Name**: Enter a unique, descriptive name for the tag. You can't rename a tag after you create it.
   - **Description**: Enter an optional description for the tag.


   When you're finished on the **User tags** page, select **Next**.

4. On the **Assign members** page, do either of the following steps:

   - Select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Add members**. In the **Add members** flyout that opens, do any of the following steps to add individual users or groups in the **Search users and groups to add** box:

     - Click in the box and scroll through the list to select a user or group.
     - Or, start typing a name to filter the list, and then select the value below the box.


     To add more members, click in an empty area in the box, and then type another name or scroll the list to select another user or group.


     To remove individual entries from the box, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-remove-selection.png) next to the entry.


     When you're finished on the **Add members** flyout, select **Add**.


     Back on the **Assign members** page, the users and groups that you added are listed by **Name** and **Type**. To remove entries from the list, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** next to the entry.

   - Select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-download.png) **Import** to select a text file that contains the email addresses of the users or groups \(one entry per line\).


   When you're finished on the **Assign members** page, select **Next**.

5. On the **Review tag** page, review your settings. You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or the specific page in the wizard.

   When you're finished on the **Review tag** page, select **Submit**.
6. On the **New tag created** page, you can select the links to add a new tag or manage the tag members.

   When you're finished on the **New tag created** page, select **Done**.

   Note

   It can take up to 8 hours to completely apply tags.

   If you assign a group to a user tag, members of the group at the time of tag creation are assigned tag. Users later added to the group aren't automatically assigned the user tag.

## Use the Microsoft Defender portal to view user tags

In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Settings** > **Email & collaboration** > **User tags**. Or, to go directly to the **User tags** page, use [https://security.microsoft.com/securitysettings/userTags](https://security.microsoft.com/securitysettings/userTags).

On the **User tags** page, you can sort the entries by clicking on an available column header. The following columns are available:

- **Tag**: The name of the user tag.
- **Applied to**: The number of members
- **Last modified**
- **Created on**

Use ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-filter.png) **Filter** to filter the user tags by **Last modified date**.

Use the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-search.png) **Search** box and a corresponding value to find specific user tag.

Select a user tag by clicking anywhere in the row other than the check box next to the name to open the details flyout for the user tag.

The details flyout of the user tag contains the following information, based on the type of tag:

- **System tags**: The details flyout for the Priority account tag contains the following information:

  - **Last updated**
  - **Description**
  - A link to [https://security.microsoft.com/securitysettings/priorityAccountProtection](https://security.microsoft.com/securitysettings/priorityAccountProtection) to turn on or turn off [priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection)
  - **Applied to**

- **Custom tags**: The details flyout for a custom tag contains the same information as the **User tags** page, plus the list of users and groups that the tag applies to.

## Use the Microsoft Defender portal to modify user tags

After you select the user tag, use either of the following methods to modify it:

- **On the User tags page**: Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit** action that appears.
- **In the details flyout of the selected user tag**: Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit** action at the top of the flyout.

The modify tag wizard uses the same **Define tag**, **Assign members**, and **Review tag** pages described in [Use the Microsoft Defender portal to create user tags](#use-the-microsoft-defender-portal-to-create-user-tags), with the following exceptions:

- You can't rename or change the description of the Priority account tag, so the **Define tag** page isn't available for the Priority account tag.
- The **Define tag** page is available for custom tags, but you can't rename the tag; you can only change the description.

## Use the Microsoft Defender portal to remove user tags

You can't remove the built-in Priority account tag.

Warning

Removing a custom user tag is permanent and can't be undone. The tag is removed from all users and groups it's assigned to, and it's no longer available in reports and features. Make sure you want to delete the tag before you proceed.

After you select the custom tag, use either of the following methods to remove it:

- **On the User tags page**: Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** action that appears.
- **In the details flyout of the selected user tag**: Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** action at the top of the flyout.

Read the warning in the confirmation dialog that opens, and then select **Yes, remove**.

Back on the **User tags** page, the custom tag is no longer listed.

## User tags in reports and features

After you apply system tags or custom tags to users, you can use those tags as filters in the following features in Defender for Office 365:

- [Alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts)
- [Incidents](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-manage-incidents-and-alerts)
- [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)
- [Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page)
- [Quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files) Currently, tag selection on the Quarantine filter page supports the Priority tag only.
- [Admin submissions and user reported messages](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin)
- [Email security reports](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security)

  - [Compromised user report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#compromised-users-report)
  - [Submissions report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#submissions-report)
  - [Threat protection status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#threat-protection-status-report)
  - [Top senders and recipients report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#top-senders-and-recipients-report)

- [Campaigns](https://learn.microsoft.com/en-us/defender-office-365/campaigns)
- [Custom alert policies](https://learn.microsoft.com/en-us/defender-xdr/alert-policies#view-alerts)
- [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)

  - [Simulations](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations)
  - [Simulation automations](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulation-automations)
  - [Payloads](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-payloads)
  - [Training campaigns](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-training-campaigns)
  - [Training modules](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-training-modules)

- In organizations above a certain size, the [Email issues for priority accounts report](https://learn.microsoft.com/en-us/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) is available in the Exchange admin center \(EAC\).

For information about where the effects of priority account protection are visible, see [Review differentiated protection from priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection#review-differentiated-protection-from-priority-account-protection).

## Related content

For more information about priority accounts, see the following articles:

- [Configure and review priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection)
- [Manage and monitor priority accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts)
