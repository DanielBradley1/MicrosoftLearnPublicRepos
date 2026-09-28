<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/email/select-domain-to-use-for-email-from-microsoft-365-products?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Select the domain to use for email from Microsoft 365 products

As users interact with each other across Microsoft 365 products, the service sends emails to keep them informed about activity in their organization. Because direct user-to-user interactions trigger most of these messages, they're sent from the originating user's email address and behave like any other user sent email. Those emails remain unchanged and continue to work as they do today.

## No-reply system emails

Microsoft 365 emails that aren't tied to a specific user interaction or actions are sent from system-based product accounts. Examples of these types of emails include items such as batched comment notifications, Teams missed activities, news digests, activity digests, processing updates and scheduled items. By default, these messages are sent from Microsoft no-reply product addresses, such as `no-reply@sharepointonline.com`, `no-reply@glint.mail.microsoft`, and `no-reply@teams.mail.microsoft`.

Because they're sent from Microsoft-owned system addresses, recipients see them marked as **\[External\]** notifications in Outlook. The **Send email notifications from your domain** setting allows you to configure Microsoft 365 to send these system notifications from a domain you own instead of the default Microsoft no-reply addresses. For example, if you select contoso.com as your sending domain, a notification that would normally be sent from `no-reply@sharepointonline.com` is instead sent from `no-reply@contoso.com`.

When this option is enabled:

- The sender address uses your verified custom domain that you selected.
- Emails are sent through your Exchange Online instance within Microsoft 365. They're considered internal communications and your Exchange Online Administrator can track them.

Note

Only domains registered within your tenant can be used. Domain ownership must be verified through the existing add domains process within Microsoft 365. Use the following steps and note the Domain Name System \(DNS\) records required when configuring a domain for sending email.

## Configure the "Send email notifications from your domain" setting

The setting is available via the Microsoft 365 Admin Center **Settings** menu item. Select **Settings**, select **Org settings**, and then select the **Organization profile** tab as illustrated.

[![Screenshot of the Org Settings - Send email notifications setting.](https://learn.microsoft.com/en-us/microsoft-365/media/send-email-notifications-org-settings.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/send-email-notifications-org-settings.png?view=o365-worldwide#lightbox)

Note

- This setting is an opt-in setting that allows the Microsoft 365 system administrators to select a verified domain within the tenant. The verified domain is validated for ownership.
- The setting can take up to 24 hours to take effect.
- The recommendation is to use a domain that has the appropriate DNS records to facilitate email validation. For example, SPF, DKIM, DMARC, and MX records. Email validation complies with the [RFC compliance](https://www.ietf.org/rfc/rfc2142.txt) for sending and receiving email. For more information, see [Learn more about Exchange Online Email Routing](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/mail-flow-best-practices).
- Ensure you comply with all privacy, compliance, and security requirements and policies within your organization.

**To configure the "Send email notifications from your domain" setting:**

1. In the Microsoft 365 admin center, in the navigation pane select **Settings**.
2. Select **Org settings**.
3. On the **Org settings** page, select **Organization profile**.
4. On the **Organization profile** page, select **Send email notifications from your domain**.
5. In the **Send email notifications from your domain** page, select **Use a custom send-from domain address**.
6. The **Domains** menu, select the domain that you want to use for your email replies. The domains listed in the menu includes verified complete and incomplete domains as Microsoft 365 allows DNS settings to be configured and managed outside of the tenant. Your System or Exchange administrator must ensure that they follow and meet all DNS and domain requirements.
7. For **Custom username**, administrators can optionally configure the no-reply prefix. They could then create a matching email address in Exchange, if they would like to monitor responses from users.
8. Select **Save**. Changes take a few minutes to complete.

   ![Screenshot of the Send email notifications setting.](https://learn.microsoft.com/en-us/microsoft-365/media/save-email-notifications-domain.png?view=o365-worldwide)

Note

If you make a mistake or would like to roll back the change, deselect the **Use a custom send-from domain address** checkbox and then select **Save**. The setting reverts to the original configuration.

## Supported products

The following products currently support this feature:

- Microsoft 365 Admin Center
- Microsoft Copilot
- Microsoft 365 eSignature
- Microsoft Defender
- Microsoft Forms
- Microsoft Search Insights
- Microsoft Teams
- Microsoft Viva Connections
- Microsoft Viva Glint
- Microsoft Viva Pulse
- Microsoft Viva Topics
- Microsoft Viva Amplify
- Office
- OneDrive for work or school
- Power BI
- Microsoft Project
- SharePoint in Microsoft 365

Note

The supported products list will be updated as each product migrates to support the setting. No additional action is required as these products onboard to the centralized setting.

## Excluded Scenarios

One Time Passcodes \(OTP\) generated from sharing within OneDrive and SharePoint in Microsoft 365 continues to use `no-reply@notify.microsoft.com`. These emails are secure emails generated by Microsoft and utilize this trusted sender address to ensure delivery of these emails.
