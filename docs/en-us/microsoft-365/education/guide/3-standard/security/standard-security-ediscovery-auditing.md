<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/security/standard-security-ediscovery-auditing -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 2: eDiscovery and auditing

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

This article outlines how to configure eDiscovery and auditing within the Microsoft 365 environment for educational institutions with an A3 license. These features are crucial for maintaining compliance, managing legal holds, and ensuring that all necessary data is preserved and accessible during legal or regulatory investigations.

## Requirements

- Microsoft 365 A3 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Microsoft Purview

| Feature | Description | Learn more Links |
| --- | --- | --- |
| **Audit \(Standard\)** | Provides you with the ability to log and search for audited activities and power your forensic, IT, compliance, and legal investigations | [Learn about auditing solutions in Microsoft Purview](https://learn.microsoft.com/en-us/purview/audit-solutions-overview) |
| **eDiscovery Standard for sites, files, and emails** | Basic eDiscovery tool that organizations can use to search and export content in Microsoft 365 and Office 365 | [Get started with eDiscovery \(Standard\)](https://learn.microsoft.com/en-us/purview/ediscovery-standard-get-started) |
| **Data Classification Analytics: Content Explorer** | Content Explorer provides visibility into amount and types of sensitive data and allows users to filter by label or sensitivity type. | [Microsoft Purview Information Protection: Data classification analytics: Overview Content & Activity Explorer](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-information-protection-data-classification-analytics-overview-content--activity-explorer) |
| **Information Protection Message Encryption** | A service built on Azure Rights Management \(Azure RMS\) that lets you send encrypted email to people inside or outside your organization | [Microsoft Purview Information Protection Message Encryption](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-information-protection-message-encryption) |
| **Sensitivity Labels \(manual\)** | Users can apply sensitivity labels manually to | [Learn about sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels) |
| **DLP for Files and emails** | Prevent their users from inappropriately sharing sensitive data with people who shouldn't have it | [Learn about data loss prevention](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) |
| **Retention Labels \(manual\)** | Manage the data for your organization by deciding proactively whether to retain content, delete content, or retain and then delete the content | [Create and configure retention policies](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=teams-retention) |

## Basic org-wide or location-wide retention policies

**What are basic retention policies?**

Basic retention policies in Microsoft 365 allow educational institutions to retain or delete content across services like Exchange Online, SharePoint, OneDrive, and Microsoft Teams. These policies are centrally managed through the Microsoft Purview portal and are designed to help institutions:

- Comply with regulations such as FERPA, GDPR, and HIPAA.
- Preserve institutional knowledge and academic records.
- Reduce risk by deleting outdated or unnecessary content.

These policies can be applied:

- Org-wide: to all users and content locations across the tenant.
- Location-wide: to specific services like mailboxes, SharePoint sites, or Teams chats.

**How they work in education:**

Retention policies support three core actions:

- Retain-only: Keep content for a specified period \(for example, seven years for student records\).
- Delete-only: Automatically delete content after a set time \(for example, 30 days for junk email\).
- Retain and then delete: Retain content for a period, then delete it \(for example, retain faculty emails for five years, then purge\).

These actions are enforced in-place, meaning content remains in its original location and is discoverable for compliance or legal purposes without needing to move or duplicate it.

**Key education use cases:**

- Student records: Retain OneDrive files and Exchange emails for a minimum of seven years.
- Faculty communications: Apply retention to Teams messages and Outlook mailboxes.
- Research data: Preserve SharePoint content for compliance with grant or funding requirements.
- Graduated students: Automatically delete inactive accounts and associated data after a defined period.

**Policy management and limits:**

Admins can create up to 10 org-wide policies and 1,000 policies with specific inclusions or exclusions. Policies can be combined with retention labels for more granular control, such as tagging specific documents as "Confidential – Student Data" with custom retention rules.

**Learn more:**

- [Microsoft Learn: Retention Policies in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/compliance/retention)  
  A comprehensive guide to setting up retention policies in Microsoft 365 to manage content across your organization.
- [Information Governance in Azure](https://learn.microsoft.com/en-us/azure/governance/)  
  How to use Azure's governance tools to create and manage retention policies.
- [Records management and retention in Google Vault](https://support.google.com/vault/answer/2462365?hl=en)  
  An overview of using Google Vault to manage retention and eDiscovery for your organization.

## Litigation hold

Microsoft 365 for Education offers robust litigation hold capabilities to help educational institutions preserve electronically stored information \(ESI\) during legal proceedings. Here are some key features:

- **Mailbox preservation:** When a mailbox is placed on litigation hold, all content, including deleted items and original versions of modified items, is retained. This retention applies to both the primary and archive mailboxes.
- **Hold duration:** You can specify a hold duration \(time-based hold\) to retain items for a specific period or opt for an indefinite hold until the litigation hold is removed.
- **Increased storage quota:** The storage quota for the Recoverable Items folder is increased from 30 GB to 110 GB when a mailbox is on litigation hold.
- **Retention policies:** Microsoft 365 allows the creation of retention policies and labels to manage data retention and deletion, helping to ensure compliance with legal and regulatory requirements.
- **eDiscovery tools:** The platform includes eDiscovery tools to search, hold, and export data relevant to legal cases, making it easier to manage and review large volumes of information.

**Learn more:**

- [Create a Litigation hold](https://learn.microsoft.com/en-us/purview/ediscovery-create-a-litigation-hold)

In Microsoft 365 for Education, you can use litigation hold in several scenarios to preserve electronically stored information \(ESI\) when there's a reasonable expectation of litigation. Here are some common situations:

- **Anticipated legal action:** When you anticipate legal action involving the institution, such as disputes over student records, employment issues, or compliance with federal regulations.
- **Ongoing litigation:** During ongoing litigation, to ensure that all relevant data is preserved and not accidentally deleted or altered.
- **Regulatory investigations:** When there are regulatory investigations that require the preservation of specific data, such as compliance with Family Educational Rights and Privacy Act \(FERPA\) or other educational regulations.
- **Internal investigations:** For internal investigations related to misconduct, policy violations, or other issues that might lead to legal proceedings.

To place a mailbox on litigation hold in Microsoft 365, you need to have the appropriate permissions, typically assigned through the Discovery Management role group. Once a mailbox is on litigation hold, all content, including deleted items and original versions of modified items, is retained until the hold is removed.

**To configure litigation hold in Microsoft 365:**

1. Navigate to the Microsoft 365 admin center and select **Users > Active users**.
2. Choose the user whose mailbox you want to place on litigation hold and select the user's name to open their properties.
3. To manage the litigation hold, navigate to the **Mail** tab under the user's properties. Under **More actions**, select **Manage litigation hold**.
4. To enable litigation hold, select the box for **Turn on litigation hold**. Optionally, you can specify a hold duration \(in days\) to create a time-based hold. If you leave this box blank, items are held indefinitely until the hold is removed.
5. Select **Save changes** to apply the litigation hold.

Alternatively, you can use the Exchange Admin Center \(EAC\) to place a mailbox on litigation hold:

1. Navigate to the EAC.
2. Select **Recipients > Mailboxes**.
3. To edit mailbox features, select the mailbox you want to place on litigation hold, and then select **Edit**. In the mailbox properties, navigate to **Mailbox features** and under **Litigation hold**, select **Enable**.
4. To specify the hold duration, enter the Litigation hold duration and select **Save** .

**Learn more:**

- [Place a mailbox on litigation hold](https://learn.microsoft.com/en-us/exchange/policy-and-compliance/holds/litigation-holds)

## Microsoft Purview Audit \(Standard\)

**What is Microsoft Purview Audit \(Standard\)?**

**Microsoft Purview Audit \(Standard\)** is a foundational auditing solution included with Microsoft 365 and Office 365 subscriptions, including education SKUs like A1, A3, and A5. It enables IT administrators and compliance officers to:

- Search audit logs for user and admin activities across Microsoft 365 services \(for example, Exchange, SharePoint, Teams\).
- Export and analyze audit records to investigate incidents or support requests.
- Monitor user behavior to ensure compliance with institutional policies.
- Troubleshoot issues by tracing actions taken on files, mailboxes, or configurations.

**Key features in education:**

In educational environments, Audit \(Standard\) is especially useful for:

- Tracking student and faculty activity in Microsoft Teams, OneDrive, and Exchange.
- Investigating security incidents such as unauthorized access or data leakage.
- Supporting compliance with regulations like FERPA, COPPA, and GDPR.
- Providing transparency for digital learning environments and hybrid classrooms.

Audit \(Standard\) is enabled by default for tenants with eligible licenses and retains audit logs for 180 days. It supports searching by user, activity type, date range, and workload, making it a practical tool for school IT admins and compliance teams.

**Audit \(Standard\) vs. Audit \(Premium\):**

While Audit \(Standard\) covers most basic auditing needs, Audit \(Premium\) \(available with Microsoft 365 A5\) adds:

- Longer retention \(up to 10 years\)
- High-value audit events \(for example, when a user accesses a sensitive file\)
- Intelligent insights and higher API bandwidth for automation and integration

## Data classification analytics

**What is data classification analytics?**

Data classification analytics, part of the Microsoft Purview suite, is a compliance and governance capability that helps organizations—including educational institutions—identify, classify, and monitor sensitive data across Microsoft 365 environments. It provides visibility into how data is being used, labeled, and protected, enabling institutions to make informed decisions about data governance and risk management.

**Core capabilities in education:**

In educational settings, where institutions handle a wide range of sensitive data \(for example, student records, financial aid, health information\), data classification analytics support:

- Discovery of sensitive information: Automatically identifies over 300+ built-in sensitive information types \(SITs\), such as student ID numbers, health records, or financial data. Institutions can also define custom types to meet specific compliance needs.
- Classification and labeling: Applies sensitivity and retention labels to content across Microsoft 365 \(for example, Teams, SharePoint, Exchange\) to ensure data is handled appropriately throughout its lifecycle.
- Monitoring and reporting: Provides dashboards and reports that show where sensitive data resides, how it’s being accessed, and whether it’s protected. This includes top SITs, top data sources, and user activity on labeled content.
- Trainable classifiers: Uses machine learning models to identify proprietary or institution-specific data patterns, such as research data or internal assessments.
- Zero change management: Allows institutions to assess their data landscape without enforcing policies immediately—ideal for piloting governance strategies before full rollout.

**Role in data governance frameworks:**

Data classification is a foundational element of a broader data governance framework. In education, this framework ensures that data is:

- Collected and categorized appropriately at the point of entry.
- Protected and retained according to institutional and regulatory policies \(for example, FERPA, GDPR\).
- Archived or disposed of securely when no longer needed.

**Integration with broader education analytics:**

Data classification also supports broader analytics initiatives in education. Education data and AI insights show how classified data feeds into dashboards and predictive models that inform student success strategies, resource allocation, and institutional planning.

## eDiscovery \(Standard\) for sites, files, emails

**What Is Microsoft Purview eDiscovery \(Standard\)?**

Microsoft Purview eDiscovery \(Standard\) is a built-in compliance tool in Microsoft 365 that enables organizations—including educational institutions—to identify, preserve, search, and export content across Microsoft services for legal, regulatory, or investigative purposes. It supports content from:

- Exchange Online \(emails\)
- SharePoint Online and OneDrive for Business \(files and sites\)
- Microsoft Teams, Microsoft 365 Groups, and Viva Engage

**Key capabilities in education:**

In educational settings, eDiscovery \(Standard\) is used to:

- Support legal holds for student or staff-related investigations.
- Respond to FOIA or FERPA requests by searching across mailboxes, Teams chats, and document libraries.
- Preserve evidence in cases of academic misconduct, harassment, or data breaches.

With eDiscovery \(Standard\), you can:

- Create cases to manage investigations.
- Use keyword and property-based queries to search across multiple content locations.
- Preview and refine search results before exporting.
- Export data to a secure Azure Storage location and download it using the eDiscovery Export Tool.

**Licensing and access:**

eDiscovery \(Standard\) is included in Microsoft 365 Education A1, A3, and A5 plans. However, to use it:

- Admins must assign eDiscovery permissions to legal, compliance, or IT roles.
- Required enterprise apps like ComplianceWorkbenchApp and Exchange Online Protection must be enabled.

**Transition from legacy tools:**

The classic eDiscovery experience is being retired in **August 2025**, so institutions should transition to the modern Microsoft Purview portal. This newer experience offers better integration, performance, and support for hybrid and cloud-native education environments.

## Microsoft Purview Data Loss Protection \(for email and files\)

Microsoft Purview Data Loss Prevention \(DLP\) is a cloud-native solution designed to help organizations—including those in education—identify, monitor, and protect sensitive information across Microsoft 365 services such as Exchange Online, SharePoint, OneDrive, and Teams. Based on the enterprise data and public documentation I reviewed, here’s a detailed breakdown of how it works specifically for email and files in educational settings:

**Purpose in education:**

- Protect sensitive data such as student records, financial aid information, health data, and research content.
- Ensure compliance with regulations like FERPA, HIPAA, and GDPR.
- Prevent accidental data leaks through email or file-sharing platforms commonly used in academic environments.

**Key capabilities for email \(Exchange Online\):**

- Automatic detection and protection: DLP policies can detect sensitive data \(for example, student IDs, SSNs, credit card numbers\) and automatically block, encrypt, or flag emails before they're sent.
- Policy tips in Outlook: Users are alerted in real time if their message contains sensitive content, helping them make informed decisions before sending.
- Approval workflows: High-risk messages can trigger alerts or require managerial approval before being sent.

**Key capabilities for files \(SharePoint, OneDrive, Teams\):**

- External sharing controls: DLP can restrict or monitor the sharing of sensitive files with unauthorized users.
- Sensitivity labels and encryption: Files can be automatically labeled and encrypted based on their content.
- Activity monitoring: Admins can track file access and sharing behaviors to enforce compliance.

**Advanced features:**

- Deep Content Analysis: Goes beyond keyword matching by using machine learning classifiers, exact data match \(EDM\), and custom sensitive info types.
- Unified Policy Management: Admins can manage all DLP policies from the Microsoft Purview portal using adaptive scopes.
- Incident Response: Alerts include rich metadata \(user, device, policy details\) and can be triaged directly from email or Microsoft Defender XDR.

**Deployment and integration:**

- Cloud-managed: No on-premises infrastructure is required. DLP is built into Microsoft 365 apps and services, Windows endpoints, and can extend to non-Microsoft apps via Microsoft Defender for Cloud Apps.
- Education-specific scenarios: For example, blocking the transfer of executable files in Teams chats by targeting OneDrive and SharePoint policies, since Teams stores data in those services.
