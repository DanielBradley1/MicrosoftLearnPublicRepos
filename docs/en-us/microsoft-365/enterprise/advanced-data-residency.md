<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/advanced-data-residency?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-18 -->

# Advanced Data Residency in Microsoft 365

## Overview of Advanced Data Residency

The *Microsoft 365 Advanced Data Residency add-on* \(*ADR*\) provides eligible customers with expanded coverage of Microsoft 365 services and Customer Data, committed data residency for local country/region datacenter regions, and prioritized *Tenant* migration services. With *Advanced Data Residency*, enterprise customers can best address their data residency compliance and *Tenant* location requirements.

The following services are included in *ADR*. For more information, see:

- [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide)
- [Microsoft 365 Copilot and Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide)
- [Microsoft 365 web apps \(formerly "Office for the Web"\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-m365-web-apps?view=o365-worldwide)
- [Microsoft Defender for Office P1 and the built-in security features for all cloud mailboxes \(formerly "Exchange Online Protection \(EOP\)"\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide)
- [Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide)\*

  - [Audit \(Standard\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---audit-standard)
  - [Audit \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---audit-premium)
  - [Data Lifecycle Management \(DLM\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#risk--compliance---data-lifecycle-management-dlm)
  - [Data Loss Prevention \(DLP\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---data-loss-prevention-dlp)
  - [Information Barriers](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---information-barriers)
  - [Information Protection \(MIP\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#data-security---information-protection-mip)

- [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide)
- [SharePoint/OneDrive](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide)
- [Viva Connections](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-viva-connections?view=o365-worldwide)

Note

\*The Microsoft Purview services list includes all services covered as part of the *Advanced Data Residency* commitment as of February 2026. Additional Microsoft Purview services aren't currently supported.

## Licensing and Purchase

### Eligibility

The *Advanced Data Residency* \("*ADR*"\) add-on is intended for Microsoft 365 enterprise customers who have comprehensive data residency requirements. To be eligible to purchase *ADR*, customers must meet the following prerequisites:

- The *Tenant Default Geography* must be one of the countries or regions included in the *Local Region Geography*: Australia, Austria, Brazil, Canada, Chile, Denmark, France, Germany, India, Indonesia, Israel, Italy, Japan, Malaysia, Mexico, New Zealand, Norway, Poland, Qatar, South Africa, South Korea, Spain, Sweden, Switzerland, Taiwan, United Arab Emirates, and United Kingdom.
- Customers must have licenses for one or more of the following products:

  - Microsoft 365 A3, A5, F1, F3, E3, E5, or E7 \(including SKUs without Microsoft Teams\)
  - Office 365 A1, A3, A5, F3, E1, E3, or E5 \(including SKUs without Microsoft Teams\)
  - Exchange Online Plan 1 or Plan 2
  - OneDrive Plan 1 or Plan 2
  - SharePoint Plan 1 or Plan 2
  - Microsoft Teams Enterprise, EEA, or Essentials
  - Microsoft 365 Apps for Enterprise
  - Microsoft 365 Business Basic, Standard, or Premium \(including SKUs without Microsoft Teams\)

### Licensing Requirements

Customers must cover 100% of paid licenses in the *Tenant* with *ADR add-on* licenses for the *Tenant* to receive data residency for *ADR* services.

Note

ADR does not impose a minimum licensing threshold; however, 100% license coverage is required to establish and maintain a data residency commitment.

The required level of coverage depends on the *Tenant* type:

| Tenant type | Coverage requirement |
| --- | --- |
| Commercial \(ADR\) | 100% of all eligible paid Microsoft 365 seats |
| Education \(ADR-E\) | 100% of all eligible Microsoft 365 seats \(paid and unpaid/free\) |
| Mixed Commercial + Education \(ADR\) | 100% of all eligible paid Microsoft 365 seats \(free education seats not required\) |

Important

*ADR* coverage is based on a *percentage of eligible seats*, not a fixed seat count—there's no minimum that qualifies on its own. Every *Tenant*, regardless of size, must maintain *100% coverage* to keep the *Durable Commitment on Data Location*. Coverage is calculated using *purchased \(available\)* seats, not the seats currently assigned to users.

ADR License Calculation Example \(Commercial Tenant\):

| ADR-related SKU | Available Licenses \(Purchased\) | Allocated Licenses \(Assigned\) <sup>1</sup> | ADR Licenses Required \(100% of Available\) |
| --- | --- | --- | --- |
| Office 365 E3 | 200 | 125 | 200 |
| Microsoft 365 F1 | 1420 | 1100 | 1420 |
| Exchange Online Plan 2 | 25 | 22 | 25 |
| Totals | 1645 | 1247 | 1645 <sup>2</sup> |

<sup>1</sup> The *Allocated licenses* column is informational only. *ADR* coverage is calculated against *available \(purchased\)* seats, not allocated/assigned seats.

<sup>2</sup> In this example, the *Tenant* must hold *1,645* *ADR* licenses \(100% of the 1,645 available eligible seats\) to maintain a *Durable Commitment on Data Location*. The number 1,645 *isn't* a universal minimum—it's the 100% coverage figure for this specific *Tenant*. A different *Tenant* with 50 or 50,000 eligible paid seats must hold the same number of *ADR* licenses as eligible paid seats. Holding fewer *ADR* licenses than eligible seats—by any amount—means the *Tenant* doesn't have a *Durable Commitment on Data Location* and is subject to being moved out of the *Local Region Geography*.

Customers who purchase *Multi-Geo* licenses for their *Tenant* don't have to also pay for *ADR* for the same licenses. You avoid 'double licensing' a single seat for two different data residency programs. For example, if a customer would normally require 15,000 *ADR* licenses to satisfy the program requirements, but they also have 4,000 *Multi-Geo* licenses, then they're only required to purchase 11,000 *ADR* licenses. The two programs combined would cover the normal *ADR* program requirement of 100% user coverage.

Tip: To view/determine the number of assigned *ADR* licenses for your *Tenant*, you can access the *Data Location Card* in the Microsoft 365 admin center by navigating to **Admin > Settings > Org settings > Organization profile > Data location**. This page displays the "Required Seat Count," "License Count," and "License Expiration." For more information, see [What does the "Advanced Data Residency \(ADR\) License Information" display?](#what-does-the-advanced-data-residency-adr-license-information-display) later in this article.

Note

[Microsoft Defender for Office P1](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide), [Microsoft Purview \(select services\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide), and [Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide) are covered by [Durable Commitments on Data Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#durable-commitments-on-data-location) but not currently displayed in the *Data Location Card*. For more information, see [Where your Microsoft 365 customer data is stored](https://learn.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide).

[![Screenshot of Data Location Card Advanced Data Residency \(ADR\) License Information.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-license-information-0725.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-license-information-0725.png?view=o365-worldwide#lightbox)

Note

Changes to a *Tenant's* licensing count can take up to 24-48 hours to reflect in the *Data Location Card*.

### Tenants with a mix of Commercial and Education subscriptions

When a customer has a mix of commercial and education license types including both Commercial/Public Sector \(for example, E3, E5\) and Education \(for example, A1, A3\) licenses in their subscription, the following applies:

- Customers have rights to purchase full *ADR add-on* for only the paid portion of Microsoft 365 SKUs and aren't obligated to cover free subscription types. However, they must cover the paid education licenses with *ADR* \(Microsoft 365 A3/A5, Office 365 A3/A5 student or faculty\).
- ADR for Education is only available to Volume Licensing / EES \(Microsoft Enrollment for Education Solutions\) customers; contact your Microsoft account representative for details on how to obtain an ADR Education related SKU.

## Data Migration Management

If any customer *Tenant* data covered by the *Advanced Data Residency* feature isn't stored at rest within the customer's eligible *Local Region Geography*, then a data migration is needed to address customer data residency compliance and *Tenant* location requirements that are fulfilled by *ADR*.

### Starting Data Migration

To determine if a *Tenant* needs to perform a data migration, the Tenant Global Admin should visit the *Data Location Card* in the Microsoft 365 admin center by navigating to **Admin > Settings > Org settings > Organization profile > Data location**. From here, the Tenant Global Admin can see the current location of the customer's data-at-rest.

After receiving the *Advanced Data Residency* licenses, the Tenant Global Admin must select the option displayed on the *Data Location Card* to initiate the data migration process for *ADR* services that don't currently reside in their *Local Region Geography*.

#### Microsoft 365 Admin Center Data Location

The following screenshot is an example of the Microsoft 365 admin center *Data Location Card* view that an *ADR* customer sees before opting for migration to their *Local Region Geography*.

[![Screenshot of Microsoft 365 Admin Center Data location View.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-mac-view-1125.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-mac-view-1125.png?view=o365-worldwide#lightbox)

Note

The data migration process described in the following sections doesn't initiate until the Tenant Global Admin completes this task.

#### Before Migration Opt-in

Once a Tenant Global Admin chooses the option to initiate migration, they're provided with confirmation of their opt-in date and migration initiation.

![Screenshot of Data Location View Before Migration Opt-in.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-opt-in-0725.png?view=o365-worldwide)

#### After Migration Opt-in

The *Data Location Card* in the Microsoft 365 admin center displays the most up-to-date location of each service throughout the data migration process. Tenant Global Admins can also view any Message center notifications related to their migration within the Microsoft 365 admin center by navigating to **Health > Message center**.

![Screenshot of Data Location View After Migration Opt-in.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-in-progress-cropped-0725.png?view=o365-worldwide)

### Migration Expectations

Microsoft adheres to the [Microsoft Online Services Service Level Agreement \(SLA\)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for service availability and uses reasonable efforts to complete an *Advanced Data Residency add-on* customer data migration within 12 months from the time the Tenant Global Admin selects the option to initiate migration. However, large, complex customers, and situations outside of Microsoft's control, may require more time for migration to complete.

Data moves are a back-end service operation with minimal impact to a customer's operations. For information related to specific services, Tenant Global Admins can refer to the "Migration" sections in the following Service Data Residency Capabilities pages: [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide#migration), [SharePoint and OneDrive](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide#migration-with-advanced-data-residency), [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide#migration), [Microsoft 365 Copilot and Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide#migration-and-user-experience), [Microsoft Defender for Office P1](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide#migration), [Microsoft 365 web apps \(formerly known as "Office for the Web"\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-m365-web-apps?view=o365-worldwide#migration), [Viva Connections](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-viva-connections?view=o365-worldwide#migration), [Microsoft Purview](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide#migration), and [Other Services](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-other?view=o365-worldwide).

### During and After your Migration

No action is needed from the customer while Microsoft moves each *ADR* service and associated customer *Tenant* data to the customer's eligible *Local Region Geography*.

Tenant Global Admins can visit *Message center* or access the *Data Location Card* within the Microsoft 365 admin center throughout the migration process to review any migration notices and see when each service completes migration. From the Microsoft 365 admin center, Tenant Global Admins can access the Message center by navigating to **Health > Message center** and the *Data Location Card* by navigating to **Admin > Settings > Org settings > Organization profile > Data location**.

The following screenshots are examples of the Microsoft 365 admin center *Data Location Card* view that an *ADR* customer can expect to see during and after their migration.

#### During Migration

![Screenshot of Data Location View Migration in Progress.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-in-progress-0725.png?view=o365-worldwide)

#### After Migration

![Screenshot of Data Location View Migration Completed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-move-complete-0725.png?view=o365-worldwide)

### Effect on End Users and Services

Data moves are a back-end service operation with minimal, if any, effect on end users. Microsoft adheres to the [Microsoft Online Services Service Level Agreement \(SLA\)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for service availability and notifies customers of any service maintenance done via Message center in the Microsoft 365 admin center.

### Features Affected

Given the complex nature of services that are included in an E3 or E5 license, the migration of customer data from one data center to another could cause minor disruption or temporary unavailability of certain services. For more information, Tenant Global Admins can refer to the "Migration" section of each service page within [Service Data Residency Capabilities](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide).

### Status Notification

Microsoft doesn't provide a granular status to indicate progress toward migration completion for individual customer scenarios.

Tenant Global Admins can stay informed of migration updates through Message center notifications and reviewing the "Data location" section within the Microsoft 365 admin center to see when a service completes migration to their *Local Region Geography*. From the Microsoft 365 admin center, Tenant Global Admins can access the Message center by navigating to **Health > Message center** and the *Data Location Card* by navigating to **Admin > Settings > Org settings > Organization profile > Data location**.

For more information on Migration and Data Location, Tenant Global Admins can refer to the following pages:

- [Overview and Definitions - Microsoft 365 Enterprise](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-overview?view=o365-worldwide#migrationsmoves)
- [Where your Microsoft 365 customer data is stored - Microsoft 365 Enterprise](https://learn.microsoft.com/en-us/microsoft-365/enterprise/o365-data-locations?view=o365-worldwide)
- [Learn More about the Data Location Card - Microsoft 365 Enterprise](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-data-location?view=o365-worldwide)

### What does the "Advanced Data Residency \(ADR\) License Information" display?

The *Data Location Card* now shows *Advanced Data Residency \(ADR\)* licensing details. *Tenants* with active or recently active *ADR* subscriptions see an "Advanced Data Residency \(ADR\) License Information" section that displays three fields related to a *Tenant's* licensing:

1. **Required Seat Count**: This field displays the number of Microsoft 365 seats that require *ADR* coverage.
2. **License Count**: This field displays the number of active *ADR/ADR-E* licenses assigned to the *Tenant*.
3. **License Expiration**: This field displays the expiration date of the *ADR* license assigned to the *Tenant*.

### What happens if a *Tenant* has insufficient seat coverage for ADR?

The *Data Location Card* now displays warnings and notifications related to Seat Coverage.

If a *Tenant* falls below the number of licenses required for *ADR* coverage, a statement appears on the *DLC* indicating that "The Advanced Data Residency \(ADR\) license may not have sufficient seat coverage. Without full seat coverage, the tenant's data may be relocated outside the local region. Please consult with your Microsoft representatives to understand the requirements regarding sufficient seat coverage. Please procure additional ADR licenses promptly to ensure continued data residency within the Local Regional Geography." A link to *Marketplace* is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location View Insufficient ADR Seat Coverage.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-insufficient-seat-coverage-cropped-0725.png?view=o365-worldwide)

If this warning message appears on a *Tenant's Data Location Card*, Tenant Global Admins should reach out to their Microsoft Representatives to understand if their current agreements reflect properly and what steps, if any, are required to bring the *Tenant* back into compliance.

If there's a substantial discrepancy between the "Required Seat Count" and "License Count" the *Data Location Card* will update the *Committed Geography* location to display the most current and accurate commitments in place \(if any\) after *ADR* is removed. At this point, data may be relocated subject to the constraints displayed in the updated *Committed Geography*.

### ADR License Warnings and Notifications Related to License Expiry

The new *Data Location Card* is designed to help Tenant Global Admins track when *ADR* licenses are nearing expiry, and displays the following warnings and alerts in relation to license expiry:

**90 days before License Expiration**: A statement appears on the *DLC* indicating that "The Advanced Data Residency \(ADR\) licenses are about to expire. Please renew the licenses to maintain ADR coverage and ensure the data remains protected within your Local Regional Geography." A link to *Marketplace* is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location View ADR Licenses Expiring.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-licenses-expiring-cropped-0725.png?view=o365-worldwide)

**On License Expiration**: Starting on the day a *Tenant's* licenses expired, a statement appears on the *DLC* indicating that "The Advanced Data Residency \(ADR\) license has expired. Without a valid ADR license, the tenant's data may be relocated outside the local region. Please renew promptly to ensure continued data residency within the Local Regional Geography." A link to *Marketplace* is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location View ADR Licenses Expired.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-licenses-expired-cropped-0725.png?view=o365-worldwide)

It's important to note that while a *Tenant's ADR* licenses are expired, Microsoft provides a grace period to allow the customer to renew their licenses. During this grace period, the *Tenant's Data Location Card* doesn't display any changes to the *Tenant's Committed Geography* and the *Tenant's* data won't be relocated.

**After Grace Period**: After the grace period provided, Microsoft will remove the *Durable Commitment on Data Location* provided by *ADR*, and the *Committed Geography* location in the *DLC* will update to display the most current and accurate commitments in place \(if any\) after *ADR* is removed. At this point, data may be relocated, without notification or warning, subject to the constraints displayed in the updated *Committed Geography*.
