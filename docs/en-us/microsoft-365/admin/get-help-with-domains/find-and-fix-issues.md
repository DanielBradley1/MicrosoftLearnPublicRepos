<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Find and fix issues after adding your domain or DNS records

Getting your domain set up to work with Microsoft 365 can be challenging. The DNS system is nit picky to work with, and the DNS setup for your domain affects important business activities, like email!

Note

You can check for problems with your domain by checking its status. Go to **Setup** > **Domains** and view the notifications in the **Status** column. If you see an issue, select the three dots \(more actions\), and then choose **Check health**. The pane that opens describes any issues occurring with your domain.

## What's going on?

- [Can't verify your domain?](#cant-verify-your-domain)
- [Outlook isn't working?](#outlook-isnt-working)
- [Everyone's email got switched to Microsoft 365 and you only wanted YOUR email to switch?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)
- [Can't confirm non-profit or school account status?](#cant-confirm-non-profit-or-school-account-status)
- [Services not working with your domain?](#services-not-working-with-your-domain)
- [Accessing your website isn't working?](#accessing-your-website-isnt-working)

## Can't verify your domain?

There are a couple of common reasons that domain verification doesn't work as it should:

1. **The verification record value isn't quite correct.** Double-check that the exact value is copied and pasted into the TXT verification record at your DNS host. One common issue isn't including the **MS=** part of the record.
2. **The record hasn't been saved.** At some DNS hosts, you have to take an extra step to save the zone file \(where the DNS record is stored\) so that it updates across the Internet. Make sure the changes are saved so Microsoft 365 can see and verify the record.
3. **The record hasn't updated across the Internet.** It typically only takes a few minutes for us to be able to see the new record, but occasionally it can take as long as a few hours.

## Outlook isn't working?

If the MX record and other DNS records are set up correctly for your domain but mail doesn't work, let Microsoft help you [fix your Outlook problems](https://learn.microsoft.com/en-us/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).

## Everyone's email got switched to Microsoft 365 and you only wanted YOUR email to switch?

When you add your domain to Microsoft 365, typically your domain's MX record is updated to point to Microsoft 365. All email sent to that domain starts coming to Microsoft 365 shortly after the MX record is set up. Make sure mailboxes are created in Microsoft 365 for everyone who has email on your domain before you change the MX record.

What if you don't want to move email for everyone on your domain to Microsoft 365? You can take steps to [pilot Microsoft 365 with just a few email addresses instead](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide).

## Can't confirm non-profit or school account status?

There are a couple of scenarios when you just need to verify your organization's domain and not set up any services. For example, to prove to Microsoft 365 that your organization qualifies for a school subscription.

Check out the guidance in [Verify your Microsoft 365 domain to prove ownership, nonprofit, or education status, or to activate Viva Engage](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide) to make sure all the required steps are completed.

## Services not working with your domain?

Microsoft can help you track down issues with your domain's DNS setup. The domains troubleshooter in Microsoft 365 shows you any records that you need to fix and exactly what the records need to be set to.

1. Go to **Setup > Domains**.
2. View the notifications in the **Status** column.
3. If you see an issue, select the three dots \(more actions\), and then select **Check health**.
4. The pane that opens describes any issues occurring with your domain.

Tip

Got your DNS set up correctly, but mail doesn't work in Outlook on your desktop? Check out the [different mail flow scenarios you can have with Microsoft 365](https://learn.microsoft.com/en-us/exchange/mail-flow-best-practices/mail-flow-best-practices) to make sure you've got things set up correctly for your business. Or get more troubleshooting help with email at [Fix Outlook problems](https://learn.microsoft.com/en-us/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).

## Accessing your website isn't working?

If DNS issues are fixed but you're still having trouble, try one of the following solutions:

- People can't get to your website at *contoso.com*: [Track down website issues](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/add-domain?view=o365-worldwide)
- You can't update your A record or CNAME record to point to your website: [Update custom DNS records in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/add-domain?view=o365-worldwide)

## Support

**[Check the Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)** if you don't find what you're looking for.

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).

## Related content

- [Small business help & learning](https://go.microsoft.com/fwlink/?linkid=2224585).
- [Troubleshoot: Audit data on verified domain change](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain).
- [Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide).
