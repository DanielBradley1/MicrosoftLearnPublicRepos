<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/create-block-sender-lists-in-office-365 -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# Create sender blocklists for cloud mailboxes

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

All Microsoft 365 organizations with cloud mailboxes offer multiple ways of blocking inbound email from unwanted senders. Collectively, you can think of these options as *blocklists*.

The following list contains the available methods to block senders from most recommended to least recommended:

1. Block entries for domains and email addresses \(including spoofed senders\) in the Tenant Allow/Block List.
2. Outlook Blocked Senders \(the Blocked Senders list in each mailbox that affects only that mailbox\).
3. Blocked sender lists or blocked domain lists in anti-spam policies.
4. Exchange mail flow rules \(transport rules\).
5. The IP Block List in the default connection filter policy.

The following sections describe each method in more detail.

Tip

Always submit messages in your blocklists to Microsoft for analysis. For instructions, see [Report questionable email to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-questionable-email-to-microsoft). If the messages or message sources are determined to be harmful, Microsoft can automatically block the messages, and you don't need to manually maintain entries in your own blocklists.

Instead of blocking email, you also have several options to allow email from specific sources using *safe sender lists*. For more information, see [Create sender allowlists](https://learn.microsoft.com/en-us/defender-office-365/create-safe-sender-lists-in-office-365).

A standard SMTP email message can contain different sender email addresses as described in [Why internet email needs authentication](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about#why-internet-email-needs-authentication). Frequently, the MAIL FROM address \(also known as the `5321.MailFrom` address, P1 sender, or envelope sender\) and From address \(also known as the `5322.From` address or P2 sender\) are the same. However, when email is sent on behalf of someone else, the addresses can be different. Blocked sender lists and blocked domain lists in anti-spam policies inspect the From address only. This behavior is similar to Outlook Blocked Senders that use the From address.

## Use block entries in the Tenant Allow/Block List

Our number one recommended option for blocking mail from specific senders or domains is the Tenant Allow/Block List. For instructions, see [Create block entries for domains and email addresses](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-block-entries-for-domains-and-email-addresses) and [Create block entries for spoofed senders](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-block-entries-for-spoofed-senders).

Email messages from senders or domains that you block by using Tenant Allow/Block List entries are marked as **High confidence spam**. The [anti-spam policy](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure) that detected the message for the recipient determines what happens to the messages. In the [Standard and Strict preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies), high confidence spam messages are quarantined.

As an added benefit, users in the organization can't *send* email to these blocked domains and addresses. The message is returned in the following non-delivery report \(also known as an NDR or bounce message\): `550 5.7.703 Your message can't be delivered because messages to XXX, YYY are blocked by your organization using Tenant Allow Block List.` The entire message is blocked for all internal and external recipients of the message, even if only one recipient email address or domain is defined in a block entry.

Only consider different block methods if you can't use block entries in the Tenant Allow/Block List for some reason.

## Use Outlook Blocked Senders

When only a few users received unwanted email, users or admins can add the sender email addresses to the Blocked Senders list in the mailbox. Blocked Senders entries affect that mailbox only. For instructions, see the following articles:

- **Users**: [Block or unblock senders in Outlook](https://support.microsoft.com/office/9bf812d4-6995-4d19-901a-76d6e26939b0).
- **Admins**: [Configure junk email settings on cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/configure-junk-email-settings-on-exo-mailboxes).

When messages are successfully blocked due to a user's Blocked Senders list, the **X-Forefront-Antispam-Report** header field contains the value `SFV:BLK`.

Tip

If the unwanted messages are newsletters from a reputable and recognizable source, unsubscribing from the email is another option to stop the user from receiving the messages.

## Use blocked sender lists or blocked domain lists in anti-spam policies

When multiple users are affected, the scope is wider, so the next best option is blocked sender lists or blocked domain lists in custom anti-spam policies or the default anti-spam policy. Messages from senders on the lists are marked as **High confidence spam**, and the action that you configured for the **High Confidence Spam** filter verdict is taken on the messages. For more information, see [Configure anti-spam policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure).

The maximum limit for blocked sender lists and blocked domain lists in anti-spam policies is approximately 1,000 entries.

## Use mail flow rules

Mail flow rules can also look for keywords or other properties in the unwanted messages. For more information about mail flow rules, see [Mail flow rules in Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

Important

It's easy to create rules that block too many messages or that don't block enough messages. Use specific criteria that identify *only* the messages you want to block. Also, be sure to [monitor the usage of the rule](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#monitor-rule-usage) to ensure everything works as expected.

## Use the IP Block List in the default connection filter policy

When it's not possible to use one of the other options to block a sender, *only then* should you use the IP Block List in the default connection filter policy. For more information, see [Configure connection filtering](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure). It's important to keep the number of blocked IPs to a minimum, so we don't recommend blocking entire IP address ranges.

You should *especially* avoid adding IP address ranges that belong to consumer services \(for example, outlook.com\) or shared infrastructures. You also need to review the list of blocked IP addresses as part of regular maintenance.

Tip

The IP Block List accepts Classless Inter-Domain Routing \(CIDR\) IP address ranges from /24 through /32.
