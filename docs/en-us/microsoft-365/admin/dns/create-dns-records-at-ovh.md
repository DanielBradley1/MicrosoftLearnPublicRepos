<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Connect your DNS records at OVH to Microsoft 365

Use this article to connect DNS records at OVH to Microsoft 365 by verifying domain ownership and adding the required records for email, Microsoft Teams, and device management. After you add the records, your domain is ready to work with Microsoft 365.

This article covers the creation of the following DNS records at OVH:

| **Service** | **DNS record types** |
| --- | --- |
| [**Domain verification**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=domain-verify#add-microsoft-365-dns-records-at-ovh) | TXT |
| [**Email**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=email#add-microsoft-365-dns-records-at-ovh) | MX, CNAME \(Autodiscover\), TXT \(SPF\) |
| [**Microsoft Teams**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=teams#add-microsoft-365-dns-records-at-ovh) | SRV \(2\), CNAME \(2\) |
| [**Microsoft Intune/MDM**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=intune-mdm#add-microsoft-365-dns-records-at-ovh) | CNAME \(2\) |

Note

OVH is a non-Microsoft site. Microsoft doesn't control the OVH site. Additionally, OVH might change their website and tools so that the steps in this article are no longer valid. For support with OVH's site and tools, contact OVH support.

## Before you begin

- You must own a domain registered with OVH.
- You must add the domain in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). If the domain isn't added in the Microsoft 365 admin center, follow the steps in [Add a domain](https://learn.microsoft.com/en-us/admin/setup/add-domain#add-a-domain) to add your domain before you start adding DNS records at OVH.

Note

When creating or updating DNS records, it typically takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a DNS record change to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Find and fix issues after adding your domain or DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues?view=o365-worldwide).

## Sign in to OVH to manage your domain's DNS records

To add DNS records at OVH, sign in to your OVH account and then go to the page where you can manage your domain's DNS records. Follow these steps to get there:

1. Sign in to your OVH domains page by going to the OVH [Log in to OVH](https://www.ovh.com/manager/) page.

   [![Screenshot of the OVH login page.](https://learn.microsoft.com/en-us/microsoft-365/media/1424cc15-720d-49d1-b99b-8ba63b216238.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/1424cc15-720d-49d1-b99b-8ba63b216238.png?view=o365-worldwide#lightbox)
2. On the dashboard landing page, under **View all my activity**, select the name of the domain that you want edit.
3. Select the **DNS zone** tab.

   [![Screenshot of the OVH DNS zone tab selected for a domain.](https://learn.microsoft.com/en-us/microsoft-365/media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png?view=o365-worldwide#lightbox)

## Add Microsoft 365 DNS records at OVH

To add required DNS records at OVH for Microsoft 365 services, select the tab based on which DNS records you need to add:

- [**Domain Verification**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=domain-verify#add-microsoft-365-dns-records-at-ovh).
- [**Email**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=email#add-microsoft-365-dns-records-at-ovh).
- [**Microsoft Teams**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=teams#add-microsoft-365-dns-records-at-ovh).
- [**Microsoft Intune/Mobile Device Management for Microsoft 365**](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=intune-mdm#add-microsoft-365-dns-records-at-ovh).

- 

  [![](https://learn.microsoft.com/en-us/microsoft-365/media/icons/domain-18.svg?view=o365-worldwide)](#tabpanel_1_domain-verify)

- 

  [![](https://learn.microsoft.com/en-us/microsoft-365/media/icons/email-18.svg?view=o365-worldwide)](#tabpanel_1_email)

- 

  [![](https://learn.microsoft.com/en-us/microsoft-365/media/icons/teams-18.svg?view=o365-worldwide)](#tabpanel_1_teams)

- 

  [![](https://learn.microsoft.com/en-us/microsoft-365/media/icons/intune-18.svg?view=o365-worldwide)](#tabpanel_1_intune-mdm)

#### Add a TXT record for domain ownership verification

Before you can use your domain with Microsoft 365, you need to prove you own the domain. Your ability to sign in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain. This process involves creating a TXT record at your domain registrar with a specific value that Microsoft can look for. When Microsoft finds the record with the correct value, your domain is verified. The TXT record is used only to verify that you own your domain. It doesn't affect anything else and can be deleted once domain verification is complete.

Note

The procedures in this section assume that you started the process of [adding a domain](https://learn.microsoft.com/en-us/admin/setup/add-domain#add-a-domain), but you didn't verify domain ownership yet.

To add the TXT record for domain verification at OVH, follow these steps:

1. Get the **TXT** value specific for your domain from the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). For help on finding the value of your TXT record in the Microsoft 365 admin center, see [Gather the information you need to create DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide#step-1-find-the-txt-record-value-and-verify).
2. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
3. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
4. In the **Extended records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **TXT**.

   [![Screenshot of the OVH TXT entry selected in the Extended records section.](https://learn.microsoft.com/en-us/microsoft-365/media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png?view=o365-worldwide#lightbox)
5. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Record Type** | **Subdomain** | **TTL** | **Value** |
   | --- | --- | --- | --- |
   | TXT | *leave blank* | 3600 \(seconds\) | *MS=msXXXXXXXX* |


   - In the **Value** field, replace *MS=msXXXXXXXX* with the TXT value you gathered earlier from the Microsoft 365 admin center. The value shown in the table is only an example.

6. Select **Next**.
7. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.

   [![Screenshot of the OVH confirmation pane for the TXT record used for verification.](https://learn.microsoft.com/en-us/microsoft-365/media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png?view=o365-worldwide#lightbox)
8. Wait a few minutes before you continue, so that the record you created can update across the Internet.

Now that you added the TXT record at your domain registrar's site, go back to the Microsoft 365 admin center and complete the domain ownership verification process. When Microsoft 365 finds the correct TXT record, your domain is verified.

To verify the record in the Microsoft 365 admin center, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. From the left navigation bar, select **... Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
4. In the **Domains** page, select the ellipsis **⋮** next to the domain that you're verifying, and then select **Start setup**.

   [![Screenshot of the Microsoft 365 admin center Domains page with the Start setup option selected to begin domain verification.](https://learn.microsoft.com/en-us/microsoft-365/media/dns-ionos/ionos-domainconnects-2.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/dns-ionos/ionos-domainconnects-2.png?view=o365-worldwide#lightbox)
5. In the **Verify you own your domain** page, make sure **Add a TXT record to the domain's DNS records** is selected, and then select **Continue**.
6. On the **Add a record to verify domain ownership** page, select **Verify**.
7. After you verify domain ownership, the **How do you want to connect your domain?** page appears. The rest of the wizard walks you through adding additional DNS records to connect your domain to Microsoft 365 services. For more information, see the following article or the following sections in this article:

   - [Connect to Microsoft services by adding DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide&&tabs=manual#step-2-connect-to-microsoft-services-by-adding-dns-records).
   - [Add an MX record to enable email delivery to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=email#add-an-mx-record-to-enable-email-delivery-to-microsoft-365).
   - [Add a CNAME record so email accounts are automatically set up in Outlook and other email clients](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=email#add-a-cname-record-so-email-accounts-are-automatically-set-up-in-outlook-and-other-email-clients).
   - [Add an SPF TXT record to help prevent email spam](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=email#add-an-spf-txt-record-to-help-prevent-email-spam).
   - [DNS records for Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=teams#dns-records-for-microsoft-teams).
   - [DNS records for Microsoft Intune and Mobile Device Management for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/dns/create-dns-records-at-ovh?view=o365-worldwide&&tabs=intune-mdm#dns-records-for-microsoft-intune-and-mobile-device-management-for-microsoft-365).

#### DNS records for Microsoft 365 email

Microsoft 365 email requires three types of DNS records:

- An [MX](#add-an-mx-record-to-enable-email-delivery-to-microsoft-365) record for email delivery.
- A [CNAME](#add-a-cname-record-so-email-accounts-are-automatically-set-up-in-outlook-and-other-email-clients) record for email account discovery.
- A [TXT](#add-an-spf-txt-record-to-help-prevent-email-spam) record for SPF email spam protection.

To add each of these types of records at OVH, follow the steps in the following sections.

##### Add an MX record to enable email delivery to Microsoft 365

To add the MX record for email at OVH, follow these steps:

1. Get the **MX** value specific for your domain from the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). For help on finding the value of your MX record in the Microsoft 365 admin center, see [Gather the information you need to create DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/information-for-dns-records?view=o365-worldwide#step-2-find-the-mx-record-value-for-email-and-more).
2. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
3. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
4. In the **Mail records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **MX**.

   [![Screenshot of the OVH MX record type selected in the Mail records section.](https://learn.microsoft.com/en-us/microsoft-365/media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png?view=o365-worldwide#lightbox)
5. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Priority** | **Target** |
   | --- | --- | --- | --- |
   | *leave blank* | 3600 \(seconds\) | 0 | *<mx-value>*.mail.protection.outlook.com. |


   - In the **Target** field, replace *<mx-value>* with the MX value you gathered earlier from the Microsoft 365 admin center. Make sure this entry ends with a period \(**.**\). The value shown in the table is only an example.
   - For more information about priority, see [What is MX priority?](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide#what-is-mx-priority)


   Note


   By default OVH uses relative notation for the target. Relative notation adds the domain name to the end of the target record. To use absolute notation instead, add a dot to the target record as shown in the table.

6. Select **Next**.  [![Screenshot of the OVH MX record pane with the Next button.](https://learn.microsoft.com/en-us/microsoft-365/media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png?view=o365-worldwide#lightbox)
7. In the **Add an entry to the DNS zone** pane, select **Confirm**.

   [![Screenshot of the OVH MX record pane with the Confirm button.](https://learn.microsoft.com/en-us/microsoft-365/media/090bfb11-a753-4af0-8982-582a4069a169.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/090bfb11-a753-4af0-8982-582a4069a169.png?view=o365-worldwide#lightbox)
8. Remove all previous MX records except for the one that you just added. In the **DNS zone** page, select each record that needs to be deleted and then in the **Actions** column, select the trash-can **Delete** icon.

   [![Screenshot of the OVH DNS zone page with the Delete icon for an MX record.](https://learn.microsoft.com/en-us/microsoft-365/media/892b328b-7057-4828-b8c5-fe26284dc8c2.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/892b328b-7057-4828-b8c5-fe26284dc8c2.png?view=o365-worldwide#lightbox)
9. Once all previous MX records are deleted, in the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.

##### Add a CNAME record so email accounts are automatically set up in Outlook and other email clients

To add a CNAME record for email account discovery at OVH, follow these steps:

1. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
2. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
3. In the **Pointer records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **CNAME**.

   [![Screenshot of the OVH CNAME record type selected in the Pointer records section.](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide#lightbox)
4. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Target** |
   | --- | --- | --- |
   | autodiscover | 3600 \(seconds\) | autodiscover.outlook.com. |


   Important


   Make sure the **Value** *autodiscover.outlook.com.* ends with a period \(**.**\).


   [![Screenshot of the OVH CNAME record values for autodiscover.](https://learn.microsoft.com/en-us/microsoft-365/media/516938b3-0b12-4736-a631-099e12e189f5.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/516938b3-0b12-4736-a631-099e12e189f5.png?view=o365-worldwide#lightbox)

5. Select **Next**.

   [![Screenshot of the OVH CNAME values entered with the Next button.](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide#lightbox)
6. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.

##### Add an SPF TXT record to help prevent email spam

Important

If your domain already has an SPF record, don't create a new one for Microsoft 365. Instead, add the required Microsoft 365 values to the existing record so that you have a *single* SPF record that includes both sets of values.

To add an SPF TXT record for email spam protection at OVH, follow these steps:

1. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
2. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
3. In the **Pointer records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **TXT**.
4. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Value** |
   | --- | --- | --- |
   | *leave blank* | 3600 \(seconds\) | v=spf1 include:spf.protection.outlook.com -all |


   [![Screenshot of the OVH TXT record values for SPF.](https://learn.microsoft.com/en-us/microsoft-365/media/f50466e9-1557-4548-8a39-e98978a5ee2e.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/f50466e9-1557-4548-8a39-e98978a5ee2e.png?view=o365-worldwide#lightbox)

5. Select **Next**.

   [![Screenshot of the OVH TXT record for SPF entered with the Next button.](https://learn.microsoft.com/en-us/microsoft-365/media/7937eb7c-114f-479f-a916-bcbe476d6108.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/7937eb7c-114f-479f-a916-bcbe476d6108.png?view=o365-worldwide#lightbox)
6. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.

   [![Screenshot of the OVH TXT record for SPF with the Confirm button.](https://learn.microsoft.com/en-us/microsoft-365/media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png?view=o365-worldwide#lightbox)

#### DNS records for Microsoft Teams

Microsoft Teams needs four records:

- Two [SRV](#add-the-two-required-srv-records-for-microsoft-teams) records for user-to-user communication.
- Two [CNAME](#add-the-two-required-cname-records-for-microsoft-teams) records to sign in and connect users to the service.

Only add these DNS records if your organization uses Microsoft Teams.

##### Add the two required SRV records for Microsoft Teams

To add SRV records for Microsoft Teams at OVH, follow these steps:

1. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
2. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
3. In the **Extended records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **SRV**.
4. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Value** |
   | --- | --- | --- |
   | *leave blank* | 3600 \(seconds\) | v=spf1 include:spf.protection.outlook.com -all |

   | **Subdomain** | **TTL** | **Priority** | **Weight** | **Port** | **Target** |
   | --- | --- | --- | --- | --- | --- |
   | \_sip.\_tls | 3600 \(seconds\) | 100 | 1 | 443 | sipdir.online.lync.com. |
   | \_sipfederationtls.\_tcp | 3600 \(seconds\) | 100 | 1 | 5061 | sipfed.online.lync.com. |


   Important


   Make sure both **Target** fields *sipdir.online.lync.com.* and *sipfed.online.lync.com.* end with a period \(**.**\).

5. To add the second SRV record, select **Add another record**, create another SRV record using the values from the second row in the table, and then select **Create records**.
6. Once both SRV records are added, select **Confirm**.
7. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.

##### Add the two required CNAME records for Microsoft Teams

To add CNAME records for Microsoft Teams at OVH, follow these steps:

1. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
2. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
3. In the **Pointer records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **CNAME**.

   [![Screenshot of the OVH CNAME record type selected in the Pointer records section.](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide#lightbox)
4. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Target** |
   | --- | --- | --- |
   | sip | 3600 \(seconds\) | sipdir.online.lync.com. |
   | lyncdiscover | 3600 \(seconds\) | webdir.online.lync.com. |


   Important


   Make sure both **Target** fields *sipdir.online.lync.com.* and *webdir.online.lync.com.* end with a period \(**.**\).

5. Select **Next**.

   [![Screenshot of the OVH CNAME values entered with the Next button.](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide#lightbox)
6. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.
7. Repeat the steps to add the second CNAME record using the values from the second row in the table.

#### DNS records for Microsoft Intune and Mobile Device Management for Microsoft 365

Microsoft Intune and Mobile Device Management for Microsoft 365 help you secure and remotely manage devices that connect to your domain. Mobile Device Management for Microsoft 365 needs two CNAME records so that users can enroll devices to the service. Only add these records if your organization uses Microsoft Intune or Mobile Device Management for Microsoft 365.

##### Add the two required CNAME records for Microsoft Intune and Mobile Device Management for Microsoft 365

To add CNAME records for Microsoft Intune and Mobile Device Management for Microsoft 365 at OVH, follow these steps:

1. If you're not already signed in to the OVH **DNS Zone** page for your domain, follow the steps in [Sign in to OVH to manage your domain's DNS records](#sign-in-to-ovh-to-manage-your-domains-dns-records) to get there.
2. In the **DNS Zone** page, select the **Add an entry** tile.

   [![Screenshot of the OVH DNS Zone page with the Add an entry tile.](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png?view=o365-worldwide#lightbox)
3. In the **Pointer records** section of the **Step 1 of 3 - Add an entry to the DNS zone** pane, select **CNAME**.

   [![Screenshot of the OVH CNAME record type selected in the Pointer records section.](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png?view=o365-worldwide#lightbox)
4. In the **Step 2 of 3 - Add an entry to the DNS zone** pane, enter the values from the following table:
   | **Subdomain** | **TTL** | **Target** |
   | --- | --- | --- |
   | enterpriseregistration | 3600 \(seconds\) | enterpriseregistration.windows.net. |
   | enterpriseenrollment | 3600 \(seconds\) | enterpriseenrollment-s.manage.microsoft.com. |


   Important


   Make sure both **Target** fields *enterpriseregistration.windows.net.* and *enterpriseenrollment-s.manage.microsoft.com.* end with a period \(**.**\).

5. Select **Next**.

   [![Screenshot of the OVH CNAME values entered with the Next button.](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png?view=o365-worldwide#lightbox)
6. In the **Step 3 of 3 - Add an entry to the DNS zone** pane, select **Confirm**.
7. Repeat the steps to add the second CNAME record using the values from the second row in the table.

## Advanced option: Intune and Mobile Device Management for Microsoft 365

This service helps you secure and remotely manage mobile devices that connect to your domain. Mobile Device Management needs two CNAME records so that users can enroll devices to the service.

## Support

If you don't find what you're looking for, check the [**Domains FAQ**](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/domains-faq?view=o365-worldwide).

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).
