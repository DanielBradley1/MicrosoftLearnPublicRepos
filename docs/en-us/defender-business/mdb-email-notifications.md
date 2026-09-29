<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-email-notifications -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Set up email notifications

This article describes how to set up email notifications for your security team.

![Visual depicting step 4 - set up email notifications for your security team.](https://learn.microsoft.com/en-us/defender-business/media/mdb-setup-step4.png)

When you can set up email notifications for your security team, they can be notified via email whenever any alerts are generated, or new vulnerabilities are discovered.

## What to do

1. [Learn about types of email notifications](#types-of-email-notifications).
2. [View and edit email notification settings](#view-and-edit-email-notifications).
3. [Proceed to your next steps](#next-steps).

## Types of email notifications

When you set up email notifications, you can choose from the following types:

- **Vulnerabilities**: When new exploits or vulnerability events are detected.
- **Alerts & vulnerabilities**: When detected threats on devices generate alerts, or when new exploits or vulnerability events are detected.

Tip

**Email notifications aren't the only way your security team can find out about new alerts or vulnerabilities**. For example:

- Whenever your security team signs into the Microsoft Defender portal, they see cards highlighting new threats, alerts, and vulnerabilities. Defender for Business is designed to highlight important information that your security team cares about as soon as they sign in.
- The **Incidents** page. To learn more, see [View and manage incidents in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-manage-incidents).

## View and edit email notifications

To view or edit email notification settings for your company, follow these steps:

1. Go to the Microsoft Defender portal \([https://security.microsoft.com](https://security.microsoft.com)\) and sign in.
2. In the navigation pane, select **Settings**, and then select **Endpoints**. Then, under **General**, select **Email notifications**.
3. Review the information on the **Alerts** and **Vulnerabilities** tabs.

   - If you don't see any items listed on the **Alerts** tab, you can create a rule for people to be notified when alerts are generated. To get help with this task, see [Create rules for alert notifications](https://learn.microsoft.com/en-us/defender-xdr/configure-email-notifications).
   - If you don't see any items listed on the **Vulnerabilities** tab, you can create a rule for people to be notified whenever a new vulnerability is discovered. To get help with this task, see [Create rules for vulnerability events](https://learn.microsoft.com/en-us/defender-endpoint/configure-vulnerability-email-notifications).
   - If you do have rules created, select a rule to edit it. You can also delete a rule.

Important

When you set up email notifications in Defender for Business, you must assign the notification rules to specific users. Defender for Business doesn't use [role-based access control like Defender for Endpoint does](https://learn.microsoft.com/en-us/defender-endpoint/rbac).

You can't apply email notifications to device groups in Defender for Business.

## Next steps

Proceed to:

- [Step 5: Onboard devices to Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices)
- [Step 6: Set up, review, and edit your security policies and settings in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings)
