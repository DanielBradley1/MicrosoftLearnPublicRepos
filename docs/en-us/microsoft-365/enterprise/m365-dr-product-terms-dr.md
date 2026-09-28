<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-product-terms-dr?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Overview of Product Terms Data Residency

Note

*This document is intended to provide a general overview of the *Microsoft Product Terms* \("*Product Terms*"\) in relation to Microsoft 365 data residency commitments. In the event of a discrepancy, the official terms listed on the [*Product Terms* webpage](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) shall prevail.*

The Privacy and Security Terms included with the *Product Terms* provide a data residency commitment under the conditions described below.

## Product Terms Data Residency Commitments for Commercial Customers

**Terms apply to**: *Tenants* with a *Default Geography*, regardless of date of initial provisioning, of Australia, Brazil, Canada, France, Germany, India, Japan, Norway, Qatar, South Africa, South Korea, Sweden, Switzerland, the United Kingdom, the United Arab Emirates, United States, and the European Union.

**Commitments Period**: The commitment period is equal to the length of the customer's agreement with Microsoft. Typically, this period is 1-3 years.

[*Microsoft 365 Core Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-1-definitions-and-terms): The services covered by the commitment excerpted below are listed in the following table:

| Service | Date Added to Privacy and Security Terms |
| :--- | :--- |
| Exchange Online | Always Included |
| SharePoint | Always Included |
| OneDrive for Business | Always Included |
| Microsoft Teams | Added November 1, 2022 |
| Microsoft 365 Copilot | Added March 1, 2024 |
| Microsoft 365 Copilot Chat | Added September 1, 2025 |

The language at time of writing this article is:

