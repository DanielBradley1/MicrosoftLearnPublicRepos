<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-protection-spoofing-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions - Anti-spoofing protection

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

**Applies to**

- [Built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about)
- [Microsoft Defender for Office 365 Plan 1 and Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)
- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

This article provides frequently asked questions and answers about anti-spoofing protection for all organizations with cloud mailboxes.

For questions and answers about anti-spam protection, see [Frequently asked questions: Anti-spam protection](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-protection-faq).

For questions and answers about anti-malware protection, see [Frequently asked questions: Anti-malware protection](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-protection-faq)

## Why did Microsoft choose to junk unauthenticated inbound email?

Microsoft believes that the risk of continuing to allow unauthenticated inbound email is higher than the risk of losing legitimate inbound email.

## Does junking unauthenticated inbound email cause legitimate email to be marked as spam?

When Microsoft enabled this feature in 2018, some false positives happened \(good messages were marked as bad\). Over time, senders adjusted to the requirements. The number of messages that were misidentified as spoofed became negligible for most email paths.

Microsoft itself first adopted the new email authentication requirements several weeks before deploying it to customers. While there was disruption at first, it gradually declined.

## Is spoof intelligence available to Microsoft 365 customers without Defender for Office 365?

Yes. As of October 2018, spoof intelligence is available to all organizations with cloud mailboxes.

## How can I report spam or non-spam messages back to Microsoft?

See [Report messages and files to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-report-messages-files-to-microsoft).

## What happens if I disable anti-spoofing protection for my organization?

We don't recommend disabling anti-spoofing protection. Disabling the protection allows more delivered phishing and spam messages in your organization. Not all phishing is spoofing, and not all spoofed messages will be missed. However, your risk is higher.

Now that [Enhanced Filtering for Connectors](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) is available, we no longer recommended turning off anti-spoofing protection when your email is routed through a non-Microsoft service before arriving at Microsoft 365.

## Does anti-spoofing protection mean I'm protected from all phishing?

Unfortunately, no. Attackers constantly adapt to use other techniques \(for example, compromised accounts or accounts in free email services\). However, anti-phishing protection works better to detect these other types of phishing methods. The protection layers in Microsoft 365 are designed work together and build on top of each other.

## Do other large email services block unauthenticated inbound email?

Nearly all large email services implement traditional SPF, DKIM, and DMARC checks. Some services have other, more strict checks, but few go as far as Microsoft 365 to block unauthenticated email and treat them as spoofed messages. However, the industry is becoming more aware about issues with unauthenticated email, particularly because of the problem of phishing.

## Do I still need to enable the Advanced Spam Filter setting "SPF record: hard fail" \('MarkAsSpamSpfRecordHardFail'\) if I enable anti-spoofing?

No. This ASF setting is no longer required. Anti-spoofing protection considers both SPF hard fails and a wider set of criteria. If you have anti-spoofing enabled and the **SPF record: hard fail** \(*MarkAsSpamSpfRecordHardFail*\) turned on, you'll probably get more false positives.

We recommend that you disable this feature as it provides almost no additional benefit for detecting spam or phishing messages, and would instead generate mostly false positives. For more information, see [Advanced Spam Filter \(ASF\) settings in anti-spam policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-asf-settings-about).

## Does Sender Rewriting Scheme help fix forwarded email?

SRS only partially fixes the problem of forwarded email. By rewriting the SMTP **MAIL FROM** value, SRS can ensure that the forwarded message passes SPF at the next destination. However, because anti-spoofing is based on the **From** address in combination with the **MAIL FROM** or DKIM-signing domain \(or other signals\), it's not enough to prevent SRS forwarded email from being marked as spoofed.
