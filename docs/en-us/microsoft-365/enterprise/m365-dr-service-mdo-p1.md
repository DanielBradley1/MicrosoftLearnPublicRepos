<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-mdo-p1?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# Data Residency for Microsoft Defender for Office P1

## Overview

Service documentation: [Office 365 Security including Microsoft Defender for Office 365 and the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)

Capability Summary: Protects email and collaboration from zero-day malware, phish, and business email compromise. Microsoft Defender for Office 365 Plan 1 builds on [the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/eop-about).

## Data Residency commitments available

### Advanced Data Residency add-on

Required Conditions:

1. [*Tenant*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) has a sign-up country/region included in [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) or *Expanded Local Region Geography*.
2. *Tenant* has a valid Advanced Data Residency subscription for all users in the *Tenant*
3. The MDO P1 subscription [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) is provisioned in *Local Region Geography* or *Expanded Local Region Geography*.

**Commitment:**

Refer to the [ADR Commitment page](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide#microsoft-defender-for-office-p1) for the specific customer [*Data at Rest*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitment for Microsoft Defender for Office P1.

Other Information

In addition, processing of data that is required to analyze threats and inspect suspicious emails, documents, messages, and links is done in a sandbox environment and performed within the *Local Region Geography* or *Expanded Local Region*.

## Built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)

### Overview

Service documentation: [Overview of the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/eop-about)

Capability summary: Built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\) is the cloud-based filtering service that protects your organization against spam, malware, and other email threats.

### Data Residency commitments available

#### Advanced Data Residency add-on

Required Conditions:

1. *Tenant* has a sign-up country/region included in *Local Region Geography* or *Expanded Local Region Geography*.
2. *Tenant* has a valid Advanced Data Residency subscription for all users in the *Tenant*
3. *Customer Data* for the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\) is provisioned in *Local Region Geography* or *Expanded Local Region Geography*

**Commitment:**

Refer to the [Advanced Data Residency Commitment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-commitments?view=o365-worldwide) page for the specific customer *Data at Rest* commitment for the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\).

## Migration

*Customer Data* for the built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\) migrates after [*ADR*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) migration is initiated. Microsoft Defender for Office 365 Plan 1 doesn't have *Customer Data* to migrate.

## How can I determine customer data location?

You can find the actual data location in Tenant Admin Center. As a tenant administrator you can find the actual data location, for committed data, by navigating to **Admin -> Settings -> Org Settings -> Organization Profile -> Data Location**.
