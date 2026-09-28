<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-purview -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Microsoft Purview

## Zero Trust

FastTrack provides comprehensive guidance on implementing Zero Trust security principles. The Zero Trust model assumes breach and verifies each request as though it originates from an uncontrolled network. This approach ensures robust security across your networks, applications, and environment. FastTrack accomplishes this by focusing on identity, devices, applications, data, infrastructure, and networks. With FastTrack, you can confidently advance your Zero Trust security journey and protect your digital assets effectively.

With Microsoft Purview, you can implement Zero Trust principles by identifying and protecting your data using a Zero Trust approach. This includes classifying and labeling sensitive data, applying encryption, and enforcing data loss prevention policies. By doing so, you can ensure that your data is secure, compliant, and only accessible to authorized users.

## Data Security Posture Management \(DSPM\) Classic

FastTrack helps eligible Microsoft 365 customers deploy and adopt **Microsoft Purview DSPM Classic** capabilities. Our goal: enable visibility, protection, and governance for sensitive data across your Microsoft 365 environment.

FastTrack provides **remote guidance** through three key phases:

**1. Discover**

- Assist with DSPM onboarding and dashboard setup.
- Enable visibility into sensitive data and risky activities across Microsoft 365 workloads.

**2. Protect**

- Guide configuration of sensitivity labels and policies.
- Share best practices for mitigating risks identified by DSPM.
- Explain how to leverage **Security Copilot** for investigations and insights.

**3. Govern**

- Align DSPM with compliance and governance requirements.
- Interpret analytics reports and prioritize remediation actions.
- Provide recommendations for continuous posture improvement.

### Out of Scope

- Project management or hands-on implementation.
- Custom content development or advanced Copilot extensibility.
- End-user training or change management strategy.
- Regulatory compliance audits or governance assessments.
- Onsite support \(FastTrack is remote-only\).
- Troubleshooting third-party data source ingestion.

## Microsoft Purview Compliance Manager

Microsoft Purview Compliance Manager is a solution that helps you automatically assess and manage compliance across your multicloud environment.

FastTrack provides remote guidance for the following items:

- Reviewing role types.
- Adding and configuring assessments.
- Assessing compliance by implementing improvement actions and determining how this impacts your compliance score.
- Reviewing built-in control mapping and assessing controls.
- Generating a report within an assessment.

### Out of scope

- Custom scripting and coding.
- Connectors.
- Compliance with industry and regional regulations and requirements.
- Hands-on implementation of recommended improvement actions for assessments in Compliance Manager.

### Source environment expectations

Aside from the FastTrack core onboarding, there are no minimum system requirements.

## Microsoft Purview Information Protection

Microsoft Purview Information Protection helps you discover, classify, protect, and govern sensitive information wherever it lives or travels.

FastTrack provides remote guidance for:

- Activating and configuring your tenant.
- Data classification.
- Sensitive information types.
- Creating sensitivity labels.
- Applying sensitivity labels.
- Default sensitivity labels for SharePoint document libraries.
- Installing and configuring the Microsoft Purview Data Loss Prevention \(DLP\) migration assistant for Symantec and Forcepoint.
- Understanding migration report output from the Microsoft Purview DLP migration assistant.
- Fine-tuning migrated policies in the Microsoft Purview portal.
- Discovering and labeling files at rest using the Microsoft Purview Information Protection scanner.
- Monitoring emails in transit using Exchange Online mail flow rules.
- Using migration guidance from the Azure Information Protection add-in to provide built-in labeling for Office apps.
- Enabling the sensitivity label requirement for Microsoft Power BI in the portal.
- Creating and setting up labels and policies.
- Applying information protection to documents.

FastTrack also provides guidance if you want to apply protection using Microsoft Azure Rights Management Services \(Azure RMS\), Purview Message Encryption, and DLP.

The following remote guidance is available only for E5 Premium customers:

- Trainable classifiers.
- Exact Data Match \(EDM\) custom sensitive information types.
- Knowing your data with content explorer and activity explorer.
- Automatically publishing labels using policies.
- Creating Endpoint DLP policies for Windows 10 and later devices.
- Creating Endpoint DLP policies for macOS devices.
- Creating DLP policies for Microsoft Teams chats and channels.
- Automatically classifying and labeling information in Office apps \(like Word, PowerPoint, Excel, and Outlook\) running on Windows and using the Microsoft Purview Information Protection client.
- Extending sensitivity labels to Outlook appointments, invites, and Teams online meetings.

