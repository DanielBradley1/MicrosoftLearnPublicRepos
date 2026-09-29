<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-protection-about -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Outbound spam protection for cloud mailboxes

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In all organizations with cloud mailboxes, we take managing outbound spam seriously. Even if one customer intentionally or unintentionally sends spam from their organization, that action can degrade the reputation of the whole service and can affect email delivery for other customers.

This article describes the controls and notifications that are designed to help prevent outbound spam, and what you can do if you need to send mass mailings.

Tip

If you're an end-user and your email is blocked or fails to send due to outbound spam protection, you receive a non-delivery report \(also known as an NDR or bounce message\). This behavior is expected. Only admins can review and resolve these issues, so contact your email admin for assistance.

## What admins can do to control outbound spam

Note

If messages are blocked or marked as spam, admins can review the issue in the **Exchange admin center \(EAC\)** using **Message trace** or delivery reports. For investigation and resolution guidance, see [Troubleshoot outbound email issues in Exchange Online](https://learn.microsoft.com/en-us/troubleshoot/exchange/email-delivery/ndr/non-delivery-reports-in-exchange-online)

- **Use built-in notifications**: When a user exceeds [sending limits of the service](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) or [outbound spam policies](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-policies-configure) and is restricted from sending email, the default alert policy named **User restricted from sending email** sends email notifications to members of the **TenantAdmins** group \(**Global Administrator** members\). To configure who else receives these notifications, see [Verify the alert settings for restricted users](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-restore-restricted-users#verify-the-alert-settings-for-restricted-users). Also, the default alert policies named **Email sending limit exceeded** and **Suspicious email sending patterns detected** send email notifications to members of the **TenantAdmins** group \(**Global Administrator** members\). For more information about alert policies, see [Alert policies in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/alert-policies-defender-portal).
- **Review spam complaints from non-Microsoft email providers**: Many email services like Outlook.com, Yahoo, and AOL provide a feedback loop where we review our messages that are identified as spam by their users. To learn more about sender support for Outlook.com, go to the [Microsoft Sender Support and Blocklist Removal Tool](https://sendersupport.olc.protection.outlook.com/pm/services.aspx).

## How Microsoft 365 controls outbound spam

- **Segregation of outbound email traffic**: Every outbound message sent through the service is scanned for spam. Messages determined to be spam are delivered from a secondary, less reputable IP address pool named the *high-risk delivery pool*. For more information, see [High-risk delivery pool for outbound messages](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-high-risk-delivery-pool-about).
- **Monitoring our source IP address reputation**: Microsoft 365 queries various non-Microsoft IP blocklists. An alert is generated if any of the IP addresses that we use for outbound email appear on these lists. This monitoring allows us to react quickly when spam causes our reputation to degrade. When an alert is generated, we have internal documentation that outlines how to get our IP addresses remove \(delisted\) from blocklists.
- **Disable accounts that send too much spam**<sup>\*</sup>: Even though we segregate outbound spam into the high-risk delivery pool, we can't allow an account \(often, a compromised account\) to send spam indefinitely. We monitor accounts that are sending spam, and when they exceed an undisclosed limit, the account is blocked from sending email. There are different thresholds for individual users and the entire organization.
- **Disabling accounts that send too much email too quickly**<sup>\*</sup>: In addition to the limits that look for messages marked as spam, there are also limits that block accounts when they reach an overall outbound message limit, regardless the spam filtering verdict on the outbound messages. A compromised account could send zero-day \(previously unrecognized\) spam missed by the spam filter. Because it can be difficult to identify a legitimate mass mailing campaign vs. a spam campaign, these limits help to minimize any potential damage.

<sup>\*</sup> We don't advertise the exact limits so spammers can't game the system, and so we can increase or decrease the limits as necessary. The limits are high enough to prevent an average business user from ever exceeding them, and low enough to help contain the damage caused by a spammer.

## Recommendations for customers who want to send mass mailings through Microsoft 365

It's difficult to strike a balance between customers who want to send a large volume of email vs. protecting the service from compromised accounts and bulk email senders with poor recipient acquisition practices. It's better for us to block a user who's sending too much email than allow bulk activity that results in Microsoft 365 email servers landing on a non-Microsoft IP blocklist. The associated cost and risk to the service are too great.

As described in the [Exchange Online Service Description](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits), using Microsoft 365 to send bulk email isn't a supported use of the service, and is permitted only on a "best-effort" basis. For customers who want to send bulk email using Microsoft 365, we have the following recommendations:

- Don't send a large rate or volume of email that causes you to run afoul of the [sending limits](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1) in the service. This recommendation also includes not sending email to a large list of Bcc recipients.
- Avoid using addresses in your primary email domain \(for example, contoso.com\) as senders for bulk email. Doing so can affect the delivery of regular email from senders in the domain. Consider using a custom subdomain exclusively for bulk email. For example, use `m.contoso.com` for marketing email and `t.contoso.com` for transactional email.
- Configure any custom subdomains with email authentication records in DNS \([SPF](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure), [DKIM](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dkim-configure), and [DMARC](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure)\). Many email service providers \(for example, Gmail, Yahoo!, and Outlook.com\) are configured to reject messages that don't meet email authentication standards.
- Marketing email \(especially newsletters\) should always include a way to unsubscribe from future messages. Some senders require recipients to send an email to a specified alias with the value "Unsubscribe" in the Subject line. However, a one-click option to unsubscribe is preferable for a smoother process.
- Eliminate incorrect and non-existent email aliases from your databases. Any email alias rejected in a bounce message is unnecessary and poses a risk to your outbound email, potentially triggering increased scrutiny from email filtering services. To maintain email deliverability and reputation, keep your email database current and devoid of redundant or useless email addresses.

Use the following resources outside of Microsoft 365 to send bulk email:

- **Send bulk email through on-premises email servers**: Customers maintain their own email infrastructure for mass mailings.
- **Use a non-Microsoft bulk email provider**: There are several non-Microsoft bulk email solution providers that you can use to send mass mailings. These companies have a vested interest in working with customers to ensure good email sending practices.

  The Messaging, Mobile, Malware Anti-Abuse Working Group \(MAAWG\) publishes its membership roster at [MAAWG Member Organizations List](https://www.maawg.org/about/roster). Several bulk email providers are on the list, and are known to be responsible internet citizens.

## Related content

- [How outbound spam policy limits apply to Send As and Send on behalf permissions](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-policies-send-as-send-on-behalf)
- [Troubleshoot outbound sending limits in Exchange Online](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-sending-limits-troubleshoot)
- [Troubleshoot email delivery issues with error codes \(NDR\)](https://learn.microsoft.com/en-us/troubleshoot/exchange/email-delivery/ndr/fix-error-code-550-4-4-7-in-exchange-online)
- [External sender delivery troubleshooting](https://learn.microsoft.com/en-us/defender-office-365/external-senders-mail-flow-troubleshooting)
- [Common non-delivery report \(NDR\) codes explanation](https://learn.microsoft.com/en-us/troubleshoot/exchange/email-delivery/ndr/non-delivery-reports-in-exchange-online)
