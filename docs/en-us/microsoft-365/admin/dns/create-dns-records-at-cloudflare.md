<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-cloudflare?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Connect your DNS records at Cloudflare to Microsoft 365

If Cloudflare is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Microsoft Teams Online, and so on.

## Before you begin

You have two options for setting up DNS records for your domain:

- [**Use Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain): Use the **Domain Connect** steps to automatically verify and set up your new domain to use with Microsoft 365 if your domain isn't yet set up with another email service provider.

  OR
- [**Use the manual steps**](#create-dns-records-with-manual-setup): Verify your domain using the manual steps in this article and choose when and which records to add to your domain registrar. This process allows you to set up new MX \(mail\) records, for example, at your convenience.

## Use Domain Connect to verify and set up your domain

Follow these steps to automatically verify and set up your Cloudflare domain with Microsoft 365:

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **… Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Domains**](https://admin.cloud.microsoft/?#/Domains).
4. In the **Domains** page, select the domain you want to set up.
5. Select the three dots \(more actions\) and then choose **Manage DNS**.
6. On the **How do you want to connect your domain?** page, select **Continue**.
7. On the **Add DNS record** page, select **Add DNS records**.
8. On the Cloudflare login page, sign in to your account, and select **Authorize**.

   Your domain setup for Microsoft 365 is complete.

## Create DNS records with manual setup

After you add these records at Cloudflare, your domain will be set up to work with Microsoft 365 services.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Change your domain's nameserver \(NS\) records

Important

You must perform this procedure at the domain registrar where you purchased and registered your domain.

When you signed up for Cloudflare, you added a domain by using the Cloudflare Setup process.

The domain that you added was purchased from Cloudflare or a separate domain registrar. To verify and create DNS records for your domain in Microsoft 365, you first need to change the nameservers at your domain registrar so that they use the Cloudflare nameservers.

To change your domain's name servers at your domain registrar's website yourself, follow these steps.

1. Find the area on the domain registrar's website where you can edit the nameservers for your domain.
2. Either create two nameserver records by using the values in the following table, or edit the existing nameserver records so that they match these values.
   | Type | Value |
   | --- | --- |
   | First nameserver | Use the nameserver value provided by Cloudflare. |
   | Second nameserver | Use the nameserver value provided by Cloudflare. |


   Tip


   You should use at least two name server records. If there are any other name servers listed, you should delete them.

3. Save your changes.

### Add a TXT record for verification

Before you use your domain with Microsoft, Microsoft needs to make sure that you own it. Your ability to sign in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

Note

This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. Make sure a domain is added in the Microsoft 365 Admin Center using the steps in [Add a domain](https://learn.microsoft.com/en-us/admin/setup/add-domain#add-a-domain), and that the domain isn't yet verified. The **TXT value** from the **Add a record to verify ownership** page needs to be copied for use later in this procedure.
2. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
3. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
4. On the DNS management page, select **+Add record**.

   [![Screenshot of where you select Add record to add a domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
5. Select the TXT type from the drop-down list, and type or copy and paste the values from this table. Use the TXT value \(MS=ms*XXXXXXXX*\) that you copied earlier.
   | Type | Name | TTL | Content |
   | --- | --- | --- | :--- |
   | TXT | @ | 30 minutes | MS=ms*XXXXXXXX*  <br>**Note:** This text is an example. Use your specific **Destination or Points to Address** value here, from the table. For more information, see [Gather the information you need to create DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide). |
6. Select **Save**.

   [![Screenshot of where you select Save to add a domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-txt-save.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-txt-save.png?view=o365-worldwide#lightbox)

   Wait a few minutes before you continue so that the record you created can update across the Internet.

Now that a record is added at your domain registrar's site, go back to Microsoft and search for the record. When Microsoft finds the correct TXT record, your domain is verified.

To verify the record in Microsoft 365:

1. In the admin center, go to the **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
2. On the Domains page, select the domain that you're verifying, and select **Manage DNS**.
3. Select **Continue**.
4. On the **Verify domain** page, select **Verify**.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add an MX record so email for your domain comes to Microsoft

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the DNS management page, select **+Add record**.

   [![Screenshot of where you select Add record to add an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the MX type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | Mail server | TTL | Priority |
   | --- | --- | --- | --- | --- |
   | MX | @ | *<domain-key>*.mail.protection.outlook.com  <br>**Note:** Get your *<domain-key>* from your Microsoft 365 account. For more information, see [Gather the information you need to create DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide). | 30 minutes | 1  <br>For more information about priority, see [What is MX priority?](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)  <br> |
5. Select **Save**.

   [![Screenshot of where you select Save record to add an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-mx-save.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-mx-save.png?view=o365-worldwide#lightbox)
6. If there are any other MX records listed in the **MX Records** section, delete them by selecting **Edit**, and then select **Delete**.

   [![Screenshot of where you select Delete.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-mx-delete.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-mx-delete.png?view=o365-worldwide#lightbox)
7. In the confirmation dialog box, select **Delete** to confirm your changes.

### Add the CNAME record required for Microsoft

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the **DNS management** page, select **+Add record**

   [![Screenshot of where you select Add record to add a CNAME record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the CNAME type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | Target | TTL |
   | --- | --- | --- | --- |
   | CNAME | autodiscover | autodiscover.outlook.com | Auto |
5. Select **Save**.

   [![Screenshot of where you select Save to add a CNAME record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-cname-save.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-cname-save.png?view=o365-worldwide#lightbox)

### Add a TXT record for SPF to help prevent email spam

Important

You can't have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, email errors, delivery issues, and spam classification issues can occur. If you already have an SPF record for your domain, don't create a new one for Microsoft 365. Instead, add the required Microsoft 365 values to the current record so that you have a *single* SPF record that includes both sets of values.

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the DNS management page, select **+Add record**.

   [![Screenshot of where you select Add record to add an SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the TXT type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | TTL | Content |
   | --- | --- | --- | --- |
   | TXT | @ | 30 minutes | v=spf1 include:spf.protection.outlook.com -all  <br>**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct. |
5. Select **Save**.

   [![Screenshot of where you select Save to add an SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-txt-spf-protection.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-txt-spf-protection.png?view=o365-worldwide#lightbox)

## Advanced option: Microsoft Teams

Only select this option if your organization uses Microsoft Teams for online communication services like chat, conference calls, and video calls, in addition to Microsoft Teams. Skype needs four records: two SRV records for user-to-user communication, and two CNAME records to sign-in and connect users to the service.

### Add the two required SRV records

Important

Keep in mind that Cloudflare is responsible for making this functionality available. In case you see discrepancies between the following steps and the current Cloudflare GUI \(Graphical User Interface\), consult the [Cloudflare Community](https://community.cloudflare.com/).

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the DNS management page, select **+Add record**

   [![Screenshot of where you select Add record to add an SRV record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the SRV type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | Service | Protocol | TTL | Priority | Weight | Port | Target |
   | --- | --- | --- | --- | --- | --- | --- | --- | --- |
   | SRV | Use your *domain\_name*; for example, contoso.com | \_sip | TLS | 30 minutes | 100 | 1 | 443 | sipfed.online.lync.com |
   | SRV | Use your *domain\_name*; for example, contoso.com | \_sipfederationtls | TCP | 30 minutes | 100 | 1 | 5061 | sipfed.online.lync.com |
5. Select **Save**.

   [![Screenshot of where you select Save to add an SRV record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-srv-save.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-srv-save.png?view=o365-worldwide#lightbox)
6. Add the other SRV record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add the two required CNAME records for Microsoft Teams

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the DNS management page, select **+Add record**

   [![Screenshot of where you select Add record to add CNAME records for Microsoft Teams.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the CNAME type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | Target | TTL |
   | --- | --- | --- | --- |
   | CNAME | sip | sipdir.online.lync.com  <br> | 1 Hour |
   | CNAME | lyncdiscover | webdir.online.lync.com  <br> | 1 Hour |
5. Select **Save**.
6. Add the other CNAME record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Advanced option: Intune and Mobile Device Management for Microsoft 365

This service helps you secure and remotely manage mobile devices that connect to your domain. Mobile Device Management needs two CNAME records so that users can enroll devices to the service.

### Add the two required CNAME records for Mobile Device Management

1. To get started, sign in to your domains page at Cloudflare by using [this link](https://www.cloudflare.com/a/login).
2. On the Account Home page, find the domain that you want to update, select the three dots \(**...**\) at the right and select **Configure DNS** from the drop-down menu.

   [![Screenshot of the domain you want to update.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-1.png?view=o365-worldwide#lightbox)
3. On the DNS management page, select **+Add record**.

   [![Screenshot of where you select Add record to add CNAME records for Mobile Device Management.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-cloudflare/cloudflare-domains-add-record.png?view=o365-worldwide#lightbox)
4. Select the CNAME type from the drop-down list, and type or copy and paste the values from this table.
   | Type | Name | Target | TTL |
   | --- | --- | --- | --- |
   | CNAME | enterpriseregistration | enterpriseregistration.windows.net  <br> | 1 Hour |
   | CNAME | enterpriseenrollment | enterpriseenrollment-s.manage.microsoft.com  <br> | 1 Hour |
5. Select **Save**.
6. Add the other CNAME record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Support

**[Check the Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)** if you don't find what you're looking for.

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).