### Out of scope

- Customer Key.
- Custom regular expressions \(RegEx\) development for sensitive information types.
- Creation or modification of keyword dictionaries.
- Interacting with customer data or specific guidelines for configuration of EDM-sensitive information types.
- Custom scripting and coding.
- Azure Purview.
- Configuring Enterprise State Roaming.
- SharePoint data governance and administration.

### Source environment expectations

- For more information, see [FastTrack core onboarding](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/products-and-capabilities#fasttrack-core-onboarding).
- SharePoint data access governance for data access planning:

  - [SharePoint data access governance](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaboration-governance-overview).
  - [SharePoint advanced management overview](https://learn.microsoft.com/en-us/sharepoint/advanced-management).
  - [Restricted access control policy for SharePoint sites](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control).
  - [Restricted access control policy for OneDrive](https://learn.microsoft.com/en-us/sharepoint/limit-access).

### Customer responsibilities

- A list of file share locations to be scanned.
- An approved classification taxonomy.
- Understanding of any regulatory restriction or requirements regarding key management.
- A service account created for your on-premises Active Directory synchronized with Microsoft Entra ID.
- All prerequisites for the Microsoft Purview Information Protection scanner are in place. For more information, see [Prerequisites for installing and deploying the Microsoft Purview Information Protection unified labeling scanner](https://learn.microsoft.com/en-us/azure/information-protection/deploy-aip-scanner-prereqs).
- Ensure user devices are running a supported operating system and have the necessary prerequisites installed. For more information, see [Admin Guide: Install the Microsoft Purview Information Protection unified labeling client for users](https://learn.microsoft.com/en-us/azure/information-protection/rms-client/clientv2-admin-guide-install) and [What is the Microsoft Purview Information Protection app for iOS or Android?](https://learn.microsoft.com/en-us/azure/information-protection/rms-client/mobile-app-faq).
- Installation and configuration of the Azure RMS connector and servers including the Active Directory RMS \(AD RMS\) connector for hybrid support.
- Setup and configuration of Bring Your Own Key \(BYOK\), Double Key Encryption \(DKE\) \(unified labeling client only\), or Hold Your Own Key \(HYOK\) \(classic client only\) should you require one of these options for your deployment.

## Microsoft Purview Data Lifecycle Management and Purview Records Management

Microsoft Purview Data Lifecycle and Purview Records Management helps you to govern your Microsoft 365 data for compliance or regulatory requirements.

FastTrack provides remote guidance for:

- Creating and applying retention policies.
- Creating and publishing retention labels.
- The following remote guidance is available only for E5 Premium customers: Creating and applying event-based retention labels.
- Creating and applying adaptive policy scopes.
- Reviewing file plan creation.
- Reviewing dispositions.
- Policy lookups.

### Out of scope

- Development of a records management file plan.
- Data connectors.
- Azure Purview data governance.
- Creating and managing Power Automate flows.
- Custom scripting and coding.
- Design, architect, and non-Microsoft document review.
- Importing Outlook Data Files \(PSTs\) to Office 365.
- Development of information architecture in SharePoint.
- SharePoint data governance and administration.

### Source environment expectations

- For more information, see [FastTrack core onboarding](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/products-and-capabilities#fasttrack-core-onboarding).
- SharePoint data access governance for data access planning:

  - [SharePoint data access governance](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaboration-governance-overview).
  - [SharePoint advanced management overview](https://learn.microsoft.com/en-us/sharepoint/advanced-management).
  - [Restricted access control policy for SharePoint sites](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control).
  - [Restricted access control policy for OneDrive](https://learn.microsoft.com/en-us/sharepoint/limit-access).

## Microsoft Purview Insider Risk Management

### Purview Insider Risk Management

Microsoft Purview Insider Risk Management correlates various signals to identify potential malicious or inadvertent insider risks, like IP theft, data leakage, and security violations.

FastTrack provides remote guidance for:

- Creating policies and reviewing settings.
- Accessing reports and alerts.
- Creating cases.
- Enabling and configuring forensic evidence.

#### Out of scope

- Creating and managing Power Automate flows.
- Data connectors \(beyond the HR connector\).
- Information barriers.
- Privileged access management.

### Purview Communication Compliance

Microsoft Purview Communication Compliance provides the tools to help organizations detect regulatory compliance and business conduct violations like sensitive or confidential information, harassing or threatening language, and sharing of adult content.

FastTrack provides remote guidance for the following items:

- Creating policies and reviewing settings.
- Accessing reports and alerts.
- Creating notice templates.

#### Out of scope

- Creating and managing Power Automate flows.
- Information barriers.

#### Source environment expectations

For more information, see [FastTrack core onboarding](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/products-and-capabilities#fasttrack-core-onboarding).

## Microsoft Purview eDiscovery & Audit

### Purview eDiscovery \(Premium\)

Microsoft Purview eDiscovery \(Premium\) can help your organization respond to legal matters or internal investigations by discovering data where it lives. You can manage eDiscovery workflows by identifying persons of interest and their data sources, apply holds to preserve data, and then manage the legal hold communication process.

FastTrack provides remote guidance for:

- Creating a new case.
- Putting custodians on hold.
- Managing custodians.
- Performing searches.
- Adding search results to a review set.
- Running analytics on a review set.
- Reviewing and tagging documents.
- Exporting data from the review set.
- Importing non-Office 365 data.

#### Out of scope

- Purview eDiscovery API.
- Data connectors.
- Compliance boundaries and security filters.
- Design, architect, and non-Microsoft document review.

### Purview Audit \(Premium\)

Microsoft Purview Audit \(Premium\) helps organizations conduct forensic and compliance investigations. This is done by increasing audit log retention required to conduct an investigation, providing access to intelligent insights that help determine scope of compromise, and faster access to the Office 365 Management Activity API.

FastTrack provides remote guidance for:

- Enabling advanced auditing.
- Performing a search audit log UI and basic audit PowerShell commands.

#### Out of scope

- Custom scripting and coding.

#### Source environment expectations

For more information, see [FastTrack core onboarding](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/products-and-capabilities#fasttrack-core-onboarding).

## Copilot in Purview

FastTrack provides remote guidance for:

- Onboarding assistance, including:

  - Provisioning Security Compute Units \(SCUs\).

Note

All M365 E5 customer tenants are automatically provisioned and onboarded to Security Copilot.

- Configuring default environments with necessary roles and permissions, and enabling Security Copilot embedded experiences.
- Walkthroughs for Copilot for Purview embedded experiences, including:

  - Data Security Posture Management \(DSPM\):

    - Using Promptbooks: Prebuilt prompt sequences guide investigations involving risky users and sensitive data.
    - Performing Open Prompt Investigations: Explore risks across data users and activities using open-ended prompts. Review the Prompt Gallery to show the range of available prompts.

  - Data Loss Prevention \(DLP\):

    - Using alert summaries \(full alert summaries within the solution\).
    - Using Security Copilot-powered DLP policy insights.
    - Using advanced hunting.

      - Expanding prompts available in DLP beyond the alert summary, like data and user-specific investigation.

    - Using activity explorer.

      - Security Copilot prompts in activity explorer provide responses about activity data and generate filters.

    - Using and configuring the Alert Triage Agent in DLP.

  - Insider Risk Management \(IRM\):

    - Using alert summaries \(full alert summaries within the solution\).
    - Using advanced hunting.

      - Expanding prompts available in insider risk management beyond the alert summary, like user-specific investigation.

    - Using and configuring the Alert Triage Agent in IRM.

  - Compliance:

    - Reviewing eDiscovery evidence summaries.
    - Using eDiscovery natural language search.
    - Using eDiscovery case summaries.
    - Using Communication Compliance contextual summaries.

### Out of scope

- Detailed pricing information. Contact your account team for more information.
- Providing walkthroughs of standalone experiences.
- Creating new custom agents.
- Deploying third-party agents.

#### Microsoft advanced deployment guides

Microsoft provides customers with technology and guidance to assist with deploying your Microsoft 365, Microsoft Viva, and security services. We encourage our customers to start their deployment journey with [these](https://go.microsoft.com/fwlink/?linkid=2226341) offerings.

For non-IT admins, see [Microsoft Purview setup guides](https://learn.microsoft.com/en-us/microsoft-365/compliance/purview-fast-track-setup-guides).

Note

If deployment guidance for a product is not listed in the FastTrack service, complete the Request for Assistance form, to ensure you’re directed to the most appropriate resources for your deployment goals and organizational needs. Once submitted, your request will be reviewed and routed to a resource who can best support your deployment goals.

Note

*Please note that the scope and SLA of support may vary depending on the specific workload. FastTrack can help recommend resources from self-guidance, Microsoft Unified offerings, or Microsoft partners to meet your deployment needs.*
