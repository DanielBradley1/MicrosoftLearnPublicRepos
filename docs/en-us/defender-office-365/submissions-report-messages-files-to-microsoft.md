<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/submissions-report-messages-files-to-microsoft -->
<!-- Sitemap-Last-Modified: 2026-07-22 -->

# How do I report a suspicious email, Teams message, or file to Microsoft?

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Wondering what to do with suspicious email messages, Teams messages, URLs, email attachments, or files? In all organizations with cloud mailboxes, *users* and *admins* have different ways to report suspicious email messages, URLs, and email attachments to Microsoft. In organizations with Microsoft Defender for Office 365 Plan 1 or Plan 2, or Microsoft Defender XDR, users can also report suspicious Teams messages and calls.

Admins in Microsoft 365 organizations with Microsoft Defender for Endpoint also have several methods for reporting files.

Watch this video for more information about the unified submissions experience.

<iframe src="https://learn-video.azurefd.net/vod/player?id=65c688e4-8b79-4a39-a731-ddbffa053448" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Watch this video to learn how users report suspicious email messages, email attachments, and Teams messages to Microsoft.

<iframe src="https://www.youtube-nocookie.com/embed/jC1k3Pc2Mwc" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Report suspicious email messages to Microsoft

Important

When you make a submission to Microsoft, everything associated with the submission is copied and included in the continual algorithm reviews. This copy includes all data associated with the submission, including message content, headers, any attachments, related data about routing, and all other data directly associated with the submission.

Microsoft treats your submission as your organization's permission to analyze all the information to fine-tune the submission hygiene algorithms. Your submission is held in secured and audited data centers in the USA. The submission is deleted as soon as it's no longer required. Microsoft personnel might read your submitted messages and attachments, which is normally not permitted for customer data in Microsoft 365. However, your submission is still treated as confidential between you and Microsoft, and your data isn't shared with any other party as part of the review process. Microsoft might also use AI to evaluate and create responses tailored to your submissions.

For information about reporting messages and calls in Microsoft Teams in Defender for Office 365 Plan 1 or Plan 2, see [User reported settings in Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams).

| Method | Submission type | Comments |
| --- | --- | --- |
| [The built-in Report button in supported versions of Outlook](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages#use-the-built-in-report-button-in-outlook) | User |  |
| [The Submissions page in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin) | Admin | Admins can report good \(false positives\) and bad \(false negatives\) messages, email attachments, and URLs \(entities\) from the available tabs on the **Submissions** page.  <br>  <br>Admins can also submit user reported messages from the **User reported** tab on the **Submissions** page to Microsoft for analysis. The **Submissions** page is available only in organizations with cloud mailboxes. |
| Report messages from quarantine | Admin and User | Admins can [submit quarantined messages to Microsoft for analysis](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#submit-email-to-microsoft-for-review-from-quarantine) \(false positives and false negatives\).  <br>  <br>If users are allowed to [release their own messages from quarantine](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user#release-quarantined-email), and [user reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox) is configured to allow users to report quarantined messages, users can select **Report message as having no threats** \(false positive\) when they release a quarantined message. |
| [Report messages and calls in Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/submissions-teams#how-users-report-items-in-teams) | User | In organizations with Defender for Office 365 Plan 1 or Plan 2, or Microsoft Defender XDR, users can report malicious messages and calls in Microsoft Teams. |

Note

If your organization doesn't have Microsoft Defender for Office 365, users and admins can still report suspicious emails by submitting them directly through the Microsoft submission portals \(for example, the Microsoft malware or phishing submission sites\). Forwarding suspicious emails isn't a replacement for Defender-based reporting and might not include full message metadata required for analysis.

## Related reporting settings for admins

[User reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox) allow admins to configure whether user reported messages go to a specified reporting mailbox, to Microsoft, or both. After this feature is configured, user reported messages appear on the **User reported** tab on the **Submissions** page in the Defender portal.

User reported messages are also available to admins in the following locations in the Microsoft Defender portal:

- [User-reported messages report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#user-reported-messages-report)
- [Automated investigation and response \(AIR\) results](https://learn.microsoft.com/en-us/defender-office-365/air-view-investigation-results) \(Defender for Office 365 Plan 2\)
- [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) \(Defender for Office 365 Plan 2\)

In Defender for Office 365, admins can also submit messages from the [Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page#actions-on-the-email-entity-page) and from [Alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts) in the Defender portal.

Admins can use the sample submission portal at [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission) to submit other suspected files to Microsoft for analysis. For more information, see [Submit files for analysis](https://learn.microsoft.com/en-us/defender-xdr/submission-guide).

To report suspected phishing or fraud, you can also go directly to the [Submissions page](https://security.microsoft.com/reportsubmission) in the Defender portal.

If you encounter a tech support scam, report it at [Report a scam](https://www.microsoft.com/concern/scam).

Tip

In U.S. Government organizations \(Microsoft 365 GCC, GCC High, and DoD\), admins can submit messages to Microsoft for analysis. The messages are analyzed for email authentication and policy checks only. Payload reputation, detonation, and grader analysis aren't done for compliance reasons \(data isn't allowed to leave the organization boundary\). If you report a message, URL, or email attachment to Microsoft from one of these organizations, you get the following message in the result details:

**Further investigation needed**. Your tenant doesn't allow data to leave the environment, so nothing was found during the initial scan. You'll need to contact Microsoft support to have this item reviewed.
