<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-license-management?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Advanced Data Residency: License management

This article describes how to manage [*Microsoft 365 Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\) licenses, including verifying coverage, understanding expiration warnings, and maintaining compliance.

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

## Overview

Maintaining proper license coverage is essential to retain the [*Durable Commitment on Data Location*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) provided by *ADR*.

## Verify license coverage

To view the number of assigned *ADR* licenses for your [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions):

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Navigate to **Settings** > **Org settings** > **Organization profile** > **Data location**.
3. Review the [*Data Location Card*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for *ADR* license information.

The *Data Location Card* displays:

| Field | Description |
| :--- | :--- |
| **Required Seat Count** | Number of Microsoft 365 seats that require *ADR* coverage |
| **License Count** | Number of active *ADR* licenses assigned to the *Tenant* |
| **License Expiration** | Expiration date of *ADR* licenses assigned to the *Tenant* |

![Screenshot of Data Location Card showing ADR license information.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-license-information-0725.png?view=o365-worldwide)

Note

Changes to a *Tenant's* licensing count can take up to 24-48 hours to reflect in the *Data Location Card*.

Note

[Microsoft Defender for Office P1](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide), [Microsoft Purview \(select services\)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-purview?view=o365-worldwide), and [Microsoft 365 Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot-offerings?view=o365-worldwide) are covered by [Durable Commitments on Data Location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-what-is-data-residency?view=o365-worldwide#microsoft-365-durable-commitments-on-data-location) but not currently displayed in the *Data Location Card*. For more information, see [Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-services-data-location?view=o365-worldwide).

## Coverage requirements

Customers must cover 100% of paid licenses in the *Tenant* with *ADR* add-on licenses for the *Tenant* to receive [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for *ADR* services.

Note

*ADR* does not impose a minimum licensing threshold; however, 100% license coverage is required to establish and maintain a *Data Residency* commitment.

The required level of coverage depends on the *Tenant* type:

| Tenant type | Coverage requirement |
| :--- | :--- |
| Commercial \(*ADR*\) | 100% of all eligible paid Microsoft 365 seats |
| Education \(*ADR-E*\) | 100% of all eligible Microsoft 365 seats \(paid and unpaid/free\) |
| Mixed Commercial + Education \(*ADR*\) | 100% of all eligible paid Microsoft 365 seats \(free education seats not required\) |

Important

*ADR* coverage is based on a *percentage of eligible seats*, not a fixed seat count—there's no minimum that qualifies on its own. Every *Tenant*, regardless of size, must maintain *100% coverage* to keep the *Durable Commitment on Data Location*. Coverage is calculated using *purchased \(available\)* seats, not the seats currently assigned to users.

## License calculation example

The following example shows how to calculate required *ADR* licenses:

### Table 3.3.1: ADR license calculation example \(Commercial Tenant\)

| *ADR*-related SKU | Available licenses \(Purchased\) | Allocated licenses \(Assigned\) <sup>1</sup> | *ADR* licenses required \(100% of Available\) |
| :--- | :--- | :--- | :--- |
| Office 365 E3 | 200 | 125 | 200 |
| Microsoft 365 F1 | 1,420 | 1,100 | 1,420 |
| Exchange Online Plan 2 | 25 | 22 | 25 |
| **Totals** | **1,645** | **1,247** | **1,645** <sup>2</sup> |

<sup>1</sup> The *Allocated licenses* column is informational only. *ADR* coverage is calculated against *available \(purchased\)* seats, not allocated/assigned seats.

<sup>2</sup> In this example, the *Tenant* must hold *1,645* *ADR* licenses \(100% of the 1,645 available eligible seats\) to maintain a *Durable Commitment on Data Location*. The number 1,645 *isn't* a universal minimum—it's the 100% coverage figure for this specific *Tenant*. A different *Tenant* with 50 or 50,000 eligible paid seats must hold the same number of *ADR* licenses as eligible paid seats. Holding fewer *ADR* licenses than eligible seats—by any amount—means the *Tenant* doesn't have a *Durable Commitment on Data Location* and is subject to being moved out of the [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions).

## Mixed Commercial and Education subscriptions

When a *Tenant* has a mix of commercial and education license types \(for example, E3/E5 combined with A1/A3/A5\), the following applies:

| License type | *ADR* requirement |
| :--- | :--- |
| Paid Commercial/Public Sector \(E3, E5, etc.\) | Must be covered by *ADR* |
| Paid Education \(Microsoft 365 A3/A5, Office 365 A3/A5\) | Must be covered by *ADR* |
| Free subscriptions | Not required to be covered |

Note

*ADR for Education* is only available to Volume Licensing / EES \(Microsoft Enrollment for Education Solutions\) customers. Contact your Microsoft account representative for details on how to obtain an *ADR* Education related SKU.

## ADR and Multi-Geo license interaction

Customers who purchase [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) licenses for their *Tenant* don't need to also purchase *ADR* for the same licenses. This prevents "double licensing" a single seat for two different *Data Residency* programs.

**Example**: If a customer would normally require 15,000 *ADR* licenses to satisfy program requirements, but they also have 4,000 *Multi-Geo* licenses, they're only required to purchase 11,000 *ADR* licenses. The two programs combined cover the normal *ADR* requirement of 100% user coverage.

## Insufficient seat coverage

If a *Tenant* falls below the required number of *ADR* licenses, a warning notification appears on the *Data Location Card*:

> "The Advanced Data Residency \(ADR\) license may not have sufficient seat coverage. Without full seat coverage, the tenant's data may be relocated outside the local region. Please consult with your Microsoft representatives to understand the requirements regarding sufficient seat coverage. Please procure additional ADR licenses promptly to ensure continued data residency within the Local Regional Geography."

A link to Marketplace is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location Card showing insufficient ADR seat coverage warning.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-insufficient-seat-coverage-cropped-0725.png?view=o365-worldwide)

If this warning appears:

1. Contact your Microsoft representative to understand your current agreements
2. Determine what steps are required to bring the *Tenant* back into compliance
3. Procure additional *ADR* licenses promptly

In the event of a substantial discrepancy between the required seat count and license count, the *Data Location Card* updates the [*Committed Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) to display the most current commitments in place \(if any\) after *ADR* has been removed. At this point, data may be relocated subject to the constraints displayed in the updated *Committed Geography*.

## License expiration

The *Data Location Card* displays warnings as *ADR* licenses approach expiration:

### 90 days before expiration

A warning appears:

> "The Advanced Data Residency \(ADR\) licenses are about to expire. Please renew the licenses to maintain ADR coverage and ensure the data remains protected within your Local Regional Geography."

A link to Marketplace is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location Card showing ADR licenses expiring warning.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-licenses-expiring-cropped-0725.png?view=o365-worldwide)

### On expiration date

A message appears:

> "The Advanced Data Residency \(ADR\) license has expired. Without a valid ADR license, the tenant's data may be relocated outside the local region. Please renew promptly to ensure continued data residency within the Local Regional Geography."

A link to Marketplace is provided within the message to assist with procurement of *ADR* licenses.

![Screenshot of Data Location Card showing ADR licenses expired message.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/data-residency/m365-dlc-adr-licenses-expired-cropped-0725.png?view=o365-worldwide)

## Grace period

While *ADR* licenses are expired, Microsoft provides a grace period to allow license renewal.

### During the grace period

- The *Committed Geography* on the *Data Location Card* doesn't change
- *Tenant* data isn't relocated

### After the grace period ends

- Microsoft removes the *Durable Commitment on Data Location* provided by *ADR*
- The *Committed Geography* updates to display current commitments \(if any\) after *ADR* removal
- Data may be relocated, without notification or warning, subject to the constraints displayed in the updated *Committed Geography*

## Next steps

- [Prerequisites and eligibility](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-prerequisites?view=o365-worldwide)
- [Initiate migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide)
- [Migration status and notifications](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-migration-status?view=o365-worldwide)
