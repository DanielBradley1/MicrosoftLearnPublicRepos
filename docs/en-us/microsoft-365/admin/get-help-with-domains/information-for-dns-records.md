<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Gather the information you need to create DNS records

The procedures in this article assume that the process of [adding a domain](https://learn.microsoft.com/en-us/admin/setup/add-domain#add-a-domain) is started but that the domain isn't verified yet.

## Step 1: Find the TXT record value and verify

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **… Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Domains**](https://admin.cloud.microsoft/?#/Domains).
4. In the **Domains** page, select your domain, then select **Continue setup**. The domains setup wizard displays the specific TXT value you need to add.
5. On the **Domain Verification** page, select **Add a TXT record to the domain's DNS records**, then select **Continue**.
6. Copy the **TXT value** shown. It looks like this: **MS=msXXXXXXXX**.
7. Go to [Add DNS records to connect your domain](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide), and follow the steps to add records at your DNS host's website.
8. Follow the steps for creating the TXT record \(or MX record\) at your DNS host, then verify the domain back in Microsoft 365.
9. Remove the TXT record \(or MX record\) from your DNS host once the domain is verified in Microsoft 365.

## Step 2: Find the MX record value for email and more

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **… Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Domains**](https://admin.cloud.microsoft/?#/Domains).
4. In the **Domains** page, select your domain.
5. Choose **Manage DNS**, select **More Options** > **Add your own DNS**, and then select **Continue** to see the DNS records to add.

   Keep this information available while making changes at your DNS host so that you can later copy and paste the values.

   The groups of DNS records that are listed on the page depend on your choices listed under **Domain purpose**.
6. Go to [Add DNS records to connect your domain](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide), and follow the steps to add records at your DNS host's website.
7. Follow the steps for creating the records at your DNS host.

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
- [Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide).
- [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).
- [Manage domains](https://learn.microsoft.com/en-us/admin).
