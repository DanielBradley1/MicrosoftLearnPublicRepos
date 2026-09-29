<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/m365d-response-actions-notifications -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# Get email notifications for response actions in Microsoft Defender XDR

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

You can set up email notifications in the Microsoft Defender portal to notify you about manual or automated response actions.

Manual response actions are actions that security teams can use to stop threats or aid in investigation of attacks. These actions vary depending on the Defender workload enabled in your environment.

Automated response actions are capabilities in Microsoft Defender that scale investigation and resolution to threats automatically. Automated remediation capabilities consist of [automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) and [automated investigation and response](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir).

Note

You need the **Manage security settings** permission to configure email notification settings. If you use basic permissions management, users with Security Administrator or higher roles can configure email notifications. Likewise, if your organization is using [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac), you can only create, edit, delete, and receive notifications based on device groups that you're allowed to manage.

## Create a rule for email notifications

Note

The response action email notification currently doesn't support custom detections containing response actions.

To create a rule for email notifications, perform the following steps:

1. In the navigation pane of the Microsoft Defender portal, select **Settings > Microsoft Defender XDR**. Under **General**, select **Email notifications**. Go to the **Actions** tab.

   [![Actions tab in the Microsoft Defender XDR Settings page](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig1-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig1-response-notifications.png#lightbox)
2. Select **Add notification rule**. Add a rule name and description under Basics. Both Name and Description fields accept letters, numbers, and spaces only.

   [![Basics section of the add notification rule](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig2-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig2-response-notifications.png#lightbox)
3. Proceed to the **Notification settings** section by selecting **Next** at the bottom of the pane.
4. You can choose what type of action, what status, and where the action is sourced from in the **Notification settings** section.

   [![Notifications settings section of the add notification rule](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig3-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig3-response-notifications.png#lightbox)
5. Under **Action source**, select if you want to be notified for manual or automated response actions. You can select both options.
6. Select the specific response actions in the checklist that appears under **Action**. You can choose multiple actions available in the checklist. Response actions vary depending on the Defender workload enabled in your environment. All actions selected appear in the Action field upon completion.

   [![Highlighting the Actions field in the Notification settings section of the add notification rule](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig4-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig4-response-notifications.png#lightbox)
7. You can choose to be notified based on the device groups where the response actions are applied in the **Device groups scope**. To be notified of response actions taken in all current and future device groups, selecting **All device** groups. To be notified of response actions taken in devices that belong to your selected device group, choose **Selected device groups**.

   [![Highlighting the Device groups scope in the Notification settings section of the add notification rule](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig5-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig5-response-notifications.png#lightbox)
8. Select if you want to be notified if an action is completed or failed in the **Action status** field. You can select all options available.
9. At the bottom of the pane, select **Next** to proceed to the **Recipients** section. Alternately, you can go back to the Basics section by selecting **Back**.
10. In the **Recipients** section, you can add one or more email addresses to receive notifications. Separate multiple addresses by adding a comma at the end of each address. Select **Add** to add the recipients. You can see the recipients at the bottom of the pane after successfully adding addresses.

    [![Adding multiple addresses in the Recipients section of the add notification rule](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig6-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig6-response-notifications.png#lightbox)
11. Test the notification by selecting **Send test email**. Select **Next** at the bottom of the pane to proceed to the **Review rule** section.
12. Check the rule's details in the **Review rule** section. You can edit the details by selecting **Edit** under each section's details.

    [![Highlighting the Edit option while in the Review rule section](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig7-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig7-response-notifications.png#lightbox)
13. Select **Submit** at the bottom of the pane to finish the rule creation. Recipients start receiving notifications through email based on the notification rule settings you configured. The new rule appears in the Notifications rule list under the Actions tab.
14. To edit or delete a notification rule, select the rule from the list. Select **Edit** to change the rule's details.

    Warning

    Deleting a notification rule is permanent and can't be undone.

    Select **Delete** to remove the rule.

    [![Highlighting the Edit and Delete options while in the rule list view](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig8-response-notifications.png)](https://learn.microsoft.com/en-us/defender-xdr/media/m365d-response-actions-notifications/fig8-response-notifications.png#lightbox)

Once you receive an email notification, you can go directly to the response action referenced in the notification to review or remediate it.

## Next steps

- [Get email notifications on incidents](https://learn.microsoft.com/en-us/defender-xdr/m365d-notifications-incidents)
- [Get email notifications about new reports in Threat analytics](https://learn.microsoft.com/en-us/defender-xdr/m365d-threat-analytics-notifications)

## See also

- [Configure automatic attack disruption capabilities](https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption)
- [Configure automated investigation and response](https://learn.microsoft.com/en-us/defender-xdr/m365d-configure-auto-investigation-response)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