- **Office 365 Services**: If Customer provisions its tenant in Australia, Brazil, Canada, the European Union, France, Germany, India, Japan, Norway, Qatar, South Africa, South Korea, Sweden, Switzerland, the United Kingdom, the United Arab Emirates, or the United States, Microsoft will store the following Customer Data at rest only within that Geo: \(1\) Exchange Online mailbox content \(e-mail body, calendar entries, and the content of e-mail attachments\), \(2\) SharePoint Online site content and the files stored within that site, \(3\) files uploaded to OneDrive \(work/school\), \(4\) Microsoft Teams chat messages \(including private messages, channel messages, meeting messages and images used in chats\), and for customers using Microsoft Stream \(Classic\) \(on SharePoint\) meeting recordings, and \(5\) any stored content of interactions with Microsoft 365 Copilot or Microsoft 365 Copilot Chat to the extent not included in the preceding commitments or subject to [Data Residency for Microsoft 365 Copilot and Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot?view=o365-worldwide). If Customer purchases an Advanced Data Residency subscription, then Microsoft will store certain Customer Data at rest in the applicable Geo in accordance with this section and the "Advanced Data Residency Commitments" section of the product documentation at [https://aka.ms/adroverview](https://aka.ms/adroverview).
- For current language, refer to the "Privacy and Security Terms" tab of the [*Product Terms* webpage](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) and view the section titled "Location of Customer Data at Rest for Core Online Services."

For more data residency capabilities, refer to the [*Multi-Geo* service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide) and the [*Advanced Data Residency* service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide).

## Data Residency Setting for Commercial Customers in Select Geographies

Important

*This setting is only available to eligible commercial Tenants with a Default Geography of France, Germany, Norway, Sweden, or Switzerland. Tenants with a paid data residency offering — Advanced Data Residency \(ADR\), Advanced Data Residency for Education \(ADR-E\), or Multi-Geo Capabilities — don't see this setting, because their data residency is already governed by that offering. Tenants that qualify for data residency based on Product Terms but didn't opt into the Legacy Move Program may not be eligible. If your organization isn't eligible, no action is needed and your current commitment is unchanged.*

We're adding a new data residency setting in the Microsoft 365 admin center called "**Store Microsoft 365 customer data in-country**". This setting lets you choose whether Microsoft keeps your *Microsoft 365 Core Services* data at rest in your Product Terms-associated *Geography*, or allows that data to be stored and moved outside of it. The setting is located on the *Data Location Card*, within the "Data location" section of the Microsoft 365 admin center portal. Navigate to **Admin** > **Settings** > **Org settings** > **Organization profile** > **Data location** > **Commitments**.

The setting applies only to the *Microsoft 365 Core Services*: Exchange Online, SharePoint, OneDrive for Business, Microsoft Teams, and Microsoft 365 Copilot and Microsoft 365 Copilot Chat.

Note

*This setting doesn't affect any European Union Data Boundary \(EUDB\) commitment. If your organization has an EUDB commitment, it remains in place regardless of how this setting is configured.*

## What the "Store Microsoft 365 customer data in-country" Does

| Setting | What it means |
| :--- | :--- |
| On | Microsoft keeps your *Microsoft 365 Core Services* data at rest in your Product Terms-associated *Geography*. |
| Off | Microsoft may store your *Microsoft 365 Core Services* data regionally within the *EU Data Boundary*. |

Turning the setting Off removes the in-country data-at-rest commitment for these services, and your *Committed Geography* changes to reflect that the product term storage preference is not currently active.

This setting is Off by default for eligible *Tenants* created after September 14, 2026. For eligible *Tenants* created on or before September 14, 2026 please check the Message Center for more details on your *Tenant’s* specific configuration. All Tenant Global Admins are encouraged to check their *Tenant's* setting to ensure it aligns with their company's requirements.

Note

*As part of the initial release, starting on September 14, 2026, the setting is available for review and the customer’s existing data location does not change during the notice period. On December 14, 2026, the recorded selection becomes effective. For *Tenants* that remain Off, Microsoft may then begin moving and storing in-scope customer data regionally within the *EU Data Boundary*. This does not mean that all data moves on December 14, 2026.*

## Changing Your Choice

This choice isn't permanent. If the setting is Off, you can turn it back on at any time. Microsoft re-commits your data to your *Committed Geography* and begins moving it back, which can take approximately 6 months to complete.

Note

*While your data moves, your Data Location Card may temporarily show a mismatch between your Current Geography and your Committed Geography until the move completes. For more information, see "Understanding Mismatches Between Current Geography and Committed Geography" in the [Data Location Card article](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location?view=o365-worldwide#understanding-mismatches-between-current-geography-and-committed-geography).*

## Product Terms Data Residency for Educational Customers

**Terms apply to**: *Educational \(EDU\) Tenants*

**Commitments Period**: The commitment period is equal to the length of the customer's subscription with Microsoft. Typically, this period is 1-3 years.

[*Microsoft 365 Core Services*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#table-1-definitions-and-terms): The services covered by the commitment excerpted below are listed in the following table:

| Service | Date Added to Privacy and Security Terms |
| :--- | :--- |
| Exchange Online | Always Included |
| SharePoint | Always Included |
| OneDrive for Business | Always Included |
| Microsoft Teams | Added November 1, 2022 |
| Microsoft 365 Copilot | Added March 1, 2024 |
| Microsoft 365 Copilot Chat | Added September 1, 2025 |

The language at the time of writing this article is:

- **Office 365 Education:** If Customer is provisioned outside of the EU or EFTA, and Customer has an Office 365 Education subscription but has not purchased an Advanced Data Residency for Education add-on, then notwithstanding the "Location of Customer Data at Rest for Core Online Services" section of the Product Terms, Microsoft may provision Customer's Office 365 Education tenant in, transfer [**Customer Data**](https://www.microsoft.com/licensing/terms/product/Glossary/all) to, and store [**Customer Data**](https://www.microsoft.com/licensing/terms/product/Glossary/all) at rest anywhere within the European Union or North America. If Customer is provisioned in the EU or EFTA, and Customer has an Office 365 Education subscription but has not purchased an Advanced Data Residency for Education add-on, then notwithstanding the "Location of Customer Data at Rest for Core Online Services" section of the Product Terms, Microsoft may provision Customer's Office 365 Education tenant in, transfer [**Customer Data**](https://www.microsoft.com/licensing/terms/product/Glossary/all) to, and store [**Customer Data**](https://www.microsoft.com/licensing/terms/product/Glossary/all) at rest anywhere within the European Union.
- For current language, refer to the "Privacy and Security Terms" tab of the [*Product Terms* webpage](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) and navigate to **Office 365 Services** > **Office 365 Education**.

For more data residency capabilities, refer to the [*Multi-Geo* service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide) and the [*Advanced Data Residency* service](https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide).
