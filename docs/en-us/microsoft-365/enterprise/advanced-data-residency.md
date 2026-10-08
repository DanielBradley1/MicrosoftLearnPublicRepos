<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-18 -->

# Advanced Data Residency: Overview and requirements

The [*Microsoft 365 Advanced Data Residency add-on*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\) provides eligible customers with expanded coverage of Microsoft 365 services, committed [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for [*Local Region Geographies*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions), and prioritized [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) migration services. With *ADR*, enterprise customers can address *Data Residency* compliance and *Tenant* location requirements.

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Benefits of ADR

*ADR* provides the following benefits for Microsoft 365:

- **Local Region Geography commitment**: [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) stored at rest within your specific country or region for [eligible *Tenants*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements). For many customers, *ADR* is the primary way to achieve a [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for their *Local Region Geography*.
- **Expanded service coverage**: For customers already covered by [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/MCA), *ADR* extends *Data Residency* commitments to additional Microsoft 365 services beyond [*Microsoft 365 Core Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).
- **Prioritized migration**: [Migration services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide#initiate-migration) to move existing data to your *Local Region Geography*.

## Microsoft 365 Services covered by ADR

*ADR* includes *Data Residency* commitments for the following Microsoft 365 services:

### Table 3.1: ADR service coverage for Microsoft 365

| Service category | Services included |
| :--- | :--- |
| **Core services** | Exchange Online, SharePoint, OneDrive, Microsoft Teams, Microsoft 365 Copilot, Microsoft 365 Copilot Chat |
| **Security** | Microsoft Defender for Office P1, Exchange Online Protection |
| **Productivity** | Office for the web, Viva Connections |
| **Compliance** | Microsoft Purview \(select services\)\* |

\*Microsoft Purview services covered by *ADR* include:

- Audit \(Standard and Premium\)
- Data Lifecycle Management
- Data Loss Prevention
- Information Barriers
- Information Protection

For detailed information about what *Customer Data* is stored for each service, see [ADR data commitments](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide).

## Eligibility requirements

To be eligible for *ADR*, customers must meet the following requirements.

### *Tenant's* Default Geography

The *Tenant's* [*Default Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) **must be** in one of the following *Local Region Geographies*:

Australia, Austria, Brazil, Canada, Chile, Denmark, France, Germany, India, Indonesia, Israel, Italy, Japan, Malaysia, Mexico, New Zealand, Norway, Poland, Qatar, South Africa, South Korea, Spain, Sweden, Switzerland, Taiwan, United Arab Emirates, and United Kingdom.

Important

The European Union isn't available as a single *ADR* [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions). Customers in countries or regions in the EU should evaluate whether [Product Terms](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/MCA) or [EUDB](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn) commitments meet their requirements.

### Qualifying subscriptions

Customers must have licenses for one or more of the following products:

**Group 1 - Microsoft 365 Enterprise**

- Microsoft 365 F1, F3, E3, E5, or E7 \(including SKUs without Microsoft Teams\)
- Microsoft 365 Apps for Enterprise

**Group 2 - Office 365 Enterprise**

- Office 365 F3, E1, E3, or E5 \(including SKUs without Microsoft Teams\)

**Group 3 - Microsoft 365 Business**

- Microsoft 365 Business Basic, Business Standard, Business Premium \(including SKUs without Microsoft Teams\)

**Group 4 - Microsoft Teams Standalone**

- Microsoft Teams Enterprise, Teams EEA, Teams Essentials \(paid licenses\)

**Group 5 - Exchange, OneDrive, and SharePoint Plans**

- Exchange Online Plan 1, Plan 2
- OneDrive Plan 1, Plan 2
- SharePoint Plan 1, Plan 2

**Group 6 - Microsoft 365 Education**

- Microsoft 365 A3, A5
- Office 365 A1, A3, A5 \(paid licenses\)

Note

*ADR for Education* \(Group 6\) is available only to Volume Licensing / EES \(Microsoft Enrollment for Education Solutions\) customers. Contact your Microsoft account representative for details on obtaining an *ADR* Education SKU.

### License coverage

Customers must cover 100% of paid licenses in the *Tenant* with *ADR* add-on licenses. For detailed information about coverage requirements, license calculations, mixed subscriptions, and maintaining compliance, see [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide).

## Next steps

- [ADR data commitments](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide)
- **Licensing**

  - [Prerequisites and eligibility](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-prerequisites?view=o365-worldwide)
  - [License management](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide)

- **Migration**

  - [Initiate migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide)
  - [Status and notifications](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-migration-status?view=o365-worldwide)

- **User Experience**

  - [User experience during migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-user-experience?view=o365-worldwide)

- [Compare Data Residency offerings](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-compare-offerings?view=o365-worldwide)
