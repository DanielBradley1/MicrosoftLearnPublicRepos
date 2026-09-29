<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/how-to-handle-false-positives-in-microsoft-defender-for-office-365 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# Resolve false positives for legitimate blocked emails in Microsoft Defender for Office 365

Microsoft Defender for Office 365 helps you identify and fix false positives — legitimate business emails that are mistakenly blocked as threats. Use this guide to understand *why* legitimate emails were blocked, resolve the issue, and prevent similar situations in the future.

## Prerequisites

Before you begin, make sure you meet the following requirements:

- Microsoft Defender for Office 365 Plan 1 or Plan 2 \(included in Microsoft 365 A5/E5/G5\).
- Sufficient permissions \(for example, membership in the **Security Administrator** role in [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)\).
- 5-10 minutes to complete the steps.

## Identify your false positive type

Before you begin troubleshooting, identify whether the false positive is spam-related or phishing/malware-related. The resolution steps differ based on the type of detection.

**Use the spam false positive steps in this article if**:

- Legitimate bulk email \(newsletters, marketing\) is marked as spam.
- Messages are delivered to the **Junk Email** folder instead of the Inbox.
- Messages are quarantined as spam \(not phishing or malware\).
- Message headers show a high Bulk Complaint Level \(BCL 7-9\).
- Message headers show `SFV:SPM` \(spam filter verdict\).

**Use the phishing/malware false positive steps in this article if**:

- Messages are blocked by Safe Links or Safe Attachments.
- Impersonation protection triggers incorrectly.
- Messages are detected as phishing or malware.

## Handle spam false positives

Use the following steps when legitimate email is incorrectly classified as spam.

### Step 1: Check message headers for spam indicators

