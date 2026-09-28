<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-web-com?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# Connect your DNS records at web.com to Microsoft 365

**[Check the Domains FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)** if you don't find what you're looking for.

If web.com is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Microsoft Teams Online, and so on.

After you add these records at web.com, your domain will be set up to work with Microsoft services.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).

## Change your domain's nameserver \(NS\) records

Important

You must perform this procedure at the domain registrar where you purchased and registered your domain.

When you signed up for web.com, you added a domain by using the web.com **Setup** process.

To verify and create DNS records for your domain in Microsoft, you first need to change the nameservers at your domain registrar so that they use the web.com nameservers.

To change your domain's name servers at your domain registrar's website yourself, follow these steps.

1. Find the area on the domain registrar's website where you can edit the nameservers for your domain.
2. Either create two nameserver records by using the values in the following table, or edit the existing nameserver records so that they match these values.
   | Type | Value |
   | --- | --- |
   | First nameserver | Use the nameserver value provided by web.com. |
   | Second nameserver | Use the nameserver value provided by web.com. |


   Tip


   You should use at least two name server records. If there are any other name servers listed, you should delete them.

3. Save your changes.

Note

Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Then your Microsoft email and other services will be all set to work with your domain.

## Add a TXT record for verification

Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.

Note

This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add a domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **TXT** from the drop-down list.

   ![Select TXT from the Type drop-down list for the domain verification TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-txt.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Refers | TXT value | TTL |
   | --- | --- | :--- |
   | @ | MS=ms*XXXXXXXX*  <br>**Note:** This is an example. Use your specific **Destination or Points to Address** value here, from the table. [How do I find this?](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide) | 1 Hour |
8. Select **ADD**.

   Wait a few minutes before you verify your new TXT record, so that the record you just created can update across the Internet.

Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record. When Microsoft finds the correct TXT record, your domain is verified.

To verify the record in Microsoft 365:

1. In the admin center, go to the **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
2. On the Domains page, select the domain that you're verifying, and select **Start setup**.

   ![Select Start setup.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-ionos/ionos-domainconnects-2.png?view=o365-worldwide)
3. Select **Continue**.
4. On the **Verify domain** page, select **Verify**.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Add an MX record so email for your domain will come to Microsoft

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **MX** from the drop-down list.
7. Select, or copy and paste, the values from the following table.
   | Refers to | Mail server | Priority | TTL |
   | --- | --- | --- | --- |
   | @ | *<domain-key>*.mail.protection.outlook.com  <br>**Note:** Get your *<domain-key>* from the Microsoft admin center. [How do I find this?](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide) | For more information about priority, see [What is MX priority?](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide)  <br>1 | 1 Hour |
8. Select **ADD**.

   ![Screenshot of where you select Add to add an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-mx-add.png?view=o365-worldwide)
9. If there are any other MX records, delete all of them by selecting the edit tool, and then **Delete** for each record.

   ![Select Edit.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-edit.png?view=o365-worldwide)

## Add the CNAME record required for Microsoft

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add a CNAME record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **CNAME** from the drop-down list.

   ![Select CNAME from the Type drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Refers to | Host name | Alias to | TTL |
   | --- | --- | --- | --- |
   | Other Host | autodiscover | autodiscover.outlook.com | 1 Hour |


   ![Type or copy and paste the CNAME values into the window.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname-values.png?view=o365-worldwide)

8. Select **ADD**.

## Add a TXT record for SPF to help prevent email spam

Important

You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Microsoft. Instead, add the required Microsoft values to the current record so that you have a *single* SPF record that includes both sets of values.

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add an SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **TXT** from the drop-down list.

   ![Select TXT from the Type drop-down list for the SPF TXT record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-txt.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Refers to | TXT value | TTL |
   | --- | --- | --- |
   | @ | v=spf1 include:spf.protection.outlook.com -all  <br>**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct. | 1 Hour |
8. Select **ADD**.

## Advanced option: Microsoft Teams

Only select this option if your organization uses Microsoft Teams for online communication services like chat, conference calls, and video calls, in addition to Microsoft Teams. Skype needs 4 records: 2 SRV records for user-to-user communication, and 2 CNAME records to sign-in and connect users to the service.

### Add the two required SRV records

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add an SRV record.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **SRV** from the drop-down list.

   ![Select SRV from the Type drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-srv.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Type | Service | Protocol | Weight | Port | Target | Priority | TTL |
   | --- | --- | --- | --- | --- | --- | --- | --- |
   | SRV | \_sip | TLS | 100 | 443 | sipdir.online.lync.com  <br>**This value CANNOT end with a period \(.\)** | 1 | 1 Hour |
   | SRV | \_sipfederationtls | TCP | 100 | 5061 | sipfed.online.lync.com  <br>**This value CANNOT end with a period \(.\)** | 1 | 1 Hour |


   ![Type or copy and paste the values from the table into the SRV record window.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-srv-add.png?view=o365-worldwide)

8. Select **ADD**.
9. Add the other SRV record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

### Add the two required CNAME records for Microsoft Teams

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add CNAME records for Microsoft Teams.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **CNAME** from the drop-down list.

   ![Select CNAME from the Type drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Type | Refers to | Host Name | Alias to | TTL |
   | --- | --- | --- | --- | --- |
   | CNAME | Other Host | sip | sipdir.online.lync.com  <br>**This value CANNOT end with a period \(.\)** | 1 Hour |
   | CNAME | Other Host | lyncdiscover | webdir.online.lync.com  <br>**This value CANNOT end with a period \(.\)** | 1 Hour |


   ![Type or copy and paste the CNAME values into the window.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname-values.png?view=o365-worldwide)

8. Select **ADD**.
9. Add the other CNAME record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Advanced option: Intune and Mobile Device Management for Microsoft 365

This service helps you secure and remotely manage mobile devices that connect to your domain. Mobile Device Management needs 2 CNAME records so that users can enroll devices to the service.

### Add the two required CNAME records for Mobile Device Management

1. To get started, go to your domains page at web.com by using [this link](https://checkout.web.com/manage-it/index.jsp). Log in first.
2. On the landing page, select **Domain Names**.
3. Under **Actions**, select the three dots, and then select **Manage** in the drop-down list.

   ![Select Manage from the drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-1.png?view=o365-worldwide)
4. Scroll down to select **Advanced Tools**, and next to **Advanced DNS Records**, select **MANAGE**.

   You might have to select **Continue** to get to the Manage Advanced DNS Records page.

   ![Next to Advanced DNS records, select MANAGE.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-2.png?view=o365-worldwide)
5. On the Manage Advanced DNS Records page, select **+ ADD RECORD**.

   ![Screenshot of where you select Add a record to add CNAME records for Mobile Device Management.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-add-record.png?view=o365-worldwide)
6. Under **Type**, select **CNAME** from the drop-down list.

   ![Select CNAME from the Type drop-down list.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname.png?view=o365-worldwide)
7. Select, or copy and paste, the values from the following table.
   | Type | Refers to | Host Name | Alias to | TTL |
   | --- | --- | --- | --- | --- |
   | CNAME | Other Host | enterpriseregistration | enterpriseregistration.windows.net  <br>**This value CANNOT end with a period \(.\)** | 1 Hour |
   | CNAME | Other Host | enterpriseenrollment | enterpriseenrollment-s.manage.microsoft.com  <br>**This value CANNOT end with a period \(.\)** | 1 Hour |


   ![Type or copy and paste the CNAME values from the table into the window.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-webcom/webcom-domains-cname-values.png?view=o365-worldwide)

8. Select **ADD**.
9. Add the other CNAME record by copying the values from the second row of the table.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).
