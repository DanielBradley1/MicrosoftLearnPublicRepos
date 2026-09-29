<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-take-action -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Take action on advanced hunting query results

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

You can quickly contain threats or address compromised assets found in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview). You can take actions on devices, identities, files, and emails.

## Required permissions

To take action on devices through advanced hunting, you need a role in Microsoft Defender for Endpoint with [permissions to submit remediation actions on devices](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options).

If you can't take action, contact a Global Administrator about getting the following permission:

*Active remediation actions > Security Operations*.

To take action on emails through advanced hunting, you need a role in Microsoft Defender for Office 365 to [search and purge emails](https://learn.microsoft.com/en-us/defender-office-365/scc-permissions).

- [Microsoft Defender Unified role based access control \(URBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac): Membership assigned with the following URBAC permissions enables the **Take action** option in advanced hunting and grants users the required permissions to perform remediation actions:

  - **Security operations** > **Security data** > **Response \(manage\)**: Required to approve or dismiss remediation actions.
  - **Security operations** > **Security data** > **Email & collaboration advanced actions \(manage\)**: Required to take actions on emails \(move, soft delete, hard delete\).

## Take actions on devices

You can take the following actions on devices identified by the `DeviceId` column in your query results:

- Isolate affected devices to contain an infection or prevent attacks from moving laterally.
- Collect an investigation package to obtain more forensic information.
- Run an antivirus scan to find and remove threats by using the latest security intelligence updates.
- Initiate an automated investigation to check and remediate threats on the device and possibly other affected devices.
- Restrict app execution to only Microsoft-signed executable files, preventing subsequent threat activity through malware or other untrusted executables.

To learn more about how Microsoft Defender for Endpoint performs these response actions, see [Response actions on devices](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).

## Take actions on identities

You can take the following actions on identities in your query results:

- Select **Disable user** to temporarily prevent a user from signing in.
- Select **Reset user authentication** to prompt the user to either change their password on their next sign-in session \(for on-premises identities\) or require them to sign in again \(for Microsoft Entra identities\).

[![Screenshot of the Take actions wizard with the Users section highlighted, including Disable user and Reset user authentication.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/take-actions-user-actions.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/take-actions-user-actions.png#lightbox)

Both the **Disable user** and **Reset user authentication** options require the user security identifier \(SID\), which is available in the `AccountSid`, `InitiatingProcessAccountSid`, `RequestAccountSid`, and `OnPremSid` columns.

For Microsoft Entra identities, the `AccountObjectId` parameter is required for all actions.

For more information on identity actions, see [Remediation actions in Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/remediation-actions) and [Remediation actions in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Quarantine files

You can deploy the *quarantine* action on files so that the files are automatically quarantined when encountered. When you select the **quarantine** action, you can choose between the following columns to identify which files in your query results to quarantine:

- `SHA1`: In most advanced hunting tables, this column refers to the SHA-1 of the file that's affected by the recorded action. For example, if a file was copied, this affected file is the copied file.
- `InitiatingProcessSHA1`: In most advanced hunting tables, this column refers to the file responsible for initiating the recorded action. For example, if a child process was launched, this initiator file is part of the parent process.
- `SHA256`: This column is the SHA-256 equivalent of the file identified by the `SHA1` column.
- `InitiatingProcessSHA256`: This column is the SHA-256 equivalent of the file identified by the `InitiatingProcessSHA1` column.

To learn more about how to quarantine files and restore them, see [Response actions on files](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

Note

To locate files and quarantine them, the query results should also include `DeviceId` values as device identifiers.

To take any of the device or file actions described in this section, select one or more records in your query results and then select **Take actions**. A wizard guides you through the process of selecting and then submitting your preferred actions.

[![Screenshot of the take actions option in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/take-action-multiple.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/take-action-multiple.png#lightbox)

## Take actions on emails

Apart from device-focused remediation steps, you can also take actions on emails from your query results. Select the records you want to take action on, select **Take actions**, and then under **Choose actions**, select your choice from the following options:

- **Move to mailbox folder** - select this action to move the email messages to the Junk, Inbox, or Deleted items folder.

  You can move quarantined email results \(such as false positives\) back to the inbox by selecting the **Inbox** option.

  [![Screenshot of the Inbox option under take actions pane in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-quarantine-results.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-quarantine-results.png#lightbox)
- **Delete email** - select this action to move email messages to the Deleted items folder \(**Soft delete**\) or delete them permanently \(**Hard delete**\).

  Selecting **Soft delete** also automatically soft deletes the messages from the sender's Sent Items folder if the sender is in the organization.

  [![Screenshot of the Take actions pane with the Soft delete option and the automatic sender copy deletion setting.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/soft-delete-sender-copy.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/soft-delete-sender-copy.png#lightbox)

  Automatic soft-deletion of the sender's copy is available for results using the [`EmailEvents`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailevents-table) and [`EmailPostDeliveryEvents`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailpostdeliveryevents-table) tables but not the [`UrlClickEvents`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-urlclickevents-table) table. Also, the result should contain the `EmailDirection` and `SenderFromAddress` columns for the **Delete email** option to show up in the **Take actions** wizard. Sender's copy clean-up applies to intra-organization emails and outbound emails, ensuring that only the sender's copy is soft-deleted for these email messages. Inbound messages are out of scope.

  The following query lists email events classified as spam and returns key message and delivery details:

  ```kusto
  EmailEvents
  | where ThreatTypes contains "spam"
  | project NetworkMessageId,RecipientEmailAddress, EmailDirection, SenderFromAddress, LatestDeliveryAction,LatestDeliveryLocation
  ```

- **Submit to Microsoft** - select this action to submit false positive or false negative emails to Microsoft.

  As part of the submission, you can also add URLs and URL domains, sender domains, and file attachments to the Tenant Allow/Block List to immediately mitigate the reported false positive or false negative while Microsoft evaluates the submission.

  Important

  To block a URL or URL domain, join the [`EmailUrlInfo`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailurlinfo-table) table with `NetworkMessageId` to get the required details. To block an attachment \(file\), join the [`EmailAttachmentInfo`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailattachmentinfo-table) table with `NetworkMessageId` to get the file's hash.

  **Submit to Microsoft** might be disabled if mandatory columns are missing. To resolve missing mandatory columns, select **Show empty columns** before you select **Take actions**.

  [![Screenshot of Choose actions page of the Take actions wizard with Submit to Microsoft selected and the Selected entities to block details flyout.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-take-actions-submit-to-microsoft.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-take-actions-submit-to-microsoft.png#lightbox)
- **Initiate automated investigation** - select this action to trigger [Automated investigation](https://learn.microsoft.com/en-us/defender-office-365/air-about) on email, sender, recipient, or contact recipients.

  **Initiate automated investigation** might be disabled if mandatory columns are missing. To resolve missing mandatory columns, select **Show empty columns** before you select **Take actions**.

  [![Screenshot of the Choose actions page of the Take actions wizard with Initiate automated investigation selected.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-take-actions-choose-actions.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/advanced-hunting-take-actions-choose-actions.png#lightbox)

You can provide a remediation name and a short description of the action to track it in the action center history. Use the Approval ID provided at the end of the wizard to filter for these actions in the action center:

[![Screenshot of the Take actions wizard showing the Choose actions step for selected entities.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/choose-email-actions-entities.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-take-action/choose-email-actions-entities.png#lightbox)

The email remediation actions described in this section also apply to [custom detections](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview).

## Review actions taken

The [Action center history](https://security.microsoft.com/action-center/history) page \(**Action center** > **History**\) records each action individually. To check the status of each action, go to the [action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

Note

Some tables in this article might not be available in Microsoft Defender for Endpoint. [Turn on Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable) to hunt for threats by using more data sources. To move your advanced hunting workflows from Microsoft Defender for Endpoint to Microsoft Defender, see [Migrate advanced hunting queries from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde).

## Related content

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Work with query results](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Action center overview](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
