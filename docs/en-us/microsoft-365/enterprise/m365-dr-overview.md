<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-04-01 -->

# What is Microsoft 365 Data Residency?

[*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) refers to the geographic location where an organization's data is stored or processed. For Microsoft 365, *Data Residency* defines where your [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is kept within Microsoft's global datacenter infrastructure.

Organizations increasingly need to know—and often control—where their data resides. Microsoft 365 offers several options to help meet these requirements.

For definitions of terms used in this article, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Data at rest

[*Data at Rest*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) refers to data that is stored persistently in a specific location, such as in databases, file systems, or cloud storage. This is distinct from data that is actively moving across a network or being processed.

For the Microsoft 365 services covered by this article, Microsoft determines where to store your *Data at Rest* based on two primary factors:

1. **The [*Default Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) of your Microsoft 365 [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions)** - When your organization creates a Microsoft 365 *Tenant*, a country or region is provided during sign-up. This country or region establishes the *Default Geography* for Microsoft 365 services.
2. **Available [*Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for each service** - Microsoft 365 services are deployed across datacenters worldwide, but not all services are available in every location. The provisioning logic uses the *Default Geography* combined with service availability to determine where data is stored.

Note

This article describes *Data Residency* for Microsoft 365 services. Dynamics 365 and Power Platform have separate data residency behavior and documentation. For more information, see [Microsoft Dynamics 365 and Power Platform data residency documentation](https://learn.microsoft.com/en-us/dynamics365/get-started/availability).

## Data in processing

Data in processing refers to data that is actively being used, computed, or transformed by a service—as opposed to data sitting in storage. While *Data at Rest* focuses on where data is stored, data in processing addresses where computational operations occur.

For example, Microsoft 365 Copilot processes prompts and generates responses. With the appropriate configuration, this processing occurs within the same geographic boundary as your stored data, helping organizations meet data handling requirements that extend beyond storage.

Note

Detailed documentation for data in processing is coming soon.

## Why data residency matters

Organizations consider *Data Residency* for several reasons:

- **Regulatory compliance** - Many industries and jurisdictions have regulations that require data to be stored within specific geographic boundaries. Examples include GDPR in the European Union, data localization laws in certain countries or regions, and sector-specific regulations in healthcare and finance.
- **Data sovereignty** - Governments and public sector organizations often require that citizen data remain within national borders, subject to local laws and oversight.
- **Organizational policy** - Some organizations establish internal policies about data location based on risk management, customer commitments, or business strategy.
- **Customer and stakeholder expectations** - End customers and business partners may require assurances about where their data is stored as part of contractual agreements.

Microsoft 365 provides multiple options to address these considerations, ranging from default commitments included with your subscription to add-on services that provide expanded geographic control.

## Microsoft 365 Durable Commitments on Data Location

There are three methods for ensuring that the *Tenant* data location for a particular Microsoft 365 service doesn't change.

1. [*Product Terms*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions): See the [Product Terms Data Residency page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms?view=o365-worldwide) for specific details.
2. [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) subscription: allows customers to assign data location for Exchange Online, SharePoint, OneDrive, Microsoft Teams, and Microsoft 365 Copilot and Microsoft 365 Copilot Chat to any supported *Geography*. For specific commitments, see [Multi-Geo Capabilities data commitments](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo-commitments?view=o365-worldwide).
3. [*Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) subscription: provides *Data Residency* commitments for certain *Microsoft 365 Core Services* and *Microsoft 365 Expanded Services* in [*Local Region Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions). Refer to [Advanced Data Residency: Data commitments](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide) for specific eligibility and commitments.

For detailed comparisons, see [Service coverage by offering](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide#microsoft-365-service-coverage-comparison) and [Data residency commitments by Geography](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide#microsoft-365-data-residency-commitments-by-geography). For datacenter city locations, see [Microsoft 365 datacenter locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-datacenter-locations?view=o365-worldwide).

## General data and privacy FAQ

The following questions cover broader data, privacy, and security topics. For more information about these topics, see the [Microsoft Trust Center](https://www.microsoft.com/trust-center). For data location–specific questions, see [Data Location FAQ](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location-faq?view=o365-worldwide).

### How does Microsoft define data?

<details>
<summary>Select to expand</summary>

Review our [definitions for different types of customer data](https://go.microsoft.com/fwlink/p/?linkid=864390) on the Microsoft Trust Center. In the [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all), Microsoft makes contractual commitments regarding *Customer Data*/your *Tenant* and user data. We refer to *Customer Data* as the *Customer Data* that is committed to be stored at rest only within a *Tenant's* region according to the [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all).
</details>

### Does the location of your customer data have a direct impact on your end users' experience?

<details>
<summary>Select to expand</summary>

The performance of Microsoft 365 isn't simply proportional to a *Tenant* user's distance to data center locations. Microsoft's continued investments in its global cloud network, global cloud infrastructure, and the Microsoft 365 services architecture help provide users with a singular, consistent experience independent of where *Customer Data* is stored at rest. If your users are experiencing performance issues, you should troubleshoot those in depth. Microsoft has published guidance for Microsoft 365 customers to plan for and optimize end-user performance on the [Office Support web site](https://learn.microsoft.com/en-us/microsoft-365/enterprise/network-planning-and-performance?view=o365-worldwide).
</details>

### How does Microsoft help me comply with my national, regional, and industry-specific regulations?

<details>
<summary>Select to expand</summary>

To help a *Tenant* comply with national, regional, and industry-specific requirements governing the collection and use of individuals' data, Microsoft 365 offers the most comprehensive set of compliance offerings of any global cloud productivity provider. Review [our compliance offerings](https://learn.microsoft.com/en-us/compliance/regulatory/offering-home) and more details in the [Microsoft Purview](https://go.microsoft.com/fwlink/p/?linkid=862317) section on the Microsoft Trust Center. Also, certain Microsoft 365 plans offer further compliance solutions to help a *Tenant* manage their data, comply with legal and regulatory requirements, and monitor actions taken on their data.
</details>

### Who can access your data and according to what rules?

<details>
<summary>Click to expand</summary>

Microsoft implements strong measures to help protect a *Tenant's* *Customer Data* from inappropriate access or use by unauthorized persons. This includes restricting access by Microsoft personnel and subcontractors, and carefully defining requirements for responding to government requests for *Customer Data*. However, you can access your *Tenant's* *Customer Data* at any time and for any reason. More details are available on the [Microsoft Trust Center](https://go.microsoft.com/fwlink/p/?linkid=864392).
</details>

### Does Microsoft access your data?

<details>
<summary>Select to expand</summary>

Microsoft automates most Microsoft 365 operations while intentionally limiting its own access to *Customer Data*. This helps us manage Microsoft 365 at scale and address the risks of internal threats to *Customer Data*. By default, Microsoft engineers have no standing administrative privileges and no standing access to *Customer Data* in Microsoft 365. A Microsoft engineer may have limited and logged access to *Customer Data* for a limited amount of time, but only when necessary for normal service operations and only when approved by a member of senior management at Microsoft \(and, for customers who are licensed for the Customer Lockbox feature, by the customer\).
</details>

### How does Microsoft secure your data?

<details>
<summary>Select to expand</summary>

Microsoft has robust policies, controls, and systems built into Microsoft 365 to help keep your information safe. Review the [Microsoft 365 security section](https://go.microsoft.com/fwlink/p/?linkid=864393) on the Microsoft Trust Center to learn more.
</details>

### Does Microsoft 365 encrypt your data?

<details>
<summary>Select to expand</summary>

Microsoft 365 uses service-side technologies that encrypt customer *Data at Rest* and in transit. For customer *Data at Rest*, Microsoft 365 uses volume-level and file-level encryption. For *Customer Data* in transit, Microsoft 365 uses multiple encryption technologies for communications between data centers and between clients and servers, such as Transport Layer Security \(TLS\) and Internet Protocol Security \(IPsec\). Microsoft 365 also includes customer-managed encryption features.
</details>

### Why do I see my Microsoft 365 service requests for my data at rest connecting to servers in countries or regions outside of my region?

<details>
<summary>Click to expand</summary>

On occasion, a customer request may be handled by servers in a different region than the location where a *Tenant's* *Customer Data* is stored at rest. This may happen where network routing decisions choose a different server for the request processing, but in these cases such *Tenant's* *Customer Data* is not moved to a new at rest location.
</details>

## Next steps

- [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide)
- [Compare Microsoft 365 data residency offerings](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide)
- [Choose the right solution](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-choose-solution?view=o365-worldwide)
