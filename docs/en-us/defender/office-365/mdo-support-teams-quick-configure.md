<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-quick-configure -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Quickly configure Microsoft Teams protection in Microsoft Defender for Office 365

Even if you aren't using Microsoft Defender for Office 365 for email protection, you can still use it for Microsoft Teams protection.

This article contains the quick steps to turn on and configure Defender for Office 365 protection for Microsoft Teams.

## What do you need to know before you begin?

- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com).
- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Microsoft Defender XDR Unified role based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) \(If **Email & collaboration** > **Defender for Office 365** permissions is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **Active**. Affects the Defender portal only, not PowerShell\): **Authorization and settings/Security settings/Core Security settings \(manage\)**.
  - [Email & collaboration permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions) and [Exchange Online permissions](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo):

    - Membership in the **Organization Management** or **Security Administrator** role groups in Email & collaboration permissions <u>and</u> membership in the **Organization Management** role group in Exchange Online permissions.

  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup> or **Security Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

    Important

    \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

- Allow up to 30 minutes for a new or updated policy to be applied.
- For more information about licensing requirements, see [Licensing terms](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#licensing-terms).
- Teams integration deployment is part of the overall deployment process of Defender for Office 365. For more information, see [Pilot and deploy Defender for Office 365](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-defender-office-365?toc=%2Fdefender-office-365%2FTOC.json&bc=%2Fdefender-office-365%2Fbreadcrumb%2Ftoc.json).
- Users are also protected with near real-time warnings for known bad links in Microsoft Teams messages, which is on by default. For more information, see [Microsoft Defender for Office 365 support for Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about).

## Step 1: Verify Safe Attachments integration for Microsoft Teams

For complete instructions, see [Turn on Safe Attachments for SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-configure).

1. In the Microsoft Defender portal, go to the **Safe Attachments** page at [https://security.microsoft.com/safeattachmentv2](https://security.microsoft.com/safeattachmentv2).
2. On the **Safe Attachments** page, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-gear.png) **Global settings**.
3. In the **Global settings** flyout that opens, go to the **Protect files in SharePoint, OneDrive, and Microsoft Teams** section to verify **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

   If the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png) **Off**, move the toggle to ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**, and then select **Save**.

Tip

- You can't restrict Safe Attachments for SharePoint, OneDrive, and Microsoft Teams to Microsoft Teams only.
- You can't scope Safe Attachments for SharePoint, OneDrive, and Microsoft Teams to specific users. It's on or off for everyone.

## Step 2: Verify Safe Links integration for Microsoft Teams

