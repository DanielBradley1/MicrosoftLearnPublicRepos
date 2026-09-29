<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/quarantine-quarantine-notifications -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Use quarantine notifications to release and report quarantined messages

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In all organizations with cloud mailboxes, quarantine holds potentially dangerous or unwanted messages. For more information, see [Quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-about).

Note

In Microsoft 365 operated by 21Vianet in China, quarantine isn't currently available in the Microsoft Defender portal. Quarantine is available only in the classic Exchange admin center \(classic EAC\).

For [supported protection features](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#step-2-assign-a-quarantine-policy-to-supported-features), *quarantine policies* define what users are allowed to do to quarantined messages based on why the message was quarantined. Default quarantine policies enforce the historical capabilities for the security feature that quarantined the message as described in the table at [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user). Admins can create and apply custom quarantine policies that define less restrictive or more restrictive capabilities for users. For more information, see [Create quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#step-1-create-quarantine-policies-in-the-microsoft-defender-portal).

Quarantine notifications aren't turned on in the default quarantine notifications named AdminOnlyAccessPolicy or DefaultFullAccessPolicy. Quarantine notifications are turned on in the following default quarantine policies:

- **DefaultFullAccessWithNotificationPolicy** that's used in [preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies).
- **NotificationEnabledPolicy** [if your organization has it](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#full-access-permissions-and-quarantine-notifications).

Otherwise, to turn on quarantine notifications in quarantine policies, you need to [create and configure a new quarantine policy](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#step-1-create-quarantine-policies-in-the-microsoft-defender-portal).

Admins can also use the global settings in quarantine policies to customize quarantine notifications in the following ways:

- Add translations in up to three languages.
- Customize the sender and logo that's used in the notification.
- Notification frequency \(every four hours, daily, or weekly\).

For instructions, see [Configure global quarantine notification settings](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#configure-global-quarantine-notification-settings-in-the-microsoft-defender-portal).

For shared mailboxes, quarantine notifications are supported only for users who are granted FullAccess permission to the shared mailbox \(assigned directly or through a cloud-only security group\). For more information, see [Use the EAC to edit shared mailbox delegation](https://learn.microsoft.com/en-us/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

Note

- Currently, quarantine management for shared mailboxes isn't supported with on-premises AD synchronized groups.
- By default, messages that are quarantined as high confidence phishing by anti-spam policies, malware by anti-malware policies or Safe Attachments, or by mail flow rules \(also known as transport rules\) are available only to admins. For more information, see the table at [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user).
- Quarantine notifications for messages sent to distribution groups or mail-enabled security groups are sent to all group members.
- Quarantine notifications for messages sent to Microsoft 365 Groups are sent to all group members only if the **Send copies of group conversations and events to group members** setting is turned on.

When users receive a quarantine notification, the following information is available for each quarantined message:

- **Sender**: The email address of the sender of the quarantined message.
- **Subject**: The Subject line of the quarantined message.
- **Date**: The date/time that the message was quarantined in UTC.

The actions that are available for messages in the quarantine notification depend on why the message was quarantined and the permissions in the associated quarantine policy. For more information, see [Quarantine policy permission details](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#quarantine-policy-permission-details).

- **Review message**: Available for all messages in quarantine notifications.

  Selecting the action takes you to the details flyout of the message in quarantine. It's the same result as going to the **Email** tab on the **Quarantine** page at [https://security.microsoft.com/quarantine?viewid=Email](https://security.microsoft.com/quarantine?viewid=Email), and selecting the message by clicking anywhere in the row other than the check box next to the first column. For more information, see [View quarantined message details](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user#view-quarantined-message-details).

  Tip

  You can't use [quarantine policy permissions](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#quarantine-policy-permission-details) to remove the **Review message** button.
- **Release**: Available for messages quarantined by features using a quarantine policy with the **Full access** permission group or the individual **Allow recipients to release a message from quarantine** \(*PermissionToRelease*\) permission. For example, DefaultFullAccessWithNotificationPolicy, NotificationEnabledPolicy, or custom quarantine policies.

  Selecting the action opens an informational web page that acknowledges the message was released from quarantine \(for example, **Spam message was released from quarantine**\). The **Release status** value of the message on the **Email** tab of the **Quarantine** page is **Released**. The message is delivered to the user's Inbox \(or some other folder, depending on any [Inbox rules](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) in the mailbox\).

  Recipients can't release quarantined messages in the following scenarios, regardless of how the quarantine policy is configured:

  - Messages quarantined as malware by anti-malware policies.
  - Messages quarantined as malware or phishing by Safe Attachments policies.
  - Messages quarantined as high confidence phishing by anti-spam policies.


  If the quarantine policy allows recipients to release messages, they can only *request* the release of these quarantined messages.

- **Request release**: Available for messages quarantined by features using a quarantine policy with the **Limited access** permission group or the individual **Allow recipients to request a message to be released from quarantine** \(*PermissionToRequestRelease*\) permission. For example, custom quarantine policies.

  Selecting the action opens an informational web page that acknowledges the request to release the message from quarantine \(**The message release request has been initiated. The tenant admin will determine if the request should be approved or denied.**\). The **Release status** value of the message on the **Email** tab of the **Quarantine** page is **Release requested**.

  By default, release requests are sent to members of the hidden TenantAdmins role group \(all users with admin privileges\) as configured in the **User requested to release a quarantined message** alert policy on the **Alert policy** page in the Defender portal at [https://security.microsoft.com/alertpoliciesv2](https://security.microsoft.com/alertpoliciesv2).
- **Block Sender**: Available for messages quarantined by features using a custom quarantine policy with the **Block sender** \(*PermissionToBlockSender*\) permission.

  This action opens an informational web page to acknowledge that the message was added to the Blocked Senders list in the user's mailbox \(for example, **Spam message sender was blocked in quarantine**\).

  For more information about the Blocked Senders list, see [Block messages from someone](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) and [Use Exchange Online PowerShell to configure the safelist collection on a mailbox](https://learn.microsoft.com/en-us/defender-office-365/configure-junk-email-settings-on-exo-mailboxes#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

  Tip

  The organization can still receive mail from the blocked sender. Messages from the sender are delivered to user Junk Email folders or to quarantine. To delete messages from the sender upon arrival, use [mail flow rules](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) \(also known as transport rules\) to **Block the message**.

[![Screenshot of a sample quarantine notification.](https://learn.microsoft.com/en-us/defender-office-365/media/quarantine-notification.png)](https://learn.microsoft.com/en-us/defender-office-365/media/quarantine-notification.png#lightbox)
