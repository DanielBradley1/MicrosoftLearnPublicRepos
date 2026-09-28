<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-04-01 -->

# Overview and Definitions

## Definitions and Terms

In order to promote clarity in the capability descriptions on data residency functionality in this document, refer to these terms.

### **Table 1: Definitions and Terms**

| Term | Definition |
| :--- | :--- |
| Advanced Data Residency \(ADR\) | A Microsoft 365 add-on service that guarantees customer data residency for a defined set of services. See [Table 2](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-2-durable-commitments-on-data-location-by-microsoft-365-service) below. |
| Current Geography | *Current Geography* refers to the location where *Microsoft 365 Core* and *Expanded Service* \(ADR-scoped\) data is stored for the service. **Note:** In certain scenarios, *Current Geography* may differ from *Committed Geography*, such as during migration, due to ADR license validity, or at the time-of-service provisioning and activation relative to the availability of the *Local Region Geography*. For detailed information on these cases, visit [Learn More About the Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location?view=o365-worldwide). |
| Committed Geography | *Committed Geography* refers to the location where Microsoft will store in scope customer data at rest for certain Microsoft 365 services. This location is determined by the *Durable Commitments on Data Location* applicable to the *Tenant*. Visit [Available Data Residency by Country/Region](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-3-durable-commitments-on-data-location-by-geography) for more information. |
| Data Location Card | The *Data Location Card* is located within the "Data location" section of the Microsoft 365 admin center portal. Navigate to **Admin** > **Settings** > **Org settings** > **Organization profile** > **Data location**.  <br>  <br>For specific information on how to use the Data Location Card, refer to [Learn More about The Data Location Card](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location?view=o365-worldwide). |
| Default Geography | When a *Microsoft Entra ID Tenant* is created, a country/region is provided by the customer during the sign-up process. This country/region determines the *Default Geography* for all Microsoft 365 services. In some cases, not all services are able to provision in this single *Default Geography*. See *Microsoft 365 Service provisioning mapping* below for a description. |
| Durable Commitment on Data Location | One of the four existing methods to ensure that *Tenant* data location for a particular service does not change. These methods include *[European Union Data Boundary \(EUDB\)](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn#eu-data-boundary-countries-and-datacenter-locations)*, *[Privacy and Security Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all)*, *[Advanced Data Residency \(ADR\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-commitments?view=o365-worldwide)*, and *[Multi-Geo Capabilities](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)*. |
| Educational \(EDU\) Tenant | A *Tenant* that has an active Office 365 Education subscription \(i.e., A SKU\). |
| European Free Trade Association \(EFTA\) | A regional trade organization and free trade area consisting of four European states - Liechtenstein, Iceland, **Norway**, and **Switzerland**.  <br>  <br>**Note:** Microsoft 365 currently has data centers in the **bold** *EFTA* countries. |
| European Union \(EU\) | An international organization comprising 27 European countries. These countries are **Austria**, Belgium, Bulgaria, Croatia, Cyprus, Czechia, **Denmark**, Estonia, **Finland**, **France**, **Germany**, Greece, Hungary, **Ireland**, **Italy**, Latvia, Lithuania, Luxembourg, Malta, **Netherlands**, **Poland**, Portugal, Romania, Slovakia, Slovenia, **Spain**, and **Sweden**.  <br>  <br>**Note:** Microsoft 365 currently has data centers in the **bold** *European Union* countries. |
| European Union/EFTA | Data that is stored within the *European Union \(EU\)* and/or the *European Free Trade Association \(EFTA\)*. |
| European Union Data Boundary \(EUDB\) | *European Union Data Boundary* commitment. For more information, please see [Microsoft EU Data Boundary Overview - Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy/european-data-boundary-eudb). |
| Future Local Region Geography | Future planned data center regions: Greece, Kuwait, Saudi Arabia, Thailand |
| Geography | *Local Region Geography, Future Local Region Geography*, or *Macro Region Geography* |
| Legacy Move Program | This program, which is no longer active, was offered to *Tenants* who had a valid *Default Geography* which allowed the *Tenant* to migrate existing data at rest into a *Local Region Geography*. |
| Local Region Geography | Australia, Austria, Brazil, Canada, Chile, Denmark, France, Germany, India, Indonesia, Israel, Italy, Japan, Malaysia, Mexico, New Zealand, Norway, Poland, Qatar, South Africa, South Korea, Spain, Sweden, Switzerland, Taiwan, United Arab Emirates, United Kingdom |
| Macro Region Geography | Macro Region Geography 1 - Europe, Macro Region Geography 2 - Asia Pacific, Macro Region Geography 3 - Americas, Macro Region Geography 4 - European Union/EFTA |
| Macro Region Geography 1 - Europe | Data centers in Austria, Denmark, Finland, France, Germany, Ireland, Italy, Netherlands, Poland, Spain, Sweden  <br>  <br>**Note:** This term is referenced as "Europe" on the *Data Location Card*. |
| Macro Region Geography 2 - Asia Pacific | Data centers in Australia, Hong Kong Special Administrative Region, India, Indonesia, Japan, Malaysia, New Zealand, Singapore, South Korea |
| Macro Region Geography 3 - Americas | Data centers in Brazil, Canada, Chile, Mexico, and the United States \(USA\)  <br>  <br>**Note:** This term is referenced as "Americas" on the *Data Location Card*. |
| Macro Region Geography 4 - European Union/EFTA | Data centers in Austria, Denmark, Finland, France, Germany, Ireland, Italy, Netherlands, Poland, Spain, Sweden, Norway, and Switzerland.  <br>  <br>**Note:** This term is referenced as "European Union/EFTA" on the *Data Location Card*. |
| Microsoft Entra ID | Microsoft Entra ID is the new name for [Azure Active Directory](https://learn.microsoft.com/en-us/entra/fundamentals/new-name). |
| Microsoft 365 admin center Data Location | To see the *Primary Provisioned Geography* for Exchange Online, SharePoint, OneDrive, and Microsoft Teams, refer to the Microsoft 365 admin center by navigating to **Admin > Settings > Org settings > Organization profile > Data location**. |
| Microsoft 365 Core Services | Exchange Online, SharePoint and OneDrive, Microsoft Teams, Microsoft 365 Copilot and Microsoft 365 Copilot Chat |
| Microsoft 365 Expanded Services | Microsoft Defender for Office P1 and [the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/eop-about), Microsoft 365 web apps \(formerly known as "Office for the Web"\), Viva Connections, Microsoft Purview\* |
| Microsoft 365 Multi-Geo Capabilities | *Microsoft 365 Multi-Geo Capabilities* allows a single *Tenant* to store customer data-at-rest across multiple geographies rather than be limited to the single *Primary Provisioned Geography*. See the *[Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)* page for more detail. |
| Microsoft 365 Service provisioning country mapping | Refer to [data maps](https://aka.ms/datamaps) to learn where a given service provisions specified customer data, based on the *Tenant Default Geography.* |
| Microsoft 365 Service provisioning mapping | All Microsoft 365 services use the *Default Geography* to determine where a given *Tenant's* specified data will be provisioned and stored. |
| Preferred Data Location \(PDL\) | Used for *Tenants* with a *Multi-Geo* subscription. A property set by the Global Tenant Admin that indicates where the user or shared resource's data should be stored at-rest. See the *[Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide)* page for more detail. |
| Primary Provisioned Geography | A given Microsoft 365 service uses the *Tenant Default Geography* combined with the *Microsoft 365 Service provisioning country mapping* to determine which *Geography* to provision customer data into. |
| Privacy and Security Product Terms | For current language, refer to the [Privacy and Security Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) webpage. |
| Satellite Geography | If a customer subscribes to the *Multi-Geo* service, then they can set policy at a user level to store in scope customer data in other *Geographies* outside of the *Tenant Primary Provisioned Geography*. |
| Services | Often used to refer to a Microsoft 365 service such as but not limited to Exchange Online, SharePoint, OneDrive, Microsoft Teams, etc. |
| Tenant | A *Tenant* represents an organization in *Microsoft Entra ID*. It's a reserved Microsoft Entra service instance that an organization receives and owns when it signs up for a Microsoft cloud service such as Azure or Microsoft 365. Each *Microsoft Entra ID Tenant* is distinct and separate from other *Microsoft Entra ID Tenants*. |

Note

\*The [Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide) services covered as part of the *Advanced Data Residency commitment* \(as of February 2026\) include [Data Loss Prevention](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---data-loss-prevention-dlp), [Information Barriers](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---information-barriers), [Information Protection \(MIP\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---information-protection-mip), [Audit \(Standard\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---audit-standard), [Audit \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---audit-premium), and [Data Lifecycle Management \(DLM\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---data-lifecycle-management-dlm). Additional Microsoft Purview services are not currently supported.

## Overview of Data Residency

Microsoft 365 Cloud services run on our data centers around the world and provide services to customers around the world. Customer data might be stored in multiple data centers. Data residency refers to the geographic location where customer data is stored at rest. Data residency is important for government, public sector, education and regulated commercial entities to help ensure protection of personal and/or sensitive information. In many countries/regions, customers are expected to comply with laws, regulations or industry standards that explicitly govern the location of data storage.

Microsoft makes decisions on where to persistently store customer data based on two factors:

1. The *Default Geography* of the *Tenant*
2. Available *Geographies* for a given service

### *Default Geography* of the *Microsoft Entra ID Tenant*

When a customer creates a new *Microsoft Entra ID Tenant*, the customer enters a country/region during the creation process. This country/region is what defines the *Default Geography* for the *Tenant*. There are multiple paths to creating *Tenants*. They can be created through Microsoft Entra ID forms, they can be created when trying out new Microsoft 365 services \(trials\), etc. Once a *Tenant* is created, the *Default Geography* can't be changed.

### Available *Geographies* for a given service

Microsoft 365 services aren't deployed to all Microsoft data centers globally. The larger services, like Exchange Online, SharePoint, OneDrive, and Microsoft Teams are universally deployed to all *Geographies*. Other services make decisions on where to deploy their services based on the number of customers, regional affiliations, and software architectures. When a customer first uses a service in this category, the provisioning logic uses the *Default Geography* and the supported *Geographies* to determine where to provision a given customer.

Over time, a particular service may deploy their software to additional *Geographies*, so the provisioning locations for new customers can change over time. This doesn't necessarily cause customer data to move to a new *Geography*.

You can use the *Data Location Card* via the Microsoft 365 admin center to understand where your data for a given service is stored. As a Global Tenant Admin, you can find the actual data location by navigating to **Admin > Settings > Org settings > Organization profile > Data location**. Currently, data location details are available for Exchange Online, SharePoint, OneDrive, Microsoft Teams, Microsoft 365 Copilot, [the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/eop-about), and Viva Connections. Additional data location details can be found on the [Data Maps page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide).

Note

[Microsoft Defender for Office P1](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide), [Microsoft Purview \(select services\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide), and [Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide) are covered by [Durable Commitments on Data Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#durable-commitments-on-data-location) but not currently displayed in the *Data Location Card*. Refer to [Where your Microsoft 365 customer data is stored](https://learn.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide) for more information.

Some examples:

**Example 1:** For a *Commercial Tenant* with a *Default Geography* of "France" that has a new subscription that includes Exchange Online, SharePoint, OneDrive, and Microsoft Teams, the customer data for those services will be provisioned into the French *Local Region Geography*. Why? Because those services are deployed into the French data centers and the *Tenant* has "France" as its *Default Geography*.

**Example 2:** For a *Commercial Tenant* with a *Default Geography* of "Belgium" that has a new subscription that includes Exchange Online, SharePoint, OneDrive, and Microsoft Teams, the customer data for those services will be provisioned into the *Macro Region Geography 4 - European Union/EFTA*. Why? Because there are no Microsoft 365 data centers in Belgium and the closest compliant *Geography* is *Macro Region Geography 4 - European Union/EFTA*. With this, *Commercial Tenants* with a *Default Geography* of "Belgium" are eligible to reside within the [European Union Data Boundary \(EUDB\)](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn#eu-data-boundary-countries-and-datacenter-locations).

**Example 3:** For a *Commercial Tenant* with a *Default Geography* of "Japan" that has a new subscription that includes Microsoft Forms, the customer data for Forms will be provisioned into *Macro Region Geography 3 - Americas*. Why? Because Forms is only deployed in *Macro Region Geography 3 - Americas* and *Macro Region Geography 4 - European Union/EFTA* \(*European Union/EFTA Tenants* only\).

**Example 4a:** For a *Commercial Tenant* with a *Default Geography* of "Sweden" that has a new subscription that includes Microsoft Viva Engage, the customer data for Viva Engage will be provisioned into *Macro Region Geography 4 - European Union/EFTA*. Why? Because Viva Engage is deployed in *Macro Region Geography 4 - European Union/EFTA* and Swedish *Tenants* are best served out of that *Geography*.

**Example 4b:** For a *Commercial Tenant* with a *Default Geography* of "Sweden" that has a subscription that includes Microsoft Viva Engage from before Viva Engage was deployed to *Macro Region Geography 4 - European Union/EFTA*, the customer data for Viva Engage will be located in *Macro Region Geography 3 - Americas*. Why? Because, at that time, Viva Engage only had a single deployment for all customers in *Macro Region Geography 3 - Americas*.

### Migrations/Moves

Once a Microsoft 365 service provisions a *Tenant* into a particular *Geography*, there are three ways that the customer's in scope customer data could move to another *Geography*:

1. If a customer *Tenant* has a *Default Geography* that is also a *Local Region Geography* and has a subscription to the *Advanced Data Residency* service add-on, then the *Tenant's* in scope customer data for the *Microsoft 365 Core Services* and *Microsoft 365 Expanded Services* will be migrated from its *Current Geography* to the relevant *Local Region Geography* that corresponds to the *Tenant's Default Geography*.
2. If a *Tenant* subscribes to the *Multi-Geo* service, then the Global Tenant Admin can assign user's in scope customer data for Exchange Online, SharePoint, OneDrive, Microsoft Teams, and Microsoft 365 Copilot to *Satellite Geographies*.
3. In the event that a *Tenant* does not have a *Durable Commitment on Data location*, the *Tenant's* in scope customer data is not committed to reside in any particular data center. In these cases, Microsoft will store the *Tenant's* in scope customer data in a location that enables it to deliver services effectively to the customer and that data storage location is subject to change without notice.

### Durable Commitments on Data Location

There are three methods for ensuring that the *Tenant* data location for a particular service doesn't change.

1. *Product Terms*: See the [Product Terms Data Residency page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms-dr?view=o365-worldwide) for specific details.
2. *Multi-Geo* subscription: allows customers to assign data location for Exchange Online, SharePoint, OneDrive, Microsoft Teams, and Microsoft 365 Copilot and Microsoft 365 Copilot Chat to any supported *Geography*. For more information, see [Multi Geo Data Residency](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide).
3. *Advanced Data Residency* subscription: provides data residency commitments for a *Core* and *Expanded* set of Microsoft 365 services in *Local Region Geographies*. For more information, see the [Advanced Data Residency page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide).

#### **Table 2: Durable Commitments on Data Location by Microsoft 365 Service**

| Service Name | Product Terms | Multi-Geo | ADR |
| :--- | :--- | :--- | :--- |
| Exchange Online | X<sup>1</sup> | X<sup>2</sup> | X<sup>3</sup> |
| SharePoint / OneDrive | X<sup>1</sup> | X<sup>2</sup> | X<sup>3</sup> |
| Microsoft Teams | X<sup>1</sup> | X<sup>2</sup> | X<sup>3</sup> |
| Microsoft 365 Copilot and Microsoft 365 Copilot Chat | X<sup>1</sup> | X<sup>2</sup> | X<sup>3</sup> |
| Microsoft Defender for Office P1 | - | - | X<sup>3</sup> |
| Microsoft 365 web apps \(formerly known as "Office for the Web"\) | - | - | X<sup>3</sup> |
| Viva Connections | - | - | X<sup>3</sup> |
| Microsoft Purview | - | - | X<sup>3</sup> |

1. Only available in the following countries/regions: Australia, Brazil, Canada, France, Germany, India, Japan, Qatar, South Korea, Norway, South Africa, Sweden, Switzerland, United Arab Emirates, United Kingdom, European Union and the United States.
2. Available in *Local Region Geography*, *Future Local Region Geography* \(when the future data center is launched\) and *Regional Geography countries/regions*.
3. Only available for *Local Region Geography* and *Future Local Region Geography* \(when the future data center is launched\) countries/regions.

Note

See the [Service Data Residency Capabilities section](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide) for more details on these topics.

#### **Table 3: Durable Commitments on Data Location by Geography**

| Geography | Exchange Online | SharePoint, OneDrive | Teams | Microsoft 365 Copilot and Microsoft 365 Copilot Chat | MDO P1 | Microsoft 365 web apps | Viva Connections | Purview |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Australia | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Austria | M-A | M-A | M-A | M-A | A | A | A | A |
| Brazil | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Canada | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Chile | M-A | M-A | M-A | M-A | A | A | A | A |
| Denmark | M-A | M-A | M-A | M-A | A | A | A | A |
| European Union | P-M | P-M | P-M | P-M | - | - | - | - |
| France | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Germany | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| India | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Indonesia | M-A | M-A | M-A | M-A | A | A | A | A |
| Israel | M-A | M-A | M-A | M-A | A | A | A | A |
| Italy | M-A | M-A | M-A | M-A | A | A | A | A |
| Japan | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Malaysia | M-A | M-A | M-A | M-A | A | A | A | A |
| Mexico | M-A | M-A | M-A | M-A | A | A | A | A |
| New Zealand | M-A | M-A | M-A | M-A | A | A | A | A |
| Norway | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Poland | M-A | M-A | M-A | M-A | A | A | A | A |
| Qatar | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| South Africa | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| South Korea | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Spain | M-A | M-A | M-A | M-A | A | A | A | A |
| Sweden | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Switzerland | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| Taiwan | M-A | M-A | M-A | M-A | A | A | A | A |
| United Arab Emirates | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| United Kingdom | P-M-A | P-M-A | P-M-A | P-M-A | A | A | A | A |
| United States | P-M | P-M | P-M | P-M | - | - | - | - |

P: Product Terms Data Residency  
M: Multi-Geo Data Residency  
A: Advanced Data Residency

### Geographies and associated data center city locations

The following table displays the various *Geographies* and the corresponding data center location\(s\) where Microsoft 365 customers can store data at rest.

Note

For security and compliance reasons, Microsoft does not disclose the exact location of its data centers. The table below provides detail only to the metropolitan level to support transparency around data residency.

#### **Table 4: Durable Commitments on Data Location by Data Center Location**

| Geography | Data Center Location\(s\) |
| --- | --- |
| Americas | Brazil \(Campinas, Rio\), Canada \(Quebec City, Toronto\), Chile \(Santiago\), Mexico \(Queretaro\), United States \(Boydton, Cheyenne, Chicago, Des Moines, Quincy, San Antonio, Santa Clara, San Jose\) |
| Asia Pacific | Australia \(Sydney, Melbourne\), India \(Chennai, Mumbai, Pune\), Indonesia \(Jakarta\), Japan \(Osaka, Tokyo\), Malaysia \(Kuala Lumpur\), Singapore, South Korea \(Busan, Seoul\), New Zealand \(Auckland\) |
| Australia | Melbourne, Sydney |
| Austria | Vienna |
| Brazil | Campinas, Rio |
| Canada | Quebec City, Toronto |
| Chile | Santiago |
| Denmark | Copenhagen |
| Europe | Austria \(Vienna\), Denmark \(Copenhagen\), Finland \(Helsinki\), France \(Marseille, Paris\), Germany \(Berlin, Frankfurt\), Ireland \(Dublin\), Italy \(Milan\), Netherlands \(Amsterdam\), Poland \(Warsaw\), Spain \(Madrid\), Sweden \(Gävle, Sandviken, Staffanstorp\) |
| European Union/EFTA | Austria \(Vienna\), Denmark \(Copenhagen\), Finland \(Helsinki\), France \(Marseille, Paris\), Germany \(Berlin, Frankfurt\), Ireland \(Dublin\), Italy \(Milan\), Netherlands \(Amsterdam\), Norway \(Oslo, Stavanger\), Poland \(Warsaw\), Spain \(Madrid\), Sweden \(Gävle, Sandviken, Staffanstorp\), Switzerland \(Geneva, Zurich\) |
| France | Marseille, Paris |
| Germany | Berlin, Frankfurt |
| India | Chennai, Mumbai, Pune |
| Indonesia | Jakarta |
| Israel | Tel Aviv |
| Italy | Milan |
| Japan | Osaka, Tokyo |
| Malaysia | Kuala Lumpur |
| Mexico | Queretaro |
| New Zealand | Auckland |
| Norway | Oslo, Stavanger |
| Poland | Warsaw |
| Qatar | Doha |
| Singapore | Singapore |
| South Africa | Cape Town, Johannesburg |
| South Korea | Busan, Seoul |
| Spain | Madrid |
| Sweden | Gävle, Sandviken, Staffanstorp |
| Switzerland | Geneva, Zurich |
| Taiwan | Taipei |
| United Arab Emirates | Abu Dhabi, Dubai |
| United Kingdom | Cardiff, Durham, London |
| United States | Boydton, Cheyenne, Chicago, Des Moines, Quincy, San Antonio, Santa Clara, San Jose |

### FAQ

#### How does Microsoft define data?

<details>
<summary>Select to expand</summary>

Review our [definitions for different types of customer data](https://go.microsoft.com/fwlink/p/?linkid=864390) on the Microsoft Trust Center. In the [Privacy & Security Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all), Microsoft makes contractual commitments regarding customer data/your *Tenant* and user data. We refer to customer data as the customer data that is committed to be stored at rest only within a *Tenant's* region according to the [Privacy & Security Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all).
</details>

#### Where are the exact addresses of the data centers?

<details>
<summary>Select to expand</summary>

Microsoft doesn't disclose the exact addresses of its data centers. We established this policy to help secure our data center facilities. However, we do list city locations. See [Table 4: Durable Commitments on Data Location by Data Center Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-4-durable-commitments-on-data-location-by-data-center-location) on the Overview and Definitions page to learn more.
</details>

#### Does the location of your customer data have a direct impact on your end users' experience?

<details>
<summary>Select to expand</summary>

The performance of Microsoft 365 isn't simply proportional to a *Tenant* user's distance to data center locations. Microsoft's continued investments in its global cloud network, global cloud infrastructure, and the Microsoft 365 services architecture help provide users with a singular, consistent experience independent of where customer data is stored at rest. If your users are experiencing performance issues, you should troubleshoot those in depth. Microsoft has published guidance for Microsoft 365 customers to plan for and optimize end-user performance on the [Office Support web site](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance?view=o365-worldwide).
</details>

#### How does Microsoft help me comply with my national, regional, and industry-specific regulations?

<details>
<summary>Select to expand</summary>

To help a *Tenant* comply with national, regional, and industry-specific requirements governing the collection and use of individuals' data, Microsoft 365 offers the most comprehensive set of compliance offerings of any global cloud productivity provider. Review [our compliance offerings](https://learn.microsoft.com/en-us/compliance/regulatory/offering-home) and more details in the [Microsoft Purview](https://go.microsoft.com/fwlink/p/?linkid=862317) section on the Microsoft Trust Center. Also, certain Microsoft 365 plans offer further compliance solutions to help a *Tenant* manage their data, comply with legal and regulatory requirements, and monitor actions taken on their data.
</details>

#### Who can access your data and according to what rules?

<details>
<summary>Click to expand</summary>

Microsoft implements strong measures to help protect a *Tenant's* customer data from inappropriate access or use by unauthorized persons. This includes restricting access by Microsoft personnel and subcontractors, and carefully defining requirements for responding to government requests for customer data. However, you can access your *Tenant's* customer data at any time and for any reason. More details are available on the [Microsoft Trust Center](https://go.microsoft.com/fwlink/p/?linkid=864392).
</details>

#### Does Microsoft access your data?

<details>
<summary>Select to expand</summary>

Microsoft automates most Microsoft 365 operations while intentionally limiting its own access to customer data. This helps us manage Microsoft 365 at scale and address the risks of internal threats to customer data. By default, Microsoft engineers have no standing administrative privileges and no standing access to customer data in Microsoft 365. A Microsoft engineer may have limited and logged access to customer data for a limited amount of time, but only when necessary for normal service operations and only when approved by a member of senior management at Microsoft \(and, for customers who are licensed for the Customer Lockbox feature, by the customer\).
</details>

#### How does Microsoft secure your data?

<details>
<summary>Select to expand</summary>

Microsoft has robust policies, controls, and systems built into Microsoft 365 to help keep your information safe. Review the [Microsoft 365 security section](https://go.microsoft.com/fwlink/p/?linkid=864393) on the Microsoft Trust Center to learn more.
</details>

#### Does Microsoft 365 encrypt your data?

<details>
<summary>Select to expand</summary>

Microsoft 365 uses service-side technologies that encrypt customer data at rest and in transit. For customer data at rest, Microsoft 365 uses volume-level and file-level encryption. For customer data in transit, Microsoft 365 uses multiple encryption technologies for communications between data centers and between clients and servers, such as Transport Layer Security \(TLS\) and Internet Protocol Security \(IPsec\). Microsoft 365 also includes customer-managed encryption features.
</details>

#### Where can I find data residency information for Microsoft Azure?

<details>
<summary>Select to expand</summary>

Review the [Product availability by region](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/table) page to find data residency information for Microsoft Azure.
</details>

#### Why do I see my Microsoft 365 service requests for my data at rest connecting to servers in countries outside of my region?

<details>
<summary>Click to expand</summary>

On occasion, a customer request may be handled by servers in a different region than the location where a *Tenant's* customer data is stored at rest. This may happen where network routing decisions choose a different server for the request processing, but in these cases such *Tenant's* customer data is not moved to a new at rest location.
</details>
