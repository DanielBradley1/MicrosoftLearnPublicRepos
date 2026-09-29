<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/air-user-automatic-feedback-response -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# Automatic user notifications for user reported phishing results in AIR

In Microsoft 365 organizations with [Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet), when a user reports a message as phishing, an investigation is automatically created in [automated investigation and response \(AIR\)](https://learn.microsoft.com/en-us/defender-office-365/air-about). Admins can configure the user reported message settings to send an email notification to the user who reported the message based on the verdict from AIR. This notification is also known as *automatic feedback response*. For more information, see [User reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox).

This article explains how to enable and customize automatic feedback response for specific AIR verdicts, how the notification email messages are sent, and what the notifications look like.

Tip

In organizations with Defender for Office 365 Plan 2 and Security Copilot, the [Phishing Triage Agent](https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent) complements AIR by autonomously triaging and classifying user-reported phishing emails before investigation begins, reducing manual workload for security teams.

## What do you need to know before you begin?

- The alert policy named **Email reported by user as malware or phish** must be enabled for this feature to work \(it's on by default\). For more information about this alert policy, see [Threat management alert policies](https://learn.microsoft.com/en-us/defender-xdr/alert-policies#threat-management-alert-policies).
- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). To go directly to the **User reported settings** page, use [https://security.microsoft.com/securitysettings/userSubmission](https://security.microsoft.com/securitysettings/userSubmission).
- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Email & collaboration permissions in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/mdo-portal-permissions): Membership in the **Organization Management** or **Security Administrator** role groups.
  - [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator** or **Security Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

## Use the Microsoft Defender portal to configure automatic feedback response

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Settings** > **Email & collaboration** > **User reported settings** tab. To go directly to the **User reported settings** page, use [https://security.microsoft.com/securitysettings/userSubmission](https://security.microsoft.com/securitysettings/userSubmission).
2. On the **User reported settings** page, verify that **Monitor reported messages in Outlook** is selected.
3. In the **Email notifications** > **Results email** section, select **Automatically email users the results of the investigation**, and then select one or more of the following options that appear:

   - **Phishing or malware**: An email notification is sent to the user who reported the message as phishing when AIR identifies the threat as phishing, high confidence phishing, or malware.
   - **Spam**: An email notification is sent to the user who reported the message as phishing when AIR identifies the threat as spam.
   - **No threats found**: An email notification is sent to the user who reported the message as phishing when AIR identifies no threat.


   [![Automatic feedback response options on the User reported settings page.](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback.png)](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback.png#lightbox)

4. The notification email uses the same template as when an admin selects ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-mark-and-notify.png) **Mark as and notify** on the **Submissions** page at [https://security.microsoft.com/reportsubmission](https://security.microsoft.com/reportsubmission).

   You can customize the notification email by selecting the **Customize results email** link.

   In the **Customize admin review email notifications** flyout that opens, configure the following settings on the **Phishing** \(which corresponds to the **Phishing or malware** automatic feedback response option\), **Junk** and **No threats found** tabs:

   - **Email body results text**: Enter the custom text to use. You can use different text for **Phishing**, **Junk** and **No threats found**. The maximum length is 1115 characters.
   - **Email footer text**: Enter the custom message footer text to use. The same text is used for **Phishing**, **Junk** and **No threats found**. The maximum length is 1115 characters.


   [![The user email notification customization options on the User reported settings page.](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-customize-email-notifications.png)](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-customize-email-notifications.png#lightbox)


   When you're finished in the **Customize admin review email notifications** flyout, select **Confirm** to return to the **User reported settings** page.

## How automated feedback response works

After you enable automated feedback response, the user who reported the message as phishing receives an email notification based on the AIR verdict and the selected **Automatically email users the results of the investigation** options:

Tip

The following screenshots show example notification email messages that are sent to users. As explained earlier, you can customize the notification email using the options in **Customize results email** in the user reported settings.

- **No threats found**: If a user reports a message as phishing, the submission triggers AIR on the reported message. If the investigation finds no threats, the user who reported the message receives a notification email that looks like this:

  [![An example notification email for No threats found.](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-no-threats-found-email.png)](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-no-threats-found-email.png#lightbox)
- **Spam**: If a user reports a message as phishing, the submission triggers AIR on the reported message. If the investigation finds the message is spam, the user who reported the message receives a notification email that looks like this:

  [![An example notification email for spam found.](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-spam-email.png)](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-spam-email.png#lightbox)
- **Phishing or malware**: If a user reports a message as phishing, the submission triggers AIR on the reported message. What happens next depends on the results of the investigation:

  - **High confidence phishing or malware**: The message needs to be remediated using one of the following actions:

    - Approve the recommended action \(shown as pending actions in the investigation or in the Action center\).
    - Remediation through other means \(for example, [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about)\).


    After the message has been remediated, the investigation is closed as **Remediated** or **Partially remediated**. Only when the investigation status is one of those values is the email notification sent to the user who reported the message.


    Tip


    For high confidence phishing or malware, the investigation might immediate close as **Remediated** if the message isn't found in the mailbox \(the message was deleted\). There's no pending investigation to close, so no email notification is sent to the user who reported the message.

  - **Phishing**: The investigation creates no pending actions, but the user still receives a notification email that the message was found to be phishing. The notification email looks like this:

    [![An example notification email for phishing or malware found.](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-phishing-or-malware-email.png)](https://learn.microsoft.com/en-us/defender-office-365/media/air-automatic-feedback-phishing-or-malware-email.png#lightbox)

When AIR reaches a verdict and the notification email is sent to the user who reported the message as phishing, the following property values are shown for the entry on the **User reported** tab on the **Submissions** page in the Defender portal:

- **Marked as**: Contains the verdict.
- **Marked by**: The value is **Automation**.

Whether the message was automatically or manually sent to Microsoft for review, or the message was investigated by AIR, the verdict is shown in the **Marked as** property. For more information about the **User reported** tab on the **Submissions** page, see [Admin options for user reported messages](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#admin-options-for-user-reported-messages).

## Learn More

To learn more about submissions and investigations in Defender for Microsoft 365, see the following articles:

- [Automated investigation and response in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about)
- [View the results of an automated investigation in Microsoft Defender for 365](https://learn.microsoft.com/en-us/defender-office-365/air-view-investigation-results)
- [Admin review for reported messages](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin-review-user-reported-messages)
- [Automated investigation and response \(AIR\) examples in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-examples)