Message headers reveal why a message was classified as spam. You can extract headers from the [email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page) in the Defender portal or from message properties in [Outlook message headers](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c). Use the [Message Header Analyzer](https://mha.azurewebsites.net/) to parse raw headers into a readable format. For a complete list of header fields and values, see [Anti-spam message headers](https://learn.microsoft.com/en-us/defender-office-365/message-headers-eop-mdo).

Look for these key values in the **X-Forefront-Antispam-Report** header:

| Value | Description | Implication |
| --- | --- | --- |
| `SFV:SPM` | Spam filtering verdict | Spam filtering processed the message. Use the `CAT` value to determine whether the message was identified as spam, phishing, or malware. |
| `CAT:SPM` | Category: spam | Delivered to Junk Email folder by default |
| `CAT:HSPM` | Category: high confidence spam | Quarantined by default |
| `BCL:7` to `BCL:9` | High bulk complaint level | Likely blocked by bulk mail threshold |
| `SFV:BLK` | Blocked sender | Sender is on the user's Blocked Senders list in Outlook |

### Step 2: Identify the source of the classification

Based on the header values, determine what caused the false positive:

- **Tenant Allow/Block List block entry**: Check the [email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page) overrides information, or check the Tenant Allow/Block List directly for block entries that match the sender.
- **User's Blocked Senders list**: Look for `SFV:BLK` in the message headers.
- **Exchange mail flow rule \(transport rule\)**: Look for the `X-MS-Exchange-Organization-RuleID` header.
- **Anti-spam policy settings**: A **Spam** or **High confidence spam** verdict \(`SFV:SPM` with `CAT:SPM` or `CAT:HSPM`\), or the BCL threshold is exceeded.
- **Connection filter \(IP block list\)**: Check the [connection filter policy settings](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure) for the sending IP address in the IP Block List.

### Step 3: Apply the appropriate fix

Based on the false-positive source identified in the message headers or policy checks, apply the corresponding resolution:

| Source identified | Recommended fix |
| --- | --- |
| Tenant Allow/Block List block entry | Remove the block entry or [create an allow entry for the sender](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-allow-entries-for-domains-and-email-addresses). |
| User's Blocked Senders list | Remove the sender from the user's [Blocked Senders list in Outlook](https://learn.microsoft.com/en-us/defender-office-365/configure-junk-email-settings-on-exo-mailboxes) or use an admin allow override. |
| IP block list | Add the sending IP to the [connection filter IP Allow List](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure). |
| Anti-spam policy \(spam verdict\) | [Tune the anti-spam policy](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure). For example, increase the BCL threshold or adjust the spam action. |
| Mail flow rule | Modify the [mail flow rule conditions in Exchange](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) or add exceptions for the affected sender. |
| Spam filtering error \(no organization configuration issue\) | [Submit the message to Microsoft for analysis](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-email-to-microsoft) as a false positive. |

### Step 4: Validate the fix

After you apply the selected remediation, confirm that the false-positive spam classification is resolved:

1. Ask the sender to send a test message with the same content type and sender domain.
2. Use [message trace](https://learn.microsoft.com/en-us/defender-office-365/message-trace-defender-portal) to verify the message was delivered to the Inbox.
3. Check the message headers to confirm the spam verdict is no longer applied \(for example, `SFV:NSPM` or `CAT:NONE`\).

Tip

Allow 15-30 minutes for policy changes to take effect. Mail flow rule changes might take up to one hour due to caching.

### Common spam false positive scenarios

The following table describes common scenarios and recommended approaches:

| Scenario | Key indicators | Recommended approach |
| --- | --- | --- |
| Legitimate bulk newsletter or marketing email consistently quarantined | High BCL \(7-9\), `CAT:BULK` | Increase the [Bulk Complaint Level \(BCL\) threshold](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure) \(the default value is 7\). |
| Legitimate newsletter or marketing email identified as spam or high confidence spam | `CAT:SPM` or `CAT:HSPM` | [Submit the messages to Microsoft for analysis](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-email-to-microsoft) and create an allow entry for the sender during the submission. |
| All email from a specific partner domain is blocked | Sender found in the Tenant Allow/Block List \(check the [email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page) or the Tenant Allow/Block List directly\) | Remove the block entry or [create an allow entry for the domain](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-allow-entries-for-domains-and-email-addresses). |
| Marketing automation platform email blocked \(Marketo, HubSpot, Mailchimp, etc.\) | High BCL, possible email authentication failures | Verify the sender's SPF/DKIM/DMARC configuration. If authentication passes but filtering still triggers, increase the BCL threshold or add the sending domain to the allow list. |
| Forwarded emails quarantined as spoofing | DMARC failure, spoof detection triggered | Configure [ARC trusted sealers](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-arc-configure) for the forwarding service, or add a [spoof intelligence override](https://learn.microsoft.com/en-us/defender-office-365/anti-spoofing-spoof-intelligence) for the sender/infrastructure pair. |

### Troubleshoot fixes that aren't working

If the selected remediation doesn't resolve the false-positive spam classification, check for the following common causes:

- **Propagation delay**: Allow 15-30 minutes for anti-spam policy changes and up to one hour for mail flow rule changes.
- **Policy precedence conflict**: A higher-priority policy \(preset security policy\) might override your custom policy settings. For details, see [Troubleshoot anti-spam policy issues](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-troubleshooting).
- **Multiple detection reasons**: The message triggered more than one detection \(for example, spam *and* spoof detection\). Resolving one cause might not be enough.
- **Allow entry expired or incorrect**: Verify the [Tenant Allow/Block List entry](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure) is active, not expired, and uses the correct format \(email address vs. domain\).
- **Mail flow rule action**: Mail flow rules can request that messages [bypass spam filtering](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl). Spam filtering considers the request with other signals when it determines how to handle the message. Mail flow rules can also delete messages.

## Handle phishing and malware false positives

Use the phishing, malware, and non-spam false-positive remediation steps in this section when legitimate email is incorrectly detected as phishing, malware, or another non-spam threat.

### Legitimate emails delivered to the Junk Email folder

Follow the end-user and admin remediation steps in this subsection when messages are delivered but land in the wrong folder.

#### End user actions

End users can try the following actions to correct messages that were delivered to Junk Email:

1. Report the email as **Not junk** by using the [built-in **Report** button in supported versions of Outlook](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages#use-the-built-in-report-button-in-outlook).
2. Optionally, add the sender to the [Safe Senders list](https://support.microsoft.com/office/add-recipients-to-the-safe-senders-list-in-outlook-be1baea0-beab-4a30-b968-9004332336ce) in Outlook to prevent future messages from that sender from going to Junk Email.

#### Actions admins can take for legitimate emails in Junk Email

Admins can use the following process to investigate and remediate these reports:

1. Triage user-reported messages from [the User reported tab on the Submissions page](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#view-user-reported-messages-to-microsoft).

   Tip

   In organizations with Defender for Office 365 Plan 2 and Security Copilot, the [Phishing Triage Agent](https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent) can autonomously triage and classify user-reported phishing emails, reducing manual investigation work for security teams.
2. [Submit the messages to Microsoft for analysis](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#notify-users-about-admin-submitted-messages-to-microsoft) to understand why the email was blocked.
3. If needed, while submitting to Microsoft for analysis, [create an allow entry for the sender](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-allow-entries-for-domains-and-email-addresses) to mitigate the false positive.
4. After the submission results are available, read the verdict on the **Submissions** page to understand why the emails were blocked.
5. Use the results to improve your organization's configuration and *prevent* similar false positives in the future.

### Legitimate emails in quarantine \(end user view\)

End users can take the following actions on quarantined messages:

1. Review [quarantine notifications](https://learn.microsoft.com/en-us/defender-office-365/quarantine-quarantine-notifications) about quarantined messages. The notifications are based on the settings that security admins configure.
2. Preview, release, or report quarantined messages by using the steps in [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user).

### Legitimate emails in quarantine \(admin view\)

Admins can release quarantined messages and submit them to Microsoft for analysis:

1. View quarantined emails \(including messages where users requested release\) from the [admin quarantine review page for messages and files](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files).
2. [Release messages from quarantine while submitting them to Microsoft for analysis](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files#release-quarantined-email). You can also create a temporary allow entry in the Tenant Allow/Block List during the submission to mitigate the issue.
3. After submission results are available, [read the Microsoft submission verdict results](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#results-from-microsoft) to understand why the message was detected as phishing, malware, or spoofing.

   - If false positives are due to your organization's mail-flow, anti-spam, or spoof-protection configuration, correct those settings to mitigate the false positive.
   - If false positives are due to other factors, Microsoft learns from the submission and similar messages aren't quarantined anymore.

Note

Admins need to manually release any similar quarantined messages. Quarantined messages aren't released automatically. To find and release quarantined messages in bulk, see [Can I release or report more than one quarantined message at a time?](https://learn.microsoft.com/en-us/defender-office-365/quarantine-faq#can-i-release-or-report-more-than-one-quarantined-message-at-a-time-).

### Forwarded or spoofed emails incorrectly blocked

Externally forwarded emails or legitimate cross-domain senders can trigger spoof detection because the sending infrastructure doesn't match the From address domain. If you see forwarded or non-Microsoft emails blocked as spoofing:

- Review the [spoof intelligence insight and configure overrides](https://learn.microsoft.com/en-us/defender-office-365/anti-spoofing-spoof-intelligence) for legitimate sender/infrastructure pairs.
- If your organization receives mail through an intermediary \(mailing list, forwarding service, or email gateway\), configure Authenticated Received Chain \(ARC\) [trusted sealers](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-arc-configure) so messages preserve authentication through the relay.
- Ask the external sender to fix their SPF, DKIM, and DMARC records to align with their sending infrastructure.

## Related content

- [Anti-spam protection in EOP](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-protection-about)
- [Troubleshoot common anti-spam policy issues](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-troubleshooting)
- [Manage quarantined messages and files as an admin](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files)
- [Report messages and files to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin)
- [Manage the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure)
