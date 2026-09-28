<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/dns-records-for-office-365-gcc-high?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-04-11 -->

# DNS records for Office 365 GCC High

*This article applies to Office 365 GCC High and Microsoft 365 GCC High*

As part of onboarding to Office 365 GCC High, you need to add your Simple Mail Transfer Protocol \(SMTP\) and SIP domains to your Online Services tenant. You do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.

Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the following services. You might need to modify the below table to fit your organization's needs with respect to the inbound MX records and any existing Exchange Autodiscover records you have in place. We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.

Note

Azure AD and MSOnline PowerShell modules are deprecated as of March 30, 2024. To learn more, read the [deprecation update](https://techcommunity.microsoft.com/t5/microsoft-entra-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270). After this date, support for these modules are limited to migration assistance to Microsoft Graph PowerShell SDK and security fixes. The deprecated modules will continue to function through March, 30 2025.

We recommend migrating to [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview) to interact with Microsoft Entra ID \(formerly Azure AD\). For common migration questions, refer to the [Migration FAQ](https://learn.microsoft.com/en-us/powershell/azure/active-directory/migration-faq). *Note:* Versions 1.0.x of MSOnline may experience disruption after June 30, 2024.

## Exchange Online

| Type | Priority | Host name | Points to address or value | TTL |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant*.mail.protection.office365.us \(for more information, see below\) | One Hour |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | One Hour |
| CNAME | - | autodiscover | autodiscover.office365.us | One Hour |

### Exchange Autodiscover record

If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you complete your migration.

### Exchange Online MX Record

The MX record value for your accepted domains follows a standard format as noted previously: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.

For example, if your tenant name is contoso.onmicrosoft.us, you'd use **contoso.mail.protection.office365.us** as the value for your MX record.

## External DNS records required for Teams

### SRV records

| Type | Service | Protocol | Port | Weight | Priority | Name | Target | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | One Hour |

## Other DNS records

Important

If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time. The msoid record is incompatible with Microsoft 365 Enterprise Apps *\(formerly Office 365 ProPlus\)* and will prevent activation from succeeding.
