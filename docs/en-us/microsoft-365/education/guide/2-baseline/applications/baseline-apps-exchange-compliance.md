<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-compliance -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Configure security and compliance in Microsoft Exchange Online for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-applications.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

This article describes best practices in Exchange Online for security and compliance in education.

## Sender Policy Framework

Sender Policy Framework \(SPF\) is a method of email authentication that helps validate mail sent from your Microsoft 365 organization to prevent spoofed senders. SPF uses a TXT record in DNS to identify valid sources of mail. For the "onmicrosoft.com" domain, Microsoft has already configured this framework.

The SPF record for a custom domain, "contoso.com" for example, using an Exchange Online only setup \(not hybrid\), the SPF record is: v=spf1 include:spf.protection.outlook.com –all

[Set up SPF to identify valid email sources for your Microsoft 365 domain](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure).

## DomainKeys Identified Mail

DomainKeys Identified Mail \(DKIM\) allows digital signatures to be added to email messages in the message header. Like SPF, DKIM relies on DNS records. DKIM should be enabled for all domains.

[Set up DKIM to sign mail from your Microsoft 365 domain](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dkim-configure).

## Domain-based Message Authentication

Domain-based Message Authentication \(DMARC\) authenticates senders and ensures destination email systems can validate your messages. DMARC should be published for all second-level domains. DMARC defines the behavior when SPF and DKIM fail, and should be set to fail \(p=reject\). DMARC is also configured via DNS records.

[Set up DMARC to validate the From address domain for senders in Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure).

## Simple Mail Transfer Protocol authentication

Simple Mail Transfer Protocol \(SMTP\) authentication is sometimes used by applications outside of Outlook that send email messages, since those applications might not be able to use MFA. It's recommended to disable SMTP authentication if possible.

[Enable or disable authenticated client SMTP submission \(SMTP AUTH\) in Exchange Online](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

## Contact and calendar sharing

Contact folders shouldn't be shared with all domains.

Calendar details shouldn't be shared with all domains.

In EAC, navigate to Organization / Sharing / Individual Sharing. For all policies, select **Manage domains** and for all Sharing rules, ensure **Sharing with all domains** isn't selected.

## External sender warnings

It's recommended that all incoming external messages be easily identified as such by prepending the subject line with \[EXTERNAL\] and / or a header in the message body. The alerts recipients that the email message they're receiving is from an external entity and should heighten their awareness for phishing attempts.

There are two options for flagging emails from external senders, making them instantly recognizable. First is a mailflow rule that prepends the subject field with \[EXTERNAL\] for example.

## Data Loss Prevention

Do configure data loss prevention \(DLP\) policies in Purview for Exchange Online. These policies ensure that information sensitive to an organization isn't exfiltrated via email. For example, a policy that blocks sending personal identifiable information \(PII\) via email is recommended, and could be a requirement of your organization.

[Data Loss Prevention conditions and actions for Exchange Online](https://learn.microsoft.com/en-us/purview/dlp-exchange-conditions-and-actions).

## Attachment file types

Do use Common Attachment Filters in Defender to filter emails based on attachment file type, for example exe, cmd, ps1, ve, and other click-to-run program type files.

## Malware scanning

Do use Microsoft Defender to scan for malware. Identified malware should be dropped, not quarantined.

## Phishing protection

Do define policies including zero-hour auto purge \(ZAP\), phishing protection, and impersonation protection in Defender for Office 365 \(MDO\) and Exchange Online Protection \(EOP\).

## IP allowlists

Although Microsoft Defender supports creating IP allowlists and safelists for email senders, these lists shouldn't be used since they bypass SPF, DKIM, and DMARC protections.

## Mailbox auditing and audit logging

The default audit policy logs certain administrator actions and shouldn't be disabled.

Also user activity from Microsoft 365 services is logged and should be enabled to allow for incident response and threat detection.

## Inbound anti-spam protection

Spam filters within Microsoft Defender should be enabled, moved to junk email folder, or quarantined. However allowed domains shouldn't be added to inbound anti-spam protection policies.

## Link protection

Protection against malicious links in emails protection is provided URL comparison with a blocklist. Also, direct download links should be scanned for malware, and user click tracking on malicious links should be enabled.

## Next steps

Now that you completed the Exchange Online compliance section, you're ready to go to the last section in Exchange Online for shared mailboxes, address books, and clients.

[Next: Configure shared mailboxes, address books, and clients >](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-asmabc)
