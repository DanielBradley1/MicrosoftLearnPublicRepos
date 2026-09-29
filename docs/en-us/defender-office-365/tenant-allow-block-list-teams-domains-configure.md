<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-teams-domains-configure -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Block domains and addresses in Microsoft Teams using the Tenant Allow/Block List

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In all organizations with Microsoft Teams and cloud mailboxes, admins can create and manage block entries for domains and email addresses in Microsoft Teams using the Tenant Allow/Block List.

These entries also appear on the **Organization settings** tab of the **External access** page in the Microsoft Teams admin center at [https://admin.teams.microsoft.com/company-wide-settings/external-communications](https://admin.teams.microsoft.com/company-wide-settings/external-communications):

- **Blocked domains**: Entries are in the **Allow or block external domains** section:

  [![Screenshot of the External access page in the Microsoft Teams admin center showing blocked domains.](https://learn.microsoft.com/en-us/defender-office-365/media/tenant-allow-block-list-teams-domains.png)](https://learn.microsoft.com/en-us/defender-office-365/media/tenant-allow-block-list-teams-domains.png#lightbox)
- **Blocked email addresses**: Entries are in the **Block specific users from communicating with people in my organization** section:

  [![Screenshot of the External access page in the Microsoft Teams admin center showing blocked users.](https://learn.microsoft.com/en-us/defender-office-365/media/tenant-allow-block-list-teams-senders.png)](https://learn.microsoft.com/en-us/defender-office-365/media/tenant-allow-block-list-teams-senders.png#lightbox)

For more information about the Tenant Allow/Block List, see [Manage allows and blocks in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about).

The following guidance explains how security admins can manage blocked domain and sender entries for Teams in the Microsoft Defender portal. These entries also appear in the Microsoft Teams admin center. Before you begin, review the required permissions and settings in [What do you need to know before you begin?](#what-do-you-need-to-know-before-you-begin).

## What do you need to know before you begin?

Review the following requirements and considerations before you create or manage block entries for Teams senders.

- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). To go directly to the **Tenant Allow/Block Lists** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList). Then, go to the **Teams senders** tab.
- Before adding a block entry, check the [Microsoft Teams external domain anomalies report](https://learn.microsoft.com/en-us/microsoftteams/teams-analytics-and-reports/external-domain-anomalies-report) to identify suspicious external domains that might need to be blocked.
- After you add the block entry for the domain or sender address in Teams, all new Teams communication from that organization is blocked. Block communication includes new Teams meetings, chats, channels, and calls.
- On the **Organization settings** tab of the **External access** page in the Microsoft Teams admin center at [https://admin.teams.microsoft.com/company-wide-settings/external-communications](https://admin.teams.microsoft.com/company-wide-settings/external-communications), the following settings are required to create and manage block entries for domains and senders in Teams using the Tenant Allow/Block List:

  - **Teams and Skype for Business users in external organizations** must be **Allow all external domains** or **Block only specific external domains**.
  - **Allow my security team to manage blocked domains** must be ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.
  - **Block specific users from communicating with people in my organization** ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

- The maximum number of domain block entries for Microsoft Teams is 4,000.
- The maximum number of users block entries for Microsoft Teams is 200.
- Block entries for domains and senders in Teams never expire.
- A blocked domain or sender entry in Teams should be active within 24 hours.
- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in these roles gives users the required permissions and\_ permissions for other features in Microsoft 365:

    - **Add, modify, and delete entries**: Membership in the **Global Administrator**<sup>\*</sup>, **Teams Administrator**, **Security Administrator**, or **Security Operator** roles.
    - **Read-only access to entries**: **Global Reader** or **Security Reader** roles.


    Important


    <sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Create block entries for domains and addresses in Teams in the Tenant Allow/Block List

Tip

See the requirements in the [What do you need to know before you begin?](#what-do-you-need-to-know-before-you-begin) section to managed blocked domains and senders in Teams in the Tenant Allow/Block list. If you don't meet the prerequisites, you get errors adding domains or senders on **Teams senders** tab of the **Tenant Allow/Block Lists** page.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. Or, to go directly to the **Tenant Allow/Block Lists** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. On the **Tenant Allow/Block Lists** page, select the **Teams senders** tab.
3. On the **Teams senders** tab, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Block**.
4. In the **Block sender domains & addresses on Teams** flyout that opens, enter up to 20 domains separated by commas or line breaks, and then select **Add**.

   Back on the **Teams senders** tab, the domain and addresses block entries are listed. After a few minutes, the blocked domains and addresses also appear on the **Organization settings** tab of the **External access** page in the Microsoft Teams admin center at [https://admin.teams.microsoft.com/company-wide-settings/external-communications](https://admin.teams.microsoft.com/company-wide-settings/external-communications).

## View block entries for domains and addresses in Teams in the Tenant Allow/Block List

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Tenant Allow/Block Lists** in the **Rules** section. Or, to go directly to the **Tenant Allow/Block Lists** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. Select the **Teams senders** tab.
3. On the **Teams senders** tab, you can sort the entries by clicking on an available column header. The following columns are available:

   - **Value**: The domain or email address.

4. Use the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-search.png) **Search** box and a corresponding value to find specific entries.

### Remove block entries for domains and addresses in Teams in the Tenant Allow/Block List

Use the following steps to remove blocked domain or sender address entries from the Teams senders list.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. You can also go directly to the **Tenant Allow/Block Lists** page via [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. On the **Tenant Allow/Block Lists** page, select the **Teams senders** tab.
3. On **Teams senders** tab, select the entry from the list by selecting the check box next to the first column, and then select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** action that appears.

   Tip

   You can select multiple entries by selecting each check box, or select all entries by selecting the check box next to the **Value** column header.
4. Warning

   Deleting entries removes the blocked domains or addresses from the Teams senders list. The change also propagates to Teams external access settings after a few minutes.

   In the warning dialog that opens, select **Delete**.

   Back on the **Teams senders** tab, the entry is no longer listed. After a few minutes, the blocked domain and addresses disappears from the **Organization settings** tab of the **External access** page in the Microsoft Teams admin center at [https://admin.teams.microsoft.com/company-wide-settings/external-communications](https://admin.teams.microsoft.com/company-wide-settings/external-communications).

## Related content

- [Managing external access in Teams admin center](https://learn.microsoft.com/en-us/microsoftteams/trusted-organizations-external-meetings-chat?tabs=organization-settings#specify-trusted-microsoft-365-organizations)
- [Report false positives and false negatives in Teams](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams)
- [Allow or block files in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-files-configure)
- [Allow or block URLs in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-urls-configure)