For complete instructions, see [Use the Microsoft Defender portal to modify custom Safe Links policies](https://learn.microsoft.com/en-us/defender-office-365/safe-links-policies-configure#use-the-microsoft-defender-portal-to-modify-custom-safe-links-policies).

1. In the Microsoft Defender portal, go to the **Safe Links** page at [https://security.microsoft.com/safelinksv2](https://security.microsoft.com/safelinksv2).
2. On the **Safe Links** page, verify Teams integration is turned on in any custom policies \(policies with a numerical **Priority** value\) by doing the following steps:

   1. Select the policy by clicking anywhere in the row other than the check box next to the first column.
   2. In the **Teams** section of the **Protection settings** section in the details flyout that opens, verify the value is **On: Safe Links checks a list of known, malicious links when users click links in Microsoft Teams. URLs are not rewritten**.

      If the value is **Off**, select **Edit protection settings** at the bottom of the **Protection settings** section. In the **URL & click protection settings** flyout that opens, select the check box in the **Teams** section, select **Save**, and then select **Close**.


   Repeat these steps on every custom Safe Links policy.

Important

Teams integration is on in the [Built-in protection preset security policy](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies), but any other Safe Links policies [take precedence](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies#order-of-precedence-for-preset-security-policies-and-other-threat-policies) over the Built-in protection preset security policy \(as shown in the order they're listed on the **Safe Links** page\). So, ensure that Teams protection is enabled in these policies.

## Step 3: Defender for Office 365: Verify Zero-hour auto purge \(ZAP\) for Microsoft Teams

For complete instructions, see [Configure ZAP for Teams protection in Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about#configure-zap-for-teams-protection-in-defender-for-office-365).

1. In the Microsoft Defender portal, go to the **Microsoft Teams protection** page at [https://security.microsoft.com/securitysettings/teamsProtectionPolicy](https://security.microsoft.com/securitysettings/teamsProtectionPolicy).
2. On the **Microsoft Teams protection** page, verify the toggle in the **Zero-hour auto purge \(ZAP\)** section is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

   If the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png) **Off**, move the toggle to ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**, and then select **Save**.

Tip

When ZAP for Microsoft Teams is turned on, you can use **Exclude these participants** on the **Microsoft Teams protection** page to exclude users from Teams protection. For more information, see [Configure ZAP for Teams protection in Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about#configure-zap-for-teams-protection-in-defender-for-office-365).

## Step 4: Defender for Office 365: Configure user reported settings for Microsoft Teams

For complete instructions, see [User reported settings in Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams).

1. In the Teams admin center, go to the **Settings & policies** page at [https://admin.teams.microsoft.com/one-policy/settings](https://admin.teams.microsoft.com/one-policy/settings).
2. On the **Settings & policies** page, select either the **Global \(Org-wide\) default settings** tab for all users or **Custom policies for users & groups** for specific users.
3. On the tab, go to the **Messaging** section and select **Messaging**. If you selected the **Custom policies for users & groups** tab in the previous step, do one of the following steps to edit the specific policy:

   - Click on the policy name in the **Name** column.
   - Click anywhere in the row other than the **Name** column, and then select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit** action that appears.

4. In the policy details page that opens, find the **Report a security concern** toggle, and verify the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

   If the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png) **Off**, move the toggle to ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**, and then select **Save**.

   [![Screenshot of the 'Report a security concern' toggle in Messaging policies in the Teams admin center.](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-security-risk.png)](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-security-risk.png#lightbox)
5. In the Teams admin center, go to the **Messaging settings** page at [https://admin.teams.microsoft.com/messaging/settings](https://admin.teams.microsoft.com/messaging/settings).
6. On the **Messaging settings** page, go to the **Messaging safety** section, find the **Report incorrect security detections** toggle, and verify the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

   If the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png) **Off**, move the toggle to ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**, and then select **Save**.

   [![Screenshot of the Report incorrect security detections toggle on the Messaging settings page in the Microsoft Teams admin center.](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-not-security-risk.png)](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-not-security-risk.png#lightbox)
7. In the Teams admin center, go to the **Calling settings** page at [https://admin.teams.microsoft.com/one-policy/settings/calling](https://admin.teams.microsoft.com/one-policy/settings/calling).
8. On the **Calling settings** page, go to the **General** section, find the **Report a call** toggle, and verify the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**.

   If the value is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png) **Off**, move the toggle to ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **On**, and then select **Save**.

   [![Screenshot of the 'Report a call toggle on the Call settings page in the Microsoft Teams admin center.](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-security-risk-call.png)](https://learn.microsoft.com/en-us/defender-office-365/media/submissions-teams-turn-on-off-tac-security-risk-call.png#lightbox)
9. To turn meeting reporting on or off, configure the **Allow users to report meetings** policy in the Teams admin center. For instructions, see [Turn off or turn on user reporting for meetings in the Teams admin center](https://learn.microsoft.com/en-us/microsoftteams/end-user-reporting-teams-meeting#turn-off-or-turn-on-user-reporting-for-meetings-in-the-teams-admin-center).
10. In the Microsoft Defender portal, go to the **Teams user reported settings** page at [https://security.microsoft.com/securitysettings/teamsUserSubmission](https://security.microsoft.com/securitysettings/teamsUserSubmission).
11. On the **Teams user reported settings** page, go to the **Microsoft Teams** section, and verify **Monitor reported items in Microsoft Teams** is selected.

If it's not selected, select the check box, and then select **Save**.
