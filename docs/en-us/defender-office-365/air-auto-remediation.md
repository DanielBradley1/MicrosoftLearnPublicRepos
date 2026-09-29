<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/air-auto-remediation -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Automated remediation in Automated investigation and response \(AIR\)

By default, remediation actions identified by automated investigation and response \(AIR\) in Microsoft Defender for Office 365 Plan 2 require approval by security operations \(SecOps\) teams. For more information about AIR, see [Automated investigation and response \(AIR\) in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-about)

Now, admins can also designate certain actions to automatically remediate. Automatically remediating messages identified as malicious in AIR investigations has the following benefits:

- Increases customer protection by expediting remediation of more threats.
- Saves time for SecOps teams by reducing the need for approval.

The rest of this article describes how to configure automated remediation in AIR and how to identify messages that were automatically remediated.

## Configure automated remediation

AIR creates a cluster around a detected malicious file or URL, and then the automated investigation checks the location of messages within the cluster. If the messages are in mailboxes, AIR produces a remediation action.

After you select the cluster types to automatically remediate, the selected remediation action occurs without the need for SecOps approval.

Tip

Clusters produced by AIR that don't automatically remediate still show as **Pending action** as they do today.

Clusters larger than 10,000 messages don't automatically remediate and show as **Pending action** for review.

Use the following steps to select the cluster types to automatically remediate:

In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Settings** > **Email & collaboration** > **MDO automation settings**. Or, to go directly to the **Automation settings** page, use [https://security.microsoft.com/securitysettings/mdoAutomationSettings](https://security.microsoft.com/securitysettings/mdoAutomationSettings).

The following settings are available on the **Automation settings** page:

- **Message clusters** section: Specifies the types of message clusters that are automatically remediated. Choose one or more of the following options:

  - **Similar files:** When the automated investigation recognizes a malicious file, it creates a cluster around the malicious file. The cluster groups all messages that contain the file into the cluster. Selecting this setting opts the organization in to automated remediation for these malicious file clusters.
  - **Similar URLs:** When the automated investigation recognizes a malicious URL, it creates a cluster around the malicious URL. The cluster groups all messages that contain the URL into the cluster. Selecting this setting opts the organization in to automated remediation for these malicious URL clusters.
  - **Multiple similar attributes**: Messages that share various attributes, such as subject or sender IP address. The automated investigation creates queries \(clusters\) of email using various attributes from the original email: sender values \(IP address, sender domain\) and contents \(subject, cluster ID\) to find email that might be related. he following similarity clusters that are created:

    - BodyFingerprintBin1/SenderIp
    - BodyFingerprintBin1/P2SenderDomain
    - Subject/P2SenderDomain
    - Subject/SenderIp


    Selecting this setting opts your organization into automated remediation if these clusters are found to be malicious.

- **Remediation action** section: Specifies the action to take on message cluster types specified in the **Message clusters** section.

  Currently, **Soft delete** is the only available action. For more information about soft deleted messages, see [Recoverable Items folder in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder).

  Important

  The ability to recover soft deleted messages depends on the retention policy for soft deleted messages in each mailbox. Verify your legal obligations for email retention, including messages marked as malicious. For more information on the retention of soft deleted messages, see [Change how long permanently deleted items are kept for an Exchange Online mailbox in Exchange Online](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).

When you're finished on the **Automation settings** page, select **Save**.

[![Screenshot of automated remediation of malicious entity clusters configuration in the Defender portal at Settings \\> Email & collaboration \\> MDO automation settings.](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-automation-settings.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-automation-settings.png#lightbox)

## Review automatically remediated messages

The following subsection shows how to use the Defender portal to review automated remediation actions.

### Automated remediation results in the Action center

In the Action center at [https://security.microsoft.com/action-center/](https://security.microsoft.com/action-center/), automatically remediated clusters appear on the **History** tab. Use the **Decided by** filter with the value **Automation** to return clusters that were automatically remediated.

For more information about the Action center, see [The Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

[![Screenshot of the History tab in the Action center with automatically remediated clusters filtered by the Decided by value Automation and the Action source value Automated email action.](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-action-center.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-action-center.png#lightbox)

### Automated remediation results in investigations

Within an investigation in AIR, automatically remediated clusters appear on the **Pending action history** tab of the investigation with the **Handled by** value **Automation**.

For more information about AIR investigation results, see [Details and results of automated investigation and response \(AIR\) in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-view-investigation-results).

[![Screenshot of the Pending actions history tab of an investigation with automatically remediated clusters with the Handled by value Automation.](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-investigations.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-investigations.png#lightbox)

### Automated remediation results in Threat Explorer

In Threat Explorer \(Explorer\), automatically remediated messages have the **Additional action** value **Automated remediation:automated**.

For more information about Threat Explorer, see [About Threat Explorer and Real-time detections in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about).

[![Screenshot of Threat Explorer showing messages that automated remediation deleted from the mailbox by automated remediation \(filtered by the Additional action value Automated remediation\).](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-threat-explorer.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-threat-explorer.png#lightbox)

### Automated remediation results in Advanced hunting

In Advanced hunting, automatically remediated messages are in the `EmailPostDeliveryEvents` table with both of the following property values:

- `ActionType` equals **Automated Remediation**
- `ActionTrigger` equals **Automation**.

For more information about Advanced hunting, see [Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

[![Screenshot of Advanced hunting for messages removed from mailboxes by automated remediation \(EmailPostDeliveryEvents table where the ActionType value is Automated Remediation and the ActionTrigger value is Automation.\)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-advanced-hunting.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-advanced-hunting.png#lightbox)

## Revert automated remediation actions on messages

Note

The ability to recover messages depends on the data still being available in Defender and the mailbox retention settings for soft deleted messages. For more information, see the following articles:

- [Data retention information for Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-data-retention)
- [Recoverable Items folder in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder)
- [Change how long permanently deleted items are kept for an Exchange Online mailbox in Exchange Online](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention)

The following methods are available to revert automated remediation actions and restore messages to mailboxes:

- ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-take-actions.png) **Take action** on the message in Threat Explorer or Advanced Hunting. For information about the **Take action** wizard, see [The Take action wizard](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting#the-take-action-wizard).
- The **Move to Inbox** or ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-more-actions.png) > **Move to Junk** actions in the cluster property details flyout on **History** tab of the Action center as shown in the following screenshot:

  [![Screenshot of the details flyout of an automatically remediated email cluster showing the available Move to Inbox action to undo the automated remediation action and restore messages to mailboxes.](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-action-center-cluster-details.png)](https://learn.microsoft.com/en-us/defender-office-365/media/auto-air-mdo-action-center-cluster-details.png#lightbox)

## See also

- [AIR in Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-about)
- [Review and manage remediation actions in AIR in Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-review-approve-pending-completed-actions)
- [Remediate malicious email delivered in Office 365](https://learn.microsoft.com/en-us/defender-office-365/remediate-malicious-email-delivered-office-365)
