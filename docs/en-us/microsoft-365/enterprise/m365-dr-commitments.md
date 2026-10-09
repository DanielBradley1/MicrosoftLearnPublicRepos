<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-commitments?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-01-30 -->

# Advanced Data Residency: Data commitments

This article describes the specific [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) that Microsoft commits to store at rest in the applicable [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for [eligible customers](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements) who purchase [*Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\).

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

Note

If you have purchased a [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) subscription, Microsoft stores certain *Customer Data* at rest in more than one [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) based on your configuration, even if you have purchased the *Microsoft 365 Advanced Data Residency add-on \("ADR"\)*.

Microsoft makes commitments to store certain in scope customer data at rest in the applicable *Local Region Geography* for [eligible customers](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements) that purchase *ADR*. The commitments are specified as follows.

## Microsoft 365 Core Services

### Exchange Online

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Exchange Online mailbox content \(e-mail body, calendar entries, and the content of e-mail attachments stored in the related *Local Region Geography*\).

### SharePoint and OneDrive

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- SharePoint site content and the files stored within that site and files uploaded to OneDrive

### Microsoft Teams

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Microsoft Teams chat messages \(including private messages, channel messages, meeting messages and images used in chats\), and, for customers using Microsoft Stream \(on SharePoint\), meeting recordings

### Microsoft 365 Copilot and Microsoft 365 Copilot Chat

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Any stored content of interactions with Microsoft 365 Copilot and Microsoft 365 Copilot Chat to the extent not included in the preceding commitments.

Note

For Microsoft 365 Copilot Cowork, please refer to the limitations described [here](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot?view=o365-worldwide).

## Microsoft 365 Expanded Services

### Microsoft Defender for Office P1

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Microsoft Defender for Office 365 P1 doesn't store *Customer Data* within its service.

### Exchange Online Protection

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- [Built-in security features for all cloud mailboxes \(formerly Exchange Online Protection \(EOP\)\)](https://learn.microsoft.com/en-us/defender-office-365/eop-about): The following customer data is stored at rest in the *Local Region Geography*: Service configuration data and policies, quarantined email and attachments, junk email, grading analysis, blocklists \(url, tenant, user\), spam domains, reports, and alerts.

### Office for the web

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Office for the web stores files on a storage host that has its applicable promises to *Local Region Geography*

### Viva Connections

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Viva Connections Dashboard and Feed can have content sourced from SharePoint, Exchange Online and Microsoft Teams. All customer data sourced from these services covered by data residency commitments will be stored in the *Local Region Geography*. Refer to [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide), [SharePoint](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide), and [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide) workload data residency pages for more details.

## Microsoft Purview services

### Data Loss Prevention \(DLP\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- DLP Admin Configuration
- DLP policies in Microsoft Purview portal
- DLP monitored activities
- Violation history
- Activity Explorer and Microsoft 365 unified audit logs
- Quarantine storage
- DLP Alerts and DLP Alert management dashboard

### Information Barriers

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Policy settings
- Risk indicators
- Segments Configuration

### Information Protection

#### Sensitivity labels

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Label configuration
- Labels definition
- Label policies
- Custom help page
- Activity Explorer and Microsoft 365 unified audit logs
- Label change justification records

#### Office Message Encryption \(OME\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Encryption policies
- Admin settings
- Encrypted messages

#### Classifiers

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Sensitive information types, including Enhanced Data Match \(EDM\) and Trainable Classifiers, configured by customers

Note

The Microsoft Purview services list includes all services covered as part of the *Advanced Data Residency* commitment as of February 2026. Additional Microsoft Purview services aren't currently supported.

### Audit \(Standard\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Service configuration data
- Audited Activities
- Audit Records
- Audit log query permissions

### Audit \(Premium\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- All data covered under Audit \(Standard\)
- Configuration and Customer Data related to high-value crucial events

### Data Lifecycle Management

#### Data Retention

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Retention policy settings and retention label definitions
- Customer Data stored in original locations for the following services:

  - Exchange email
  - SharePoint site
  - OneDrive accounts
  - Microsoft 365 Groups
  - Exchange public folders
  - Microsoft Teams chats and channel messages
  - Viva Engage user and community messages

- Customer Data copied and stored in Exchange Online hidden mailboxes

  - Teams channel messages
  - Teams chats
  - Teams private channel messages
  - Viva Engage user and community messages
  - SharePoint, OneDrive, Exchange Online and Microsoft Teams follow the data residency commitments for those services. Refer to [Exchange Online](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-exo?view=o365-worldwide), [SharePoint](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide), and [Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-teams?view=o365-worldwide) workload data residency pages for more details.

- Training classifiers
- Disposition data
- Mappings between retention labels and Data Loss Prevention \(DLP\) policies

#### Records Management

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Record retention label definitions
- File plan definitions
- Event-based retention policy settings
- Disposition review records and records of deletion

## Next steps

- [ADR overview and requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide)
- [Initiate ADR migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide)
