<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-godaddy?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# Connect your DNS records at GoDaddy to Microsoft 365

**[Check the Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)** if you don't find what you're looking for.

If GoDaddy is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Teams, and so on.

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).

## Before you begin

You have two options for setting up DNS records for your domain:

- [**Use Domain Connect**](#use-domain-connect-to-verify-and-set-up-your-domain) If you haven't set up your domain with another email service provider, use the Domain Connect steps to automatically verify and set up your new domain to use with Microsoft 365.

  OR
- [**Use the manual steps**](#create-dns-records-with-manual-setup) Verify your domain using the manual steps below and choose when and which records to add to your domain registrar. This allows you to set up new MX \(mail\) records, for example, at your convenience.

## Use Domain Connect to verify and set up your domain

Follow these steps to automatically verify and set up your GoDaddy domain with Microsoft 365:

1. In the Microsoft 365 admin center, select **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818), and select the domain you want to set up.
2. Select the three dots \(more actions\) > choose **Start setup**.

   ![Select Start setup.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-ionos/ionos-domainconnects-2.png?view=o365-worldwide)
3. On the How do you want to connect your domain? page, select **Continue**.
4. On the Add DNS records page, select **Add DNS records**.
5. On the GoDaddy login page, sign in to your account, and select **Authorize**.

   This completes your domain setup for Microsoft 365.

## Create DNS records with manual setup

After you add these records at GoDaddy, your domain will be set up to work with Microsoft services.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add a TXT record for verification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

Note

This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Select DNS.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **DNS Records**, select **Add New Record** on the top right corner.

   ![Screenshot of where you select Add to add a domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Select **TXT** option from the filter box.
5. In the boxes for the new record, type or copy and paste the values from the table.
   | Type | Name | Value | TTL |
   | --- | --- | --- | --- |
   | TXT | @ | MS=ms *XXXXXXXX*  <br>**Note**: This is an example. Use your specific **Destination or Points to Address** value here, from the table. [How do I find this?](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide) | 1 hour  <br> |


   ![Fill in the values from the table for the domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-txtvalue.png?view=o365-worldwide)

6. Select **Save**.

   Wait a few minutes before you continue, so that the record you just created can update across the Internet.

Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record. When Microsoft finds the correct TXT record, your domain is verified.

To verify the record in Microsoft 365:

1. In the admin center, go to the **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
2. On the Domains page, select the domain that you're verifying, and select **Start setup**.

   ![Diagram showing Select Start setup.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-ionos/ionos-domainconnects-2.png?view=o365-worldwide)
3. Select **Continue**.
4. On the **Verify domain** page, select **Verify**.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add an MX record so email for your domain will come to Microsoft

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screenshot showing Select DNS.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **MX** option from the filter box.
5. In the boxes for the new record, type or copy and paste the values from the following table.

   \(Choose the **Type** and **TTL** values from the drop-down list.\)

   | Type | Name | Priority | Value | TTL |
   | --- | --- | --- | --- | --- |
   | MX | @ | 10  <br>For more information about priority, see [What is MX priority?](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide) | *<domain-key>*.mail.protection.outlook.com  <br>**Note:** Get your *<domain-key>* from your Microsoft account. [How do I find this?](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide) | 1 hour |


   ![Screenshot showing paste values for the MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-mxvalues.png?view=o365-worldwide)

6. Select **Save**.

### Add the CNAME record required for Microsoft

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screenshot displaying Select DNS.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add a CNAME record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **CNAME** from the drop-down list.
5. Create the CNAME record.

   In the boxes for the new record, type or copy and paste the values from the first row of the following table.

   \(Choose the **TTL** value from the drop-down list.\)

   | Type | Name | Value | TTL |
   | --- | --- | --- | --- |
   | CNAME | autodiscover | autodiscover.outlook.com | 1 hour |


   ![Screenshot to paste the values for the CNAME record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-cname-values.png?view=o365-worldwide)

6. Select **Save**.

### Add a TXT record for SPF to help prevent email spam

Important

You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Microsoft. Instead, add the required Microsoft values to the current record so that you have a *single* SPF record that includes both sets of values.

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screenshot showing Select DNS from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add an SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **TXT** from the drop-down list.
5. In the boxes for the new record, type or copy and paste the following values.

   \(Choose the **TTL** value from the drop-down lists.\)

   | Type | Name | Value | TTL |
   | --- | --- | --- | --- |
   | TXT | @ | v=spf1 include:secureserver.net -all  <br>**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct. | 1 hour |


   ![Fill in the values from the table for the SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-txtvalue.png?view=o365-worldwide)

6. Select **Save**.

## Advanced option: Microsoft Teams

Only select this option if your organization uses Microsoft Teams. Teams needs 4 records: 2 SRV records for user-to-user communication, and 2 CNAME records to sign-in and connect users to the service.

### Add the two required SRV records

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screenshot showing select DNS from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add an SRV record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **SRV** from the drop-down list.
5. Create the first SRV record.

   In the boxes for the new record, type or copy and paste the values from the first row of the following table.

   \(Choose the **Type** and **TTL** values from the drop-down lists.\)

   | Type | Service | Protocol | Name | Value | Priority | Weight | Port | TTL |
   | --- | --- | --- | --- | --- | --- | --- | --- | --- |
   | SRV | \_sip | \_tls | @ | sipdir.online.lync.com | 100 | 1 | 443 | 1 Hour |
   | SRV | \_sipfederationtls | \_tcp | @ | sipfed.online.lync.com | 100 | 1 | 5061 | 1 Hour |


   ![Fill in the values from the table for the SRV records.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-srv-records.png?view=o365-worldwide)

6. Select **Save**.
7. Add the other SRV record by performing steps 3-5 again.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add the two required CNAME records for Microsoft Teams

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screenshot showing Select Manage DNS from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add CNAME records for Microsoft Teams.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **CNAME** from the drop-down list.
5. In the empty boxes for the new records, type or copy and paste the values from the first row in the following table.
   | Type | Name | Value | TTL |
   | --- | --- | --- | --- |
   | CNAME | sip | sipdir.online.lync.com.  <br>**This value MUST end with a period \(.\)** | 1 Hour |
   | CNAME | lyncdiscover | webdir.online.lync.com.  <br>**This value MUST end with a period \(.\)** | 1 Hour |


   ![Fill in the values from the table for the CNAME records for Microsoft Teams.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-cname-values.png?view=o365-worldwide)

6. Select **Save**.
7. Add the other CNAME record by performing steps 3-5 again.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Advanced option: Intune and Mobile Device Management for Microsoft 365

This service helps you secure and remotely manage mobile devices that connect to your domain. Mobile Device Management needs 2 CNAME records so that users can enroll devices to the service.

### Add the two required CNAME records Mobile Device Management

1. To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled).

   If you're prompted to log in, use your login credentials, select your login name in the upper right, and then select **My Products**.
2. Under **Domains**, in the Portfolio tab, select the ellipse \(...\) next to the domain you want to verify, and select **Edit DNS** from the drop-down menu.

   ![Screesnhot showing Select DNS from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-manage-dns.png?view=o365-worldwide)
3. Under **Records**, select **Add New Record**.

   ![Screenshot of where you select Add to add CNAME records for Mobile Device Management.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-add.png?view=o365-worldwide)
4. Choose **CNAME** from the drop-down list.
5. In the empty boxes for the new records, type or copy and paste the values from the first row in the following table.
   | Type | Name | Value | TTL |
   | --- | --- | --- | --- |
   | CNAME | enterpriseregistration | enterpriseregistration.windows.net.  <br>**This value MUST end with a period \(.\)** | 1 Hour |
   | CNAME | enterpriseenrollment | enterpriseenrollment-s.manage.microsoft.com.  <br>**This value MUST end with a period \(.\)** | 1 Hour |


   ![Fill in the values from the table for the CNAME records for Mobile Device Management.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-godaddy/godaddy-domains-cname-values.png?view=o365-worldwide)

6. Select **Save**.
7. Add the other CNAME record by performing steps 3-5 again.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).
