<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/configure-email-notifications -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Configure alert notifications in Microsoft Defender XDR

You can configure Microsoft Defender XDR to send email notifications to specified recipients for new alerts. This feature enables you to identify a group of individuals who will immediately be informed and can act on alerts based on their severity.

If you're using [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview), you can set up email notifications for specific users \(not roles or groups\).

Note

- Only users with **Manage security settings** permissions or higher roles can configure email notifications. If you've chosen to use basic permissions management, users with Security Administrator higher roles can configure email notifications.
- Device group creation is supported in Defender for Endpoint Plan 1 and Plan 2.

You can set the alert severity levels that trigger notifications. You can also add or remove recipients of the email notification. New recipients get notified about alerts triggered after they're added. For more information about alerts, see [View and organize the Alerts queue](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue).

If you're using role-based access control \(RBAC\), recipients will only receive notifications based on the device groups that were configured in the notification rule. Users with the proper permission can only create, edit, or delete notifications that are limited to their device group management scope. Only users assigned to the Global administrator role can manage notification rules that are configured for all device groups.

Note

Microsoft recommends using roles with fewer permissions for better security. The Global Administrator role, which has many permissions, should only be used in emergencies when no other role fits.

The email notification includes basic information about the alert and a link to the portal where you can do further investigation.

## Create rules for alert notifications

You can create rules that determine the devices and alert severities to send email notifications for and the notification recipients.

1. Go to the [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) and sign in using an account with the Security administrator or Global administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **General** > **Email notifications**.
3. Click **Add item**.
4. Specify the General information:

   - **Rule name** - Specify a name for the notification rule.
   - **Include organization name** - Specify the customer name that appears on the email notification.
   - **Include tenant-specific portal link** - Adds a link with the tenant ID to allow access to a specific tenant.
   - **Include device information** - Includes the device name in the email alert body.

     Note

     This information might be processed by recipient mail servers that are not in the geographic location you have selected for your Defender data.
   - **Devices** - Choose whether to notify recipients for alerts on all devices \(Global administrator role only\) or on selected device groups. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups). \(If you're using [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview), device groups do not apply.\)
   - **Alert severity** - Choose the alert severity level.

5. Click **Next**.
6. Enter the recipient's email address then click **Add recipient**. You can add multiple email addresses.
7. Check that email recipients can receive the email notifications by selecting **Send test email**.
8. Click **Save notification rule**.

## Edit a notification rule

To edit an existing notification rule, follow these steps:

1. Select the notification rule you'd like to edit.
2. Update the General and Recipient tab information.
3. Click **Save notification rule**.

## Delete a notification rule

To delete a notification rule, follow these steps:

Warning

Deleting a notification rule is permanent. Future email notifications for that rule will stop, and you must recreate the rule if you remove it by mistake.

1. Select the notification rule you'd like to delete.
2. Click **Delete**.

## Troubleshoot email notifications for alerts

The following troubleshooting information covers issues you might encounter when using email notifications for alerts.

**Problem:** Intended recipients report they're not getting the notifications.

**Solution:** Make sure that the notifications aren't blocked by email filters:

1. Check that the email notifications aren't sent to the Junk Email folder. Mark them as Not junk.
2. Check that your email security product isn't blocking the email notifications.
3. Check your email application rules that might be catching and moving your email notifications.

## Related content

- [Update data retention settings](https://learn.microsoft.com/en-us/defender-endpoint/preferences-setup)
- [Configure advanced features](https://learn.microsoft.com/en-us/defender-endpoint/advanced-features)
- [Configure vulnerability email notifications](https://learn.microsoft.com/en-us/defender-endpoint/configure-vulnerability-email-notifications)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
