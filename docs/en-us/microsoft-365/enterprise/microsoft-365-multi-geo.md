<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Microsoft 365 Multi-Geo: Overview and requirements

The [*Microsoft 365 Multi-Geo Capabilities add-on*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \("*Multi-Geo*"\) provides enterprise customers with the ability to expand their Microsoft 365 presence to multiple geographic regions \("[*Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)"\) within a single existing Microsoft 365 [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions). Customers must license *Multi-Geo* through the Enterprise Agreement, Web Direct, or CSP channels.

*Multi-Geo* is intended for enterprise customers who need to store data in multiple *Geographies* to satisfy [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) requirements, while retaining single-tenant administration and full-fidelity collaboration experiences between users as necessary.

*Multi-Geo* enables customers to manage and store in-scope data at a user level for [*Microsoft 365 Core Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) including Exchange Online, SharePoint/OneDrive, Microsoft Teams, and Microsoft 365 Copilot and Microsoft 365 Copilot Chat. In addition, *Multi-Geo* can be used with shared resources including SharePoint sites, Microsoft 365 Groups, Shared Mailboxes, eDiscovery, or Microsoft Teams teams.

Customers that utilize Microsoft Purview eDiscovery Standard or Premium should refer to [Microsoft 365 Multi-Geo eDiscovery configuration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-ediscovery-configuration?view=o365-worldwide) and [Set up compliance boundaries for eDiscovery investigations](https://learn.microsoft.com/en-us/purview/ediscovery-set-up-compliance-boundaries#searching-and-exporting-content-in-multi-geo-environments) for additional information on region usage and data storage as it relates to Microsoft Purview eDiscovery.

Customers that require performance optimization for Microsoft 365 should refer to [Network planning and performance tuning for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance?view=o365-worldwide) or contact their Support group.

Note

Customers who have purchased or used *Multi-Geo Capabilities* are not in scope for the [EU Data Boundary](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn), even if their *tenant* is listed as being in a country or region in the *EU* or *EFTA*. The [Flex routing](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-flex-routing#eligibility) setting will not be available in the Microsoft 365 admin center for customers who have purchased or used *Multi-Geo Capabilities*. Customers can check their *tenant's* country or region in the [Microsoft 365 admin center Data Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-card?view=o365-worldwide). Exchange Online, SharePoint, OneDrive, Microsoft Teams, and Microsoft Copilot and Copilot Chat are available for *Multi-Geo* configuration. For more information about data residency commitments, see [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide), [SharePoint and OneDrive](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide), [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide#data-residency-commitments-available), and [Microsoft 365 Copilot and Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide).

For a video introduction on *Microsoft 365 Multi-Geo*, see [SharePoint and OneDrive Multi-Geo to control where your data resides](https://www.youtube.com/watch?v=Do9U3JuROhk).

## Multi-Geo architecture

In a *Multi-Geo* environment, a Microsoft 365 *Tenant* consists of a [*Primary Provisioned Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(where a customer's Microsoft 365 subscription was originally provisioned\) *and* one or more [*Satellite Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) locations. In a *Multi-Geo* enabled *Tenant*, the information about *Geography* locations, groups, and user information, is mastered in [*Microsoft Entra ID*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions). Because a customer's *Tenant* information is mastered centrally and synchronized into each *Geography* location, sharing and experiences involving anyone from a customer's organization contain global awareness.

## Licensing

*Microsoft 365 Multi-Geo* is available as an add-on to the following Microsoft 365 subscription plans:

- Microsoft 365 F1, F3, E3, E5, or E7 \(including SKUs without Microsoft Teams\)
- Office 365 F3, E1, E3, or E5 \(including SKUs without Microsoft Teams\)
- Exchange Online Plan 1 or Plan 2
- OneDrive Plan 1 or Plan 2
- SharePoint Plan 1 or Plan 2
- Microsoft Teams Enterprise, EEA, or Essentials

Note

Subscriptions for small businesses and education don't currently qualify for the *Multi-Geo add-on*, even if they contain elements of the preceding list.

### Minimum Licensing

Enterprise Agreement customers must purchase a quantity of *Multi-Geo* licenses *equal to or greater than* 5% of their total eligible Microsoft 365 users. Similarly, CSP partners must purchase and assign a quantity of *Multi-Geo* licenses *equal to or greater than* 5% of their customers' total eligible Microsoft 365 users. For enterprise customers, user subscription licenses must be on the same Enterprise Agreement as the *Multi-Geo* Services licenses. Customers should contact their Microsoft account team for details.

*Multi-Geo Capabilities* in Microsoft 365 is a user-level add-on license. Customers need a license for each user that they want to host in a *Satellite Geography* location. Customers can add more licenses over time as they add users in *Satellite Geography* locations.

There are no *Multi-Geo* licenses specific to shared resources such as SharePoint Sites, Microsoft 365 Groups, Shared Mailboxes, or Microsoft Teams teams. If enough *Multi-Geo* user licenses have been acquired, then customers are eligible to use *Multi-Geo* with shared resources without limitation.

## Microsoft 365 Multi-Geo availability

*Microsoft 365 Multi-Geo* is currently offered in these *Geographies*:

| Microsoft 365 Geography | PreferredDataLocation \(PDL\) Value |
| :--- | :--- |
| South Korea, Japan, Singapore, Malaysia, Hong Kong Special Administrative Region | APC |
| Australia | AUS |
| Austria | AUT |
| Brazil | BRA |
| Canada | CAN |
| Chile | CHL |
| Denmark | DNK |
| France, Netherlands, Ireland, Norway, Switzerland, Austria, Finland, Sweden, Germany | EUR |
| France | FRA |
| Germany | DEU |
| India | IND |
| Indonesia | IDN |
| Israel | ISR |
| Italy | ITA |
| Japan | JPN |
| Korea | KOR |
| Malaysia | MYS |
| Mexico | MEX |
| New Zealand | NZL |
| Norway | NOR |
| Poland | POL |
| Qatar | QAT |
| South Africa | ZAF |
| Spain | ESP |
| Sweden | SWE |
| Switzerland | CHE |
| Taiwan | TWN |
| United Arab Emirates | ARE |
| United Kingdom | GBR |
| United States | NAM |

Note

To use a security filter for Italy, New Zealand, Spain, or Sweden in eDiscovery, you must have [premium features in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-settings-general) enabled.

To learn more about each *Geography*, including its datacenter locations, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Getting started

Whether you are a CSP partner managing your customer's Microsoft 365 subscriptions or an Enterprise Agreement customer managing your own subscriptions, you can follow these steps to get started with *Multi-Geo*:

1. Ensure that you purchase *Multi-Geo* for at least 5% of the total eligible users in your Microsoft 365 subscription. Remember that you need a license for each user you want to host in a *Satellite Geography* location.
2. Before you can start using *Microsoft 365 Multi-Geo*, Microsoft needs to configure your *Tenant* for *Multi-Geo* support. This one-time automatic configuration process is triggered after you order the *Multi-Geo Capabilities* in Microsoft 365 and the licenses show up in your *Tenant*. You'll receive service-specific notifications in the [Microsoft 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once the *Tenant* has completed the configuration process for each service, and then you may begin configuring and using your *Microsoft 365 Multi-Geo Capabilities*. The time required to configure a *Tenant* for *Multi-Geo* support varies from *Tenant* to *Tenant*, but most *Tenants* finish within a month after receipt of the feature licenses. Larger or more complex *Tenants* may require more time to complete the configuration process.
3. Read [Plan your multi-geo environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-multi-geo?view=o365-worldwide).
4. Learn about [administering a multi-geo environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/administering-a-multi-geo-environment?view=o365-worldwide) and [how your users will experience the environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-user-experience?view=o365-worldwide).
5. When you're ready to set up Microsoft 365 *Multi-Geo*, [configure your tenant for multi-geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-tenant-configuration?view=o365-worldwide).
6. [Set up search](https://learn.microsoft.com/en-us/microsoft-365/enterprise/configure-search-for-multi-geo?view=o365-worldwide).

Note

For information about the Microsoft 365 services that support *Multi-Geo*, see the [EXO](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide), [ODSP](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide), [Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide), and [Microsoft 365 Copilot and Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide) service *Data Residency* pages.

## See also

[Multi-Geo in Exchange Online and OneDrive](https://Aka.ms/GoMultiGeo)

[Multi-Geo Capabilities in OneDrive and SharePoint](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365?view=o365-worldwide)

[Multi-Geo Capabilities in Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/multi-geo-capabilities-in-exchange-online?view=o365-worldwide)

[Teams experience in a multi-geo environment](https://learn.microsoft.com/en-us/microsoftteams/teams-experience-o365odb-spo-multi-geo)
