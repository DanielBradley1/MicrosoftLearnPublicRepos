<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-advanced/start-adv-security -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Overview - Advanced security deployment guide for A5 licenses

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides a checklist for the continued steps to configure security for your Microsoft 365 education tenant with an A5 license.

## Required Microsoft products

- Microsoft 365 A5 license

## Step 1 - Security and compliance

Identity access management features help institutions manage user access and protect sensitive data.

|  |  |  |
| --- | --- | --- |
|  |  | **[Microsoft Defender for Microsoft 365 Plan 2](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance)** - Microsoft Defender for Microsoft 365 Plan 2 is an advanced security solution that builds on Plan 1 by adding automated investigation, threat hunting, and attack simulation capabilities—ideal for organizations like educational institutions that need to defend against sophisticated threats across email and collaboration platforms |
|  | ☐ | [Prevent and Detect Threats](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Anti-phishing policies with impersonation protection |
|  |  | - Safe Attachments for SharePoint, OneDrive, and Microsoft Teams |
|  |  | - Safe Links for real-time URL scanning |
|  | ☐ | [Automated Investigation and Response \(AIR\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Automatically investigates and remediates threats using built-in playbooks |
|  |  | - Reduces alert fatigue and response time |
|  | ☐ | [Threat Intelligence and Hunting](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Access to Threat Explorer and Threat Trackers |
|  |  | - Advanced hunting capabilities via Microsoft Defender XDR |
|  | ☐ | [Incident and Alert Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Centralized incident view across Microsoft 365 workloads |
|  |  | - Deep investigation of alerts and correlation of threat signals |
|  | ☐ | [Attack Simulation Training](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Simulate real-world phishing and social engineering attacks |
|  |  | - Educate users and measure organizational risk |
|  | ☐ | [Campaign Views](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Visualize phishing campaigns and their impact across the organization |
|  | ☐ | [Integration with Microsoft Defender XDR](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - Unified experience for detecting, investigating, and responding to threats across endpoints, identities, email, and apps |
|  |  | **[Microsoft Defender for EndPoint Plan 2](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance)** - Microsoft Defender for Endpoint Plan 2 is an enterprise-grade endpoint security platform that combines behavioral sensors, cloud security analytics, threat intelligence, and advanced features like endpoint detection and response \(EDR\), attack surface reduction, and threat expert consultation to proactively prevent, detect, investigate, and respond to sophisticated threats across devices |
|  | ☐ | [Deployment and Setup](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - **Update Devices:** Ensure all endpoints have the latest OS and antivirus updates |
|  |  | - **License Assignment:** Acquire and assign Defender for Endpoint Plan 2 licenses \(included in Microsoft 365 E5\) |
|  |  | - **Portal Access:** Grant access to the Microsoft Defender portal for security admins and operators |
|  |  | - **Network Configuration:** Configure proxy and internet settings for endpoint connectivity |
|  | ☐ | [Core Capabilities](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - **Attack Surface Reduction:** Apply rules to minimize exploitable areas on devices |
|  |  | - **Next-Generation Protection:** Use AI-powered antivirus and anti-malware engines |
|  |  | - **Endpoint Detection and Response \(EDR\):** Detect, investigate, and respond to advanced threats with behavioral analytics |
|  |  | - **Threat and Vulnerability Management \(TVM\):** Continuously assess and remediate endpoint vulnerabilities |
|  |  | - **Automated Investigation and Remediation \(AIR\):** Use built-in playbooks to reduce manual workload and response time |
|  | ☐ | [Operational Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance) |
|  |  | - **Monitoring and Alerts:** Use the Microsoft Defender portal to monitor incidents and alerts across endpoints |
|  |  | - **Integration with Microsoft Defender XDR:** Correlate endpoint data with signals from identities, email, and cloud apps |
|  |  | - **Performance Baseline:** Capture and monitor endpoint performance metrics to detect anomalies |

## Step 2 - Cloud access security broker

**[Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker)** is a cloud access security broker \(CASB\) that provides deep visibility, threat protection, and governance for SaaS applications by discovering shadow IT, monitoring app-to-app interactions, enforcing data protection policies, and securing OAuth-enabled apps through advanced app governance and compliance controls

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Licensing and Access Setup](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **Obtain licenses:** Assign Microsoft Defender for Cloud Apps licenses to users \(included in Microsoft 365 E5 or available as add-ons\) |
|  |  | - **Access the portal:** Navigate to the Microsoft Defender portal and select the Cloud Apps section to begin configuration |
| ☐ |  | [Discover and Monitor Cloud Usage](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **Shadow IT Discovery:** Use built-in discovery tools to identify unsanctioned or unmanaged cloud apps in use across your organization |
|  |  | - **App Cataloging:** Classify apps as sanctioned or unsanctioned based on risk scores and compliance |
| ☐ |  | [Configure Policies and Controls](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **Conditional Access App Control:** Integrate with Microsoft Entra ID to enforce real-time session controls for risky apps |
|  |  | - **Policy Creation:** Define policies for anomaly detection, file sharing, OAuth app governance, and data exfiltration |
| ☐ |  | [Enable App Governance](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **App-to-App Risk Management:** Monitor and control third-party apps connected via OAuth to Microsoft 365 |
|  |  | - **GenAI App Detection:** Automatically identify and flag unmanaged generative AI apps in your environment |
| ☐ |  | [Integrate with Microsoft Defender XDR](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **Unified Threat Detection:** Correlate cloud app signals with endpoint, identity, and email data for comprehensive threat detection |
|  |  | - **Alert Management:** Investigate and respond to alerts from Defender for Cloud Apps within the broader XDR incident queue |
| ☐ |  | [Educate and Operationalize](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker) |
|  |  | - **Use Playbooks:** Follow structured guides like the app governance Playbook to embed governance into your processes |
|  |  | - **Join Expert Sessions:** Participate in events like Ask the Experts |

## Step 3 - Data Lifecycle Management

**[Data Lifecycle Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management)** in a Microsoft A5 tenant refers to the automated governance of data retention and deletion across Microsoft 365 services using advanced compliance tools—such as retention policies, labels, and machine learning classifiers—available through Microsoft Purview to meet regulatory, legal, and organizational requirements.

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Retention Policies and Labels](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management#rules-based-automatic-retention-policies) |
|  |  | - **Rules-based automatic retention policies** Automatically retains or deletes content based on predefined conditions such as content type, location, keywords, or user attributes—without requiring manual labeling. |
|  |  | - **Machine learning-based retention** Use intelligent classifiers trained on real-world data to automatically identify and apply retention settings to content based on its meaning and context, rather than relying solely on predefined rules or keywords. |
|  |  | - **Automatic sensitivity labeling in Microsoft 365 apps** uses built-in or custom machine learning classifiers to automatically detect and apply sensitivity labels to content—such as emails, documents, and Teams chats—based on its content and context, helping enforce data protection policies without user intervention. |
|  |  | - **Automatic sensitivity labels in Exchange, OneDrive, and SharePoint** automatically applies sensitivity labels to emails and files stored in these services based on content inspection, policy conditions, or machine learning, helping enforce data protection without relying on user action. |
|  |  | - **Default sensitivity labels for SharePoint document libraries** Allows administrators to automatically apply a predefined sensitivity label to all documents uploaded to or created within a specific SharePoint library, ensuring consistent data protection without requiring user action. |
|  |  | - **Sensitivity labels based on advanced classifiers** Uses machine learning models—trained on real-world content types like contracts or resumes—to automatically identify and label sensitive data across Microsoft 365, enabling consistent protection without relying on manual tagging or static rules. |
| ☐ |  | [Records Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management#microsoft-purview-records-management) |
|  |  | - **Microsoft Purview Records Management** Enables organizations to manage high-value business, legal, or regulatory records by applying retention labels, automating disposition, and providing proof of deletion—ensuring defensible, auditable, and policy-driven lifecycle control across Microsoft 365 content |
| ☐ |  | [Insider Risk Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management#microsoft-purview-insider-risk-management) |
|  |  | - **Microsoft Purview Insider Risk Management** Helps organizations detect, investigate, and act on potentially malicious or inadvertent insider activities—such as IP theft, data leakage, or policy violations—by correlating signals across Microsoft 365 while preserving user privacy through pseudonymization and role-based access controls |
| ☐ |  | [Adaptive Protection](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management#purview-endpoint-data-loss-prevention-dlp) |
|  |  | - **Microsoft Purview EndPoint Data Loss Prevention** A feature within the Microsoft Purview DLP suite that extends data protection to onboarded Windows and macOS devices by monitoring and controlling the use, sharing, and movement of sensitive information—enabling organizations to detect risky behavior and enforce compliance policies directly at the endpoint |

## Step 4 - Microsoft Purview eDiscovery and audit

**[eDiscovery and audit](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-ediscovery-auditing)** - Microsoft Purview eDiscovery enables educational institutions to manage legal, regulatory, and internal investigations by identifying, preserving, searching, analyzing, and exporting content across Microsoft 365 services such as Exchange, SharePoint, OneDrive, and Teams. Microsoft Purview Audit provides visibility into user and admin activities across Microsoft 365, supporting forensic investigations, compliance monitoring, and insider risk detection.

|  |  |  |
| --- | --- | --- |
| ☐ |  | [eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-ediscovery-auditing#ediscovery-premium) |
|  |  | - **eDiscovery-Premium** Enables organizations to manage complex legal and regulatory investigations by identifying, preserving, collecting, analyzing, and exporting content across Microsoft 365 using tools like review sets, machine learning, and legal hold workflows. |
|  |  | - **Case Creation** The initial step in managing a legal or compliance investigation, where a secure workspace is established to define custodians, apply legal holds, collect and analyze content, and track all activities related to the case. |
|  |  | - **Create Collections** Define search criteria to gather potentially relevant content from custodial and non-custodial data sources, which can then be reviewed, analyzed, and added to a review set for legal or compliance investigations. |
|  |  | - **Commit to a Review Set** The process in Microsoft Purview eDiscovery \(Premium\) where collected content from a search or collection is added to a secure, centralized workspace—called a review set—for further analysis, tagging, redaction, and export during legal or compliance investigations. |
|  |  | - **Analyze and Review Data** Collected content is examined using built-in analytics, filters, and tagging tools to identify relevant information, detect patterns, redact sensitive data, and prepare materials for legal or compliance review. |
|  |  | - **Export Data** The final step in Microsoft Purview eDiscovery \(Premium\) where reviewed and tagged content from a review set is securely exported—along with metadata and audit logs—for legal, regulatory, or investigative use, ensuring chain-of-custody and compliance integrity. |
| ☐ |  | [Audit](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-ediscovery-auditing) |
|  |  | - **Verify Licensing and Enable Advanced Audit** Ensuring that users are assigned the appropriate Microsoft 365 A5 or Audit and eDiscovery add-on licenses and confirming that advanced auditing features—such as extended retention and high-value event logging—are activated in the Microsoft Purview portal for eligible accounts. |
|  |  | - **Assign Permissions** Granting users roles such as Audit Reader or Audit Manager within the Microsoft Purview portal, enabling them to search, view, and export audit logs while maintaining role-based access control for secure and compliant investigations. |
|  |  | - **Enable Logging of Crucial Events** Configuring the system to capture high-value forensic signals—such as MailItemsAccessed, SendOnBehalf, and SearchQueryInitiated—by ensuring mailbox auditing is properly enabled and advanced audit features are activated for licensed users. |
|  |  | - **Configure Audit Log Retention Policies** Setting custom retention durations—up to 1 year by default or 10 years with add-ons—for audit logs across Microsoft 365 workloads, ensuring long-term availability of critical forensic data to meet regulatory, legal, or investigative requirements. |
|  |  | - **Perform Forensic Investigations** Using advanced search capabilities and extended retention of audit logs to trace user and admin activities across Microsoft 365, enabling organizations to reconstruct events, detect anomalies, and support legal or compliance inquiries with detailed, time-stamped evidence. |

## Step 5 - Information Protection

**[Information Protection](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-information-protection)** in the A5 license for Education is a suite of compliance and security tools \(part of Microsoft Purview\) that enables educational institutions to classify, protect, retain, and govern sensitive data across Microsoft 365 services, helping meet regulations like FERPA, GDPR, and HIPAA while supporting secure collaboration and automated data governance.

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Advanced Message Encryption](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-information-protection#advanced-message-encryption) |
|  |  | Microsoft Purview Information Protection is a feature that enhances email security by allowing organizations to apply customizable encryption and access controls—such as expiration dates, revocation, and branding—to sensitive emails, ensuring secure communication even with external recipients. |
|  |  | - **Verify Prerequisites** Prerequisites for Advanced Message Encryption \(AME\), your organization must have a Microsoft 365 E5 Compliance, Microsoft 365 E5 Information Protection & Governance, or Office 365/Microsoft 365 E5 license, and AME must be configured to route encrypted messages through the secure web portal to enable expiration and revocation features. |
|  |  | - **Enable Microsoft Purview Message Encryption** To enable Microsoft Purview Message Encryption with Advanced Message Encryption, administrators must define mail flow rules that apply encryption and custom branding templates, ensuring external recipients access encrypted emails through a secure web portal where expiration and revocation controls can be enforced. |
|  |  | - **Create Custom Branding Templates** Use the New-OMEConfiguration PowerShell cmdlet to define branded elements like logos, color schemes, disclaimers, and expiration settings, which are then applied to encrypted emails via mail flow rules to reinforce trust and control message access |
|  |  | - **Configure Mail Flow Rules \(Transport Rules\)** Administrators define conditions and actions in the Exchange admin center that automatically apply encryption and branding templates to outbound messages based on sensitivity labels, keywords, or recipient domains, ensuring secure delivery and compliance with organizational policies |
|  |  | - **Enable Expiration and Revocation** Administrators must configure custom branding templates using PowerShell—specifically the New-OMEConfiguration cmdlet with the -ExternalMailExpiryInDays parameter—to enforce how long external recipients can access encrypted emails via the encrypted message portal, after which access is automatically revoked |
|  |  | - **Test and Monitor** Administrators should validate mail flow rules and branding templates using test messages, then monitor encryption activity and revocation events through audit logs and reporting tools to ensure secure delivery and policy compliance |
| ☐ |  | [Customer Key](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-information-protection#customer-key) |
|  |  | Customer Key in Microsoft Purview Information Protection is a feature that allows organizations to add a second layer of encryption control by using their own encryption keys—hosted in Azure Key Vault—to protect Microsoft 365 data, enabling greater control over data access and compliance with specific regulatory or contractual requirements. |
|  |  | - **Prepare Azure Resources** Administrators must first configure Azure Key Vault and assign appropriate roles with minimal permissions, ensuring secure key management before enabling encryption policies across Microsoft 365 workloads |
|  |  | - **Assign Permissions** Administrators must configure Azure Key Vault access using role-based access control \(RBAC\), granting the necessary Get, Wrap Key, and Unwrap Key permissions to service principals or managed identities that require access to the encryption keys |
|  |  | - **Create Data Encryption Policies \(DEPs\)** Administrators use PowerShell cmdlets to define encryption hierarchies that apply customer-managed keys across Microsoft 365 workloads, ensuring that sensitive data—such as Exchange mailboxes, Teams messages, and EDM data—is encrypted according to organizational compliance requirements |
|  |  | - **Assign Policies to Workloads** Create and apply Data Encryption Policies \(DEPs\) tailored to specific services—such as Exchange Online, SharePoint, OneDrive, Teams, and Microsoft Purview Information Protection—ensuring that customer-managed keys are enforced across selected workloads for all tenant users |
|  |  | - **Monitor and Manage Keys** Administrators must use Azure Key Vault with managed identities—either system-assigned or user-assigned—to control key access, configure encryption at the cluster level for services like Azure Monitor, and track key usage and rotation through audit logs and compliance reports to ensure secure and compliant data protection across workloads |
|  |  | - **Optional: Roll Back to Microsoft-Managed Keys** To roll back from Customer Key to Microsoft-managed keys in Microsoft Purview, administrators must unassign Data Encryption Policies \(DEPs\) from workloads—such as using the Set-Mailbox -DataEncryptionPolicy $null cmdlet for Exchange—and ensure that Azure Key Vault keys remain accessible so data can be re-encrypted with Microsoft-managed keys, while also submitting a support request if multi-workload DEPs are involved. |

## Security compliance A5 add-ons

**[Security compliance A5 add-ons](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons)** in the A5 Education license provide advanced protection and governance capabilities—including Microsoft Defender for Endpoint, Defender for Office 365, Defender for Identity, Defender for Cloud Apps, and Microsoft Purview tools for Insider Risk Management, eDiscovery, Audit, and Information Protection—designed to help educational institutions like yours manage threats, secure data, and meet regulatory requirements across Microsoft 365 environments.

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Microsoft 365 A5 - Security](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons#microsoft-365-a5---security) |
|  |  | Microsoft 365 A5 Security is a comprehensive suite designed for educational institutions that combines advanced threat protection, identity and access management, information protection, and compliance tools—such as Microsoft Defender for Endpoint, Defender for Office 365, and Microsoft Purview—to help detect, prevent, and respond to cybersecurity threats while ensuring secure collaboration and regulatory compliance. |
| ☐ |  | [Microsoft 365 A5 - Compliance](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons#microsoft-365-a5---compliance) |
|  |  | Microsoft 365 A5 Compliance is an advanced suite tailored for educational institutions that enhances Microsoft 365 A3 by adding Microsoft Purview-powered capabilities for data lifecycle management, eDiscovery, auditing, insider risk management, and information protection—helping schools meet regulatory requirements like FERPA and GDPR while enabling secure collaboration and governance across Microsoft 365 workloads. |
| ☐ |  | [Microsoft 365 A5 - Information Protection and Governance](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons#microsoft-365-a5---information-protection-and-governance) |
|  |  | Microsoft 365 A5 – Information Protection and Governance provides advanced capabilities through Microsoft Purview to help organizations classify, label, protect, and govern sensitive data across Microsoft 365 services, ensuring compliance with regulatory requirements and reducing data loss risks through tools like sensitivity labels, data lifecycle management, and insider risk policies. |
| ☐ |  | [Microsoft 365 A5 - Insider Risk Management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons#microsoft-365-a5---insider-risk-management) |
|  |  | Microsoft 365 A5 – Insider Risk Management enables organizations to detect, investigate, and respond to potential internal threats—such as data leaks or IP theft—by correlating user activity signals across Microsoft 365, applying privacy-preserving analytics, and enforcing policies through Microsoft Purview’s adaptive protection and role-based access controls. |
| ☐ |  | [Microsoft 365 A5 - eDiscovery and Audit](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-compliance-a5-addons#microsoft-365-a5---ediscovery-and-audit) |
|  |  | Microsoft 365 A5 – eDiscovery and Audit equips organizations with advanced tools in Microsoft Purview to identify, preserve, search, and analyze content across Microsoft 365 services for legal, regulatory, and internal investigations, while enabling comprehensive audit logging and retention policies to support compliance and forensic readiness. |
