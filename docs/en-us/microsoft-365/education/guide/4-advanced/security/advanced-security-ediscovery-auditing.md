<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-ediscovery-auditing -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 4: eDiscovery and audit premium plans

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

Educational institutions face increasing demands for robust compliance, legal, and security solutions as they manage sensitive data and respond to regulatory requirements. Microsoft offers eDiscovery and audit capabilities through Microsoft Purview, empowering schools to efficiently investigate incidents, ensure data transparency, and meet legal obligations. This article provides an overview of these premium features and their benefits for education environments.

## Requirements

- Microsoft 365 A5 license
- Purview

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin
- Security Admin
- Compliance Admin

## eDiscovery \(Premium\)

Microsoft Purview eDiscovery \(Premium\) is a powerful compliance and legal investigation tool included in the Microsoft 365 A5 license for education. It enables schools, colleges, and universities to manage complex legal, HR, and regulatory investigations efficiently and defensibly.

**What Is eDiscovery \(Premium\)?**

eDiscovery \(Premium\) builds on the capabilities of eDiscovery \(Standard\) by adding:

- Advanced case management
- Review sets
- Machine learning-based relevance scoring
- Analytics and filtering
- Legal hold and export capabilities

These features help institutions streamline the process of identifying, preserving, analyzing, and exporting content across Microsoft 365 services like Exchange, SharePoint, OneDrive, and Teams.

**Key capabilities for education institutions:**

| Capability | Description |
| --- | --- |
| Legal hold | Preserves content in place to meet legal or regulatory obligations |
| Review sets | Allows investigators to organize and analyze content before export |
| Machine learning | Uses predictive coding to prioritize relevant content |
| Audit trails | Tracks all actions taken during an investigation for defensibility |
| Role-based access | Ensures only authorized personnel can access sensitive case data |

**Strategic benefits in education:**

- FERPA and Title IX compliance: Supports investigations involving student records, misconduct, or discrimination
- HR and faculty investigations: Enables secure handling of internal complaints or policy violations
- Data transparency: Provides visibility into user and admin actions across Microsoft 365
- Cost efficiency: Reduces reliance on third-party legal discovery tools by consolidating capabilities within Microsoft 365

## eDiscovery Steps

**Case creation:**

1. Go to the Microsoft Purview portal.
2. Navigate to **eDiscovery > Premium > Cases**.
3. Select **Create a case**, provide a name and description, and configure case settings \(for example, OCR, duplicate detection\).

**Add custodial and data source:**

1. Add custodial \(for example, user mailboxes, OneDrive\) and non-custodial data sources \(for example, SharePoint, Teams\).
2. Place custodians on legal hold to preserve data.

**Create collections:**

1. Define search conditions using keywords or KQL \(Keyword Query Language\).
2. Choose whether to include unindexed items and configure deduplication settings.

**Commit to a review set:**

- Review collected data and commit it to a review set.
- You can add to a new or existing review set.

**Analyze and review data:**

- Use built-in analytics to:

  - Detect themes and near-duplicates.
  - Identify key conversations or documents.
  - Redact sensitive content

**Export data:**

- Export reviewed content for legal or regulatory use.
- Use AzCopy for large exports and maintain chain-of-custody logs.

**Manage notifications and reports:**

- Send legal hold notifications to custodians.
- Track acknowledgment and generate audit-ready reports

## Audit \(Premium\)

Microsoft Purview Audit \(Premium\) is a compliance and security feature that provides long-term, in-depth audit logging across Microsoft 365 services. It's designed to help educational institutions investigate security incidents, meet regulatory requirements, and maintain operational transparency.

**What is Audit \(Premium\)?**

Audit \(Premium\) builds on the standard audit capabilities by offering:

- Extended log retention \(up to one year by default, and longer with add-ons\)
- Access to high-value forensic events \(for example, mail read events, file access, permission changes\)
- Advanced filtering and search capabilities for faster investigations
- Integration with Microsoft Purview eDiscovery \(Premium\) for legal and compliance workflows

**Key capabilities in education:**

| Feature | Description |
| --- | --- |
| Long-term log retention | Retains audit logs for up to one year, supporting long-term investigations and compliance audits |
| Forensic-level detail | Captures detailed events like file reads, mailbox access, and permission changes—critical for insider threat detection |
| Advanced search | Enables fast, targeted searches across large volumes of audit data using filters and custom queries |
| Integration with compliance tools | Works with Insider Risk Management, eDiscovery, and DLP to provide a unified compliance and investigation platform |

**Benefits for education institutions:**

- FERPA and GDPR compliance: Supports audit requirements for student data access and handling
- Security incident response: Enables rapid investigation of suspicious activity across Microsoft 365
- Transparency and accountability: Tracks user and admin actions for internal reviews and external audits
- Cost efficiency: Reduces the need for third-party audit tools by consolidating capabilities within Microsoft 365 A5

### Audit \(Premium\) steps

#### Step 1: Verify licensing and enable advanced audit

1. Ensure users are assigned a Microsoft 365 A5 license or the Audit and eDiscovery add-on.
2. In the Microsoft 365 admin center, go to **Users > Active users**, select a user, and confirm that:

   - The Microsoft 365 Advanced Auditing app is enabled.
   - The checkbox is selected under Licenses and apps.

Changes take effect within 24 hours.

#### Step 2: Assign permissions

- In the Microsoft Purview portal, assign users to **Audit Reader** or **Audit Manager** role groups.
- For PowerShell access, use the Exchange admin center to assign Audit Logs or View-Only Audit Logs roles.

#### Step 3: Enable logging of crucial events

- Audit \(Premium\) captures high-value events like:

  - MailItemsAccessed
  - SendOnBehalf
  - SearchQueryInitiated

- These events aren't logged by default if mailbox auditing settings were customized previously. You may need to reset or update mailbox audit configurations.

#### Step 4: Configure audit log retention policies

- Default retention for Audit \(Premium\) is one year.
- You can create custom retention policies for specific workloads \(for example, Exchange, SharePoint, Microsoft Entra ID\) to meet compliance needs.
- For 10-year retention, assign the 10-Year Audit Log Retention add-on.

#### Step 5: Perform forensic investigations

- Use the Audit search tool in the Microsoft Purview portal to:

  - Filter by user, activity, date range, or workload.
  - Export logs for legal or compliance review.

- Audit \(Premium\) supports higher API bandwidth, enabling faster access to logs for automation and integration
