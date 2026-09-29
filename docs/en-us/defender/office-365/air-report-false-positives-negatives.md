<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/air-report-false-positives-negatives -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Report false positives or false negatives in automated investigation and response \(AIR\)

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Automated investigation and response \(AIR\) in Microsoft Defender for Office 365 Plan 2 includes powerful capabilities to detect and investigate threats. For more information, see [Automated investigation and response](https://learn.microsoft.com/en-us/defender-office-365/air-about).

But what if AIR incorrectly identifies an email message, attachment, or URL as a threat \(a false positive\) or missed an item that turned out to be a threat \(a false negative\)? This article explains the options that are available to security operations \(SecOps\) personnel to deal with false positives and false negatives from AIR.

## Submit false positives or false negatives to Microsoft

You can submit or resubmit false positive and false negative items to Microsoft. These items include email messages, email attachments, and URLs. For instructions, see [Use the Submissions page to submit suspected spam, phish, URLs, legitimate email getting blocked, and email attachments to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin).

## Adjust alerts to prevent false positives from recurring

The instructions depend on the available subscriptions in your organization:

- **Microsoft Defender XDR**: [Tune an alert](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts#tune-an-alert)
- **Defender for Endpoint**: Create **Allow** actions for files, IP addresses URLs or domains that are misidentified as malware on devices. For instructions, see [Create indicators](https://learn.microsoft.com/en-us/defender-endpoint/manage-indicators).

## Prerequisites

Before you undo remediation actions, verify that you have the required permissions and licensing. For details, see [Required permissions and licensing for AIR](https://learn.microsoft.com/en-us/defender-office-365/air-about#required-permissions-and-licensing-for-air).

## Undo remediation actions

SecOps personnel can often use ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-take-actions.png) **Take action** to undo the remediation action that AIR applied to the item. For example:

- From Explorer \(Threat Explorer\). For details, see [Email remediation](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting#email-remediation).
- From the Email entity page. For more information, see [Actions on the Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page#actions-on-the-email-entity-page).
- From the details flyout of entries on the **History** tab of the Action center at [https://security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history).

For details about the available actions in ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-take-actions.png) **Take action**, see the [Take action wizard](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting#the-take-action-wizard).

- To take action on messages that were moved to the Junk Email folder in the mailbox, use **Take action** > **Move to mailbox folder** and then select one of the following destinations:

  - **Inbox** for false positives.
  - **Deleted Items**, **Soft deleted items**, or **Hard deleted items** for false negatives.

- To take action on messages that were quarantined, do one of the following steps:

  - To release the message, use **Take action** > **Move to mailbox folder** > **Inbox** and then select **Release to one or more of the original recipients of the email** or **Release to all recipients**. Or, you can [release the message directly from quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#release-quarantined-email).
  - [Delete the message directly from quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#delete-email-from-quarantine) if the user has access to the quarantined message.
  - If the user doesn't have access to the quarantined message, you don't need to do anything \(the message eventually expires based on the [quarantine retention](https://learn.microsoft.com/en-us/defender-office-365/quarantine-about#quarantine-retention) period\).

- To take action on files that were quarantined, do one of the following steps:

  - [Release the quarantined file from quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#release-quarantined-files-from-quarantine).
  - [Delete the quarantined file from quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#delete-quarantined-files-from-quarantine) if the user has access to the quarantined file.
  - If the user doesn't have access to the quarantined file, you don't need to do anything \(the file eventually expires based on the [quarantine retention](https://learn.microsoft.com/en-us/defender-office-365/quarantine-about#quarantine-retention) period\).

## Related content

- [Microsoft Defender for Office 365 overview](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
- [Automated investigation and response \(AIR\) in Microsoft Defender for Office 365 Plan 2](https://learn.microsoft.com/en-us/defender-office-365/air-about)
