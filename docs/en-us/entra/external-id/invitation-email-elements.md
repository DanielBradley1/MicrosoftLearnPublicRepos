<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# B2B invitation email layout and language settings

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Invitation emails are key to welcoming partners as Microsoft Entra B2B collaboration users. Although [not mandatory](https://learn.microsoft.com/en-us/entra/external-id/redemption-experience#redemption-process-through-a-direct-link), these emails give essential information to help recipients decide whether to accept your invitation. They include a link for quick access to your resources later.

![Screenshot of the B2B invitation email.](https://learn.microsoft.com/en-us/entra/external-id/media/invitation-email-elements/invitation-email.png)

## Explaining the email

Let's review a few elements of the email so you understand how to use their capabilities. These elements might appear slightly different in some email clients.

### Subject

The subject line of the email follows this pattern: `username` invited you to collaborate with `primary domain`. For example, if Megan Bowen invites you from the domain Contoso, the subject is: “Megan Bowen invited you to collaborate with Contoso”.

### From address

The From address follows this pattern: Microsoft Invitations on behalf of `primary domain` `<invites@<primary domain>.onmicrosoft.com>`. For example, if Megan Bowen invites you from Contoso, the From address is: "Microsoft Invitations on behalf of Contoso [invites@Contoso.onmicrosoft.com](mailto:invites@Contoso.onmicrosoft.com)."

Before December 2025, invitations originate from Microsoft Invitations invites@microsoft.

Note

For the Azure service operated by [21Vianet in China](https://learn.microsoft.com/en-us/azure/china/), the sender address is `<primary domain>.partner.onmschina.cn`.  
For [Microsoft Entra ID for government](https://learn.microsoft.com/en-us/azure/azure-government/), the sender address is `<primary domain>.onmicrosoft.us`.

### Reply To

The reply-to email is set to the inviter's email when available, so that replying to the email sends an email back to the inviter.

### Phishing warning

The email starts with a brief phishing warning, advising users to accept only expected invitations. It's good practice to let partners know in advance to expect your invitation.

![Screenshot of the phishing warning in the email.](https://learn.microsoft.com/en-us/entra/external-id/media/invitation-email-elements/phishing-warning.png)

### Inviter's information and invitation message

The email includes the name and primary domain associated with the organization sending the invitation. This information should help the invitee make an informed decision about accepting the invitation. The inviter can include a message as part of their invitation to the [directory, group, or app](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator), or when they [use the invitation API](https://learn.microsoft.com/en-us/entra/external-id/customize-invitation-api). The message is highlighted in the main section of the email. The inviter's name and profile image are included if available. The message itself is a text area, so for security reasons, it doesn't process HTML tags.

![Screenshot of the invitation message in the email.](https://learn.microsoft.com/en-us/entra/external-id/media/invitation-email-elements/invitation-message-inviters-info.png)

### Accept invitation button or link and redirect URL

The next section of the email shows where the invitee is redirected after accepting the invitation, along with a button or link to proceed. In the future, the invitee can always use this link to return to your resources directly.

![Screenshot of the accept button and redirect URL in the email.](https://learn.microsoft.com/en-us/entra/external-id/media/invitation-email-elements/accept-button.png)

### Footer section

The footer provides additional details about the invitation. If the organization [configured a privacy statement](https://learn.microsoft.com/en-us/entra/fundamentals/properties-area), the link to the statement is displayed here. Otherwise, a note indicates the organization's privacy statement isn't available.

![Screenshot showing the footer section in the email.](https://learn.microsoft.com/en-us/entra/external-id/media/invitation-email-elements/footer-section.png)

## How the language is determined

The following settings determine the language presented to the guest user in the invitation email. The settings are listed in order of precedence. If you don't configure a setting, the next one in the list determines the language.

- The **messageLanguage** property of the [invitedUserMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/invitedusermessageinfo) object of the [Create invitation API](https://learn.microsoft.com/en-us/graph/api/invitation-post)
- The **preferredLanguage** property specified in the guest's [user object](https://learn.microsoft.com/en-us/graph/api/resources/user)
- The **Notification language** set in the properties of the guest user's home tenant \(for Microsoft Entra tenants only\)
- The **Notification language** set in the properties of the resource tenant

If you don't configure any of these settings, the language defaults to English \(US\).

## Custom domain email requirements

When invitation emails are sent from your organization's custom domain \(rather than the default MOERA domain\), the following requirements must be met for successful delivery.

### Mail-enabled tenant

Your tenant must be mail-enabled with an Exchange Online \(EXO\) license. Without this, invitation emails can't be sent from a custom domain.

### Avoid MOERA \(Microsoft Online Email Routing Address\) domains

MOERA domains \(`.onmicrosoft.com`\) are **strongly discouraged** for sending invitation emails because:

- MOERA domains are subject to [throttling limits](https://techcommunity.microsoft.com/blog/exchange/limiting-onmicrosoft-domain-usage-for-sending-emails/4292065).
- Emails sent from MOERA domains have a high likelihood of being filtered as spam.

To avoid these issues, [set a verified custom domain as the default domain for your tenant](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/add-domain).

### DNS configuration \(SPF, DKIM, DMARC\)

Email authentication records must be configured in DNS based on how your organization routes outbound email. Owning and verifying a custom domain in Microsoft Entra ID alone isn't sufficient — DNS records must also be in place.

- **Outbound mail goes directly through Exchange Online** — Configure SPF, DKIM, and DMARC based on Microsoft 365 settings:

  - [Add DNS records to connect your domain](https://learn.microsoft.com/en-us/microsoft-365/admin/get-started/add-domain)
  - [Set up SPF, DKIM, and DMARC](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about)

- **Outbound mail routes through a third-party gateway** \(for example, Proofpoint or Mimecast\) — Configure SPF, DKIM, and DMARC based on your third-party provider's requirements, not Microsoft 365. Your SPF record should authorize your provider's sending IPs, and DKIM signing is handled by your provider's infrastructure.

Important

If your organization doesn't send outbound email directly from Exchange Online, do **not** add Microsoft 365 SPF/DKIM records to your DNS. Instead, align your DNS authentication records with the third-party service that handles your outbound mail.

## Related content

- [Add a custom domain to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/add-domain)
- [Set up email authentication \(SPF, DKIM, DMARC\)](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about)
- [Limiting onmicrosoft domain usage for sending emails](https://techcommunity.microsoft.com/blog/exchange/limiting-onmicrosoft-domain-usage-for-sending-emails/4292065)
- [B2B collaboration invitation redemption](https://learn.microsoft.com/en-us/entra/external-id/redemption-experience)
