<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/anti-spam-spam-confidence-level-scl-about -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# Spam confidence level \(SCL\) in Microsoft 365

Historically, the spam confidence level \(SCL\) helped indicate whether spam filtering considered a message good or bad, or whether filtering was skipped on the message. Spam filtering stamps the SCL value \(-1, or 0 to 9\) on messages in the `X-Forefront-Antispam-Report` header. An SCL value of 5 or higher generally indicates the message is considered bad.

As the filtering stack evolved, particularly with the expansion into message categorization, the SCL value no longer holds the same meaning in cloud organizations. The value *doesn't* determine whether spam filtering identifies a message as **Spam** or **High confidence spam**, and it *doesn't* determine the action taken on the message. Spam filtering makes those decisions using categorization and other signals, so the same SCL value can appear on messages with different verdicts.

To understand how a message was handled, use other values in the message header. For example, `CAT` \(category\) identifies what filtered the message, and `DIR` \(directionality\) indicates whether the message was internal. For more information, see [Anti-spam message headers](https://learn.microsoft.com/en-us/defender-office-365/message-headers-eop-mdo). For the actions that anti-spam policies take for each verdict, see [Actions in anti-spam policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-protection-about#actions-in-anti-spam-policies).

In the cloud, the primary use of SCL is mail flow rules \(also known as transport rules\) to [request a bypass from most spam filtering](https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) \(SCL -1\), treat messages as spam \(SCL 5 or 6\), or treat messages as high confidence spam \(SCL 9\) based on specific criteria. But even when a rule requests a bypass, the actual SCL value stamped on the message might not be -1 \(for example, 0 or 1 to indicate it was evaluated and found not to be spam\).

The main purpose of the SCL value is to support *on-premises* Exchange servers, including hybrid environments where cloud-filtered messages are delivered to on-premises mailboxes. In on-premises Exchange, the SCL value is meaningful for the following anti-spam features:

- Delete, reject, and quarantine thresholds in the Content Filter agent on individual servers.
- The Junk Email threshold for the organization.
- The Junk Email threshold on individual mailboxes.
- SCL -1 handling in the Content Filter agent \(the message is ignored\).

For more information, see [Exchange spam confidence level \(SCL\) thresholds](https://learn.microsoft.com/en-us/exchange/antispam-and-antimalware/antispam-protection/scl).

For troubleshooting information about spam filtering overrides, see [Spam verdict override behavior](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-troubleshooting#spam-verdict-override-behavior). To identify which component filtered a specific message, see [Determine which component filtered the message](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-troubleshooting#determine-which-component-filtered-the-message).

The bulk complaint level \(BCL\) identifies bad bulk email \(also known as *gray mail*\). A higher BCL value indicates the message is more likely to exhibit undesirable spam-like behavior. You configure the BCL threshold in anti-spam policies. For more information, see the following articles:

- [Configure anti-spam policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure)
- [Bulk complaint level \(BCL\)](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-bulk-complaint-level-bcl-about)
- [What's the difference between junk email and bulk email?](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-spam-vs-bulk-about)

---

![The short icon for LinkedIn Learning.](https://learn.microsoft.com/en-us/defender-office-365/media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **New to Microsoft 365?** Discover free video courses for **Microsoft 365 admins and IT pros**, brought to you by LinkedIn Learning.
