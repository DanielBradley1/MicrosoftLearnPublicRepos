<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-threat-analytics-notifications -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Get email notifications for Threat analytics updates in Microsoft Defender XDR

You can set up email notifications that send you updates on [threat analytics](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics) reports. These notifications alert security administrators and analysts when new threat analytics reports are published or existing reports are updated in Microsoft Defender XDR. This article walks you through creating a notification rule, choosing which report types or tags to track, and adding recipients.

## Set up email notifications for report updates

To set up email notifications for threat analytics reports, perform the following steps:

1. In the navigation pane of the Microsoft Defender portal, select **Settings > Microsoft Defender XDR**. Under **General**, select **Email notifications**.
2. In the **Threat analytics** tab, select **+ Create a notification rule**. A flyout appears.
3. Follow the steps listed in the flyout. First, give your new rule a name. The description field is optional, but a name is required. You can toggle the rule on or off using the checkbox under the description field.

   Note

   The name and description fields for a new notification rule only accept English letters and numbers. Punctuations like spaces, dashes, underscores, aren't supported.

   ![Screenshot of the notification rule naming step with rule details entered and the rule enabled](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-threat-analytics-notifications/ta_create_notification_2.png)

4. Choose the reports you want to be notified about. You can choose to be updated about all newly published or updated reports or only those reports of a certain type or with a specific tag.

   ![Screenshot of the notification configuration step with Ransomware tags selected and notification types available for selection](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-threat-analytics-notifications/ta_create_notification_3.png)

5. Add at least one recipient to receive the notification emails. You can also use this screen to send a test email to check the notification settings.

   ![Screenshot of the recipients step showing three recipients and confirmation that a test email was sent](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-threat-analytics-notifications/ta_create_notification_4.png)

6. Review your new rule. Select **Edit** at the end of each subsection to change any of the settings. Once your review is complete, select **Create rule**.

   ![Screenshot of the review step showing the option to edit the notification rule before creation](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-threat-analytics-notifications/ta_create_notification_5.png)

7. Select **Done** to complete the process and close the flyout.

   ![Screenshot of the rule created screen showing green checkmarks along the sidebar and a green check in the main area](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-threat-analytics-notifications/ta_create_notification_6.png)

Your new rule now appears in the list of Threat analytics email notifications.

## Next steps

- [Get email notifications on incidents](https://learn.microsoft.com/en-us/defender-xdr/m365d-notifications-incidents)
- [Get email notifications on response actions](https://learn.microsoft.com/en-us/defender-xdr/m365d-response-actions-notifications)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
