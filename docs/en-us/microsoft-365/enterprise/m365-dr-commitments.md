<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-commitments?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-01-30 -->

# Advanced Data Residency: Data commitments

This article describes the specific [*Customer Data*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) that Microsoft commits to store at rest in the applicable [*Local Region Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) for [eligible customers](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide#eligibility-requirements) who purchase [*Advanced Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) \(*ADR*\).

For definitions of italicized terms, see [Key terms and definitions](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide).

Note

If you have purchased a [*Multi-Geo*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) subscription, Microsoft stores certain *Customer Data* at rest in more than one [*Geography*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) based on your configuration, even if you have also purchased *ADR*.

## Microsoft 365 Core Services

### Exchange Online

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Exchange Online mailbox content \(email body, calendar entries, and the content of email attachments\)

### SharePoint and OneDrive

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- SharePoint site content and the files stored within that site
- Files uploaded to OneDrive

### Microsoft Teams

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Microsoft Teams chat messages \(including private messages, channel messages, meeting messages, and images used in chats\)
- For customers using Microsoft Stream \(on SharePoint\), meeting recordings

### Microsoft 365 Copilot and Microsoft 365 Copilot Chat

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Any stored content of interactions with Microsoft 365 Copilot and Microsoft 365 Copilot Chat to the extent not included in the preceding commitments.

Note

For Microsoft 365 Copilot Cowork limitations, see [Data Residency for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-copilot?view=o365-worldwide).

## Microsoft 365 Expanded Services

### Microsoft Defender for Office P1

Microsoft Defender for Office 365 P1 doesn't store *Customer Data* within its service.

### Exchange Online Protection

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Service configuration data and policies
- Quarantined email and attachments
- Junk email and grading analysis
- Blocklists \(URL, tenant, user\)
- Spam domains
- Reports and alerts

### Office for the web

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Office for the web stores files on a storage host that has applicable commitments to *Local Region Geography*

### Viva Connections

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Viva Connections Dashboard and Feed content sourced from [SharePoint](#sharepoint-and-onedrive), [Exchange Online](#exchange-online), and [Microsoft Teams](#microsoft-teams)

All *Customer Data* sourced from these services and covered by [*Data Residency*](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-key-terms-definitions?view=o365-worldwide#table-12-key-terms-and-definitions) commitments is stored in the *Local Region Geography*. For more information, see the respective services.

## Microsoft Purview services

### Data Loss Prevention \(DLP\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- DLP admin configuration
- DLP policies in Microsoft Purview portal
- DLP monitored activities
- Violation history
- Activity Explorer and Microsoft 365 unified audit logs
- Quarantine storage
- DLP alerts and DLP Alert management dashboard

### Information Barriers

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Policy settings
- Risk indicators
- Segments configuration

### Information Protection

#### Sensitivity labels

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Label configuration
- Label definitions
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

- Sensitive information types, including Enhanced Data Match \(EDM\) and Trainable Classifiers configured by customers

### Audit \(Standard\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Service configuration data
- Audited activities
- Audit records
- Audit log query permissions

### Audit \(Premium\)

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- All data covered under Audit \(Standard\)
- Configuration and *Customer Data* related to high-value crucial events

### Data Lifecycle Management

#### Data retention

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Retention policy settings and retention label definitions
- *Customer Data* stored in original locations for:

  - [Exchange Online](#exchange-online) email
  - [SharePoint](#sharepoint-and-onedrive) sites
  - [OneDrive](#sharepoint-and-onedrive) accounts
  - Microsoft 365 Groups
  - Exchange public folders
  - [Microsoft Teams](#microsoft-teams) chats and channel messages
  - Viva Engage user and community messages

- *Customer Data* copied and stored in Exchange Online hidden mailboxes:

  - Teams channel messages
  - Teams chats
  - Teams private channel messages
  - Viva Engage user and community messages

- Training classifiers
- Disposition data
- Mappings between retention labels and Data Loss Prevention \(DLP\) policies

For more information, see the respective services.

#### Records Management

The following *Customer Data* is stored at rest in the *Local Region Geography*:

- Record retention label definitions
- File plan definitions
- Event-based retention policy settings
- Disposition review records and records of deletion

## Next steps

- [ADR overview and requirements](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-overview?view=o365-worldwide)
- [Initiate ADR migration](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-adr-initiate-migration?view=o365-worldwide)
