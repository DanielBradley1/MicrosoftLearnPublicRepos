<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-data-lifecycle-management -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 3: Data lifecycle management with Microsoft 365 A5 for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

Data lifecycle management is a critical aspect of compliance and governance for educational institutions using Microsoft 365. This article provides an overview of the data lifecycle management features available for Microsoft 365 A5 for education, including rules-based automatic retention policies, Microsoft Purview Records Management, and machine learning-based retention.

## Requirements

- Microsoft 365 A5 license

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin
- Security Admin
- Compliance Admin

## Rules-based automatic retention policies

Rules-based automatic retention policies are part of the broader Microsoft Purview Data Lifecycle Management and Microsoft Purview Records Management capabilities included in the Microsoft 365 A5 education license. These tools help educational institutions automate the retention and deletion of data to meet compliance, legal, and operational requirements.

Rules-based automatic retention policies allow institutions to:

- Automatically apply retention labels to content based on conditions such as:

  - Keywords or sensitive info types \(for example, "student ID" and "transcript"\)
  - Content location \(for example, SharePoint, OneDrive, Exchange\)
  - Metadata \(for example, creation date, author, department\)

- Trigger retention or deletion actions after a specified period \(for example, retain for seven years, then delete\)
- Ensure immutability for records that must be preserved for legal or regulatory reasons

These policies are managed through:

- Microsoft Purview Data Lifecycle Management – for broad retention and deletion across Microsoft 365
- Microsoft Purview Records Management – for more advanced scenarios like regulatory record declaration and proof of immutability

**Benefits for education institutions:**

- FERPA and GDPR compliance: Automate data retention for student records, communications, and assessments.
- Operational efficiency: Reduce manual tagging and archiving by applying rules at scale.
- Risk reduction: Ensure sensitive data isn't retained longer than necessary, reducing exposure.
- Audit readiness: Maintain defensible records with audit trails and retention proof.

## Machine learning-based retention

Machine learning-based retention refers to the use of AI-powered classification models called trainable classifiers within Microsoft Purview to automatically identify and apply retention policies to content across Microsoft 365. This capability is part of the Microsoft 365 A5 Compliance suite, but with important licensing nuances for education customers.

**What are machine learning-based retention policies?**

These are intelligent, adaptive policies that use machine learning to classify content based on its meaning and context—not just keywords or metadata. Microsoft provides pre-trained classifiers \(for example, for harassment, profanity, or resumes\), and institutions can also train custom classifiers on their own data. Once trained, these classifiers can:

- Automatically apply retention labels to content \(for example, emails, documents, Teams chats\).
- Trigger retention or deletion actions based on the content type.
- Support compliance with regulations like FERPA, GDPR, and HIPAA.

**Licensing considerations:**

Microsoft 365 A5 for education includes:

- Rules-based auto classification
- Advanced Information Governance

However, it doesn't include:

- Machine Learning–based auto classification \(trainable classifiers\)

This means that while A5 customers can use rules-based retention \(for example, based on keywords or metadata\), they would need to purchase additional licensing \(such as Microsoft 365 E5 Compliance or Microsoft Purview add-ons\) to access trainable classifiers.

**Strategic benefits for education institutions \(when licensed\):**

| Benefit | Description |
| --- | --- |
| Scalable compliance | Automatically classify and retain student records, transcripts, or sensitive communications. |
| Reduced manual effort | No need for users or admins to manually tag content. |
| Improved accuracy | Learns from labeled examples to improve classification over time. |
| Audit-ready | Provides proof of classification and retention actions for legal or regulatory review. |

## Automatic sensitivity labeling in Microsoft 365 apps

**What is automatic sensitivity labeling?**

Automatic sensitivity labeling is a feature of Microsoft Purview Information Protection that uses predefined rules or machine learning to automatically classify and protect content—such as emails, documents, and Teams messages—based on its sensitivity. This ensures that sensitive data is consistently protected without relying on users to manually apply labels.

**How it works in Microsoft 365 Apps:**

There are two main methods for applying sensitivity labels automatically:

| Method | Where it Applies | How it Works |
| --- | --- | --- |
| Client-side labeling | Word, Excel, PowerPoint, Outlook | Labels are applied as users create or edit content. Labels can be auto-applied or recommended. Users can accept or override the label. |
| Service-side labeling | SharePoint, OneDrive, Exchange Online | Labels are applied to content at rest or in transit. No user interaction is required. Ideal for large-scale, organization-wide enforcement. |

**Why it matters in education:**

- Protect student records \(for example, FERPA compliance\)
- Secure faculty communications and research data
- Prevent data leaks through Teams, email, or shared documents
- Simplify compliance with GDPR, HIPAA, and other regulations

**Key features for educational institutions:**

- Labeling triggers: Based on sensitive info types \(for example, student ID, SSN\), keywords, or trainable classifiers
- Label actions: Can apply encryption, watermarks, headers/footers, and access restrictions
- Cross-app support: Works across Microsoft 365 apps including Word, Excel, PowerPoint, Outlook, Teams, SharePoint, and OneDrive
- Policy enforcement: Admins can enforce mandatory labeling or set defaults for specific users or groups

**Recent education-specific updates:**

- Viva Amplify now supports sending emails with sensitivity labels in Outlook, respecting admin-defined label policies.
- SharePoint Online supports sensitivity labels with user-defined permissions, enabling DLP and eDiscovery on labeled files.
- Education newsletters promote training on how to create and manage sensitivity labels for Teams and other apps.

## Automatic sensitivity labels in Exchange, OneDrive, and SharePoint

Automatic sensitivity labels in Exchange, SharePoint, and OneDrive are powered by Microsoft Purview Information Protection \(Plan 2\). This feature enables educational institutions to automatically classify and protect sensitive data across Microsoft 365 services without relying on manual user input.

**What it does:**

Automatic sensitivity labeling in these services works by scanning content for predefined conditions \(like sensitive info types or keywords\) and then applying the appropriate sensitivity label. This label can enforce:

- Encryption \(for example, restrict access to specific users or groups\)
- Visual markings \(headers, footers, watermarks\)
- Access restrictions \(for example, read-only, no forwarding\)

**Application in education:**

| Service | How Automatic Labeling Works |
| --- | --- |
| Exchange Online | Labels are applied to emails based on content \(for example, student ID, health info\). Can prevent forwarding or encrypt messages automatically. |
| SharePoint Online | Files stored in document libraries can be labeled automatically based on their content. Labels persist even when files are downloaded. |
| OneDrive | Automatically labels files stored in personal drives, especially useful for faculty and staff handling sensitive student or research data. |

**Benefits for education institutions:**

- FERPA and GDPR compliance: Automatically protect student records and personal data.
- Reduced human error: Ensures consistent labeling without relying on users.
- Secure collaboration: Enforces protection even when files are shared externally.
- Audits and visibility: Labels are logged and can be used in compliance reports and investigations.

This capability is included in the Microsoft 365 A5 for Education license under Microsoft Purview Information Protection \(Plan 2\)

## Default sensitivity labels for SharePoint document libraries

Sensitivity labels based on advanced classifiers in Microsoft 365 A5 for education refer to the use of machine learning-powered trainable classifiers to automatically detect and label sensitive content across Microsoft 365 apps—such as Exchange, SharePoint, OneDrive, and Teams—based on its meaning and context, not just keywords, or metadata.

**What are advanced \(trainable\) classifiers?**

Trainable classifiers are AI models that learn to recognize specific types of content by analyzing examples. Microsoft provides several pre-trained classifiers \(for example, for harassment, profanity, resumes\). Institutions can also create custom classifiers by training them on their own labeled data.

Once trained, these classifiers can:

- Automatically apply sensitivity labels to content that matches the classifier.
- Trigger data loss prevention \(DLP\) policies or retention rules.
- Help enforce compliance with regulations like FERPA, HIPAA, and GDPR.

**Use cases in education:**

| Use Case | Example |
| --- | --- |
| Student records | Automatically label documents containing transcripts, grades, or student IDs |
| HR and faculty files | Detect and label resumes, contracts, or disciplinary records |
| Research data | Identify and protect sensitive research or grant-related content |
| Policy enforcement | Flag and restrict sharing of content containing inappropriate language or confidential data |

**Licensing for education:**

According to internal Microsoft documentation, trainable classifiers aren't included by default in the Microsoft 365 A5 education license. They're part of Microsoft Purview Information Protection \(Plan 2\), but machine learning–based auto-classification may require an additional add-on license for education customers.

**Benefits for education institutions:**

- Improved accuracy: Goes beyond keyword matching to understand context
- Scalable protection: Automatically labels large volumes of content without user input
- Regulatory compliance: Helps meet FERPA, GDPR, and other mandates
- Reduced risk: Prevents accidental exposure of sensitive or regulated data

## Sensitivity labels based on advanced classifiers

**What Are Microsoft Sensitivity Labels?**

Microsoft Sensitivity Labels are part of the Microsoft Purview Information Protection \(MIP\) framework. They allow organizations to classify and protect data across Microsoft 365 apps and services—such as Word, Excel, PowerPoint, Outlook, SharePoint, Teams, and OneDrive—without hindering collaboration.

Labels can:

- Apply encryption and content markings \(headers, footers, watermarks\)
- Restrict access to content \(for example, internal-only, specific users/groups\)
- Control external sharing and device access
- Be applied manually by users or automatically via policies and classifiers

**How advanced classifiers work:**

Advanced classifiers—also known as trainable classifiers—use machine learning to identify sensitive content based on examples you provide. These classifiers are especially useful in education where content types vary widely and may include:

- Student records
- HR files
- Child protection documents
- Research data

To create a classifier:

1. Provide at least 50 positive and 150 negative sample documents.
2. Train the classifier to recognize patterns.
3. Use it to auto-apply sensitivity labels, retention policies, or compliance rules.

This is powerful in education where manual classification is impractical due to volume and diversity of content.

**Education-specific use cases:**

- Protect student personal data and health records \(for example, FERPA, HIPAA\)
- Secure HR and disciplinary files
- Manage access to research data and grant documents
- Control sharing of curriculum materials and assessments

For example, a label like “Highly Confidential – Student Data” might automatically apply to documents containing student IDs, grades, or health information, using a classifier trained on such content.

**Deployment and automation:**

You can configure and publish labels using Microsoft Purview. Labels can be:

- Default \(applied to all new content\)
- Recommended \(suggested to users\)
- Auto-applied \(based on content or classifier match\)

Admins can also apply labels to containers like Teams, SharePoint sites, and Microsoft 365 Groups to enforce access and sharing policies at the workspace level.

## Microsoft Purview Records Management

Microsoft Purview Records Management is a powerful compliance and governance tool designed to help educational institutions manage the lifecycle of their data in a secure, automated, and policy-driven way.

Microsoft Purview Records Management enables schools, colleges, and universities to:

- Declare records \(manually or automatically\) to ensure they're preserved in a tamper-proof state.
- Apply retention labels and policies to content across Microsoft 365 \(for example, Exchange, SharePoint, OneDrive, Teams\).
- Automate retention and deletion based on regulatory, legal, or institutional requirements.
- Ensure immutability of records to meet compliance standards like FERPA, GDPR, and HIPAA.

**Key capabilities for education:**

| Feature | Description |
| --- | --- |
| Retention labels | Automatically or manually apply labels to classify content as a record. |
| Event-based retention | Trigger retention based on events like graduation, resignation, or contract expiration. |
| Proof of disposition | Generate audit-ready logs showing when and why content was deleted. |
| Regulatory record declaration | Lock records to prevent edits or deletion, ensuring compliance with legal mandates. |
| Label inheritance | Apply retention labels to folders or libraries and have them cascade to content. |
| Disposition review | Route records to reviewers before deletion for final approval. |

**Strategic benefits for education institutions:**

- Compliance assurance: Helps meet education-specific mandates like FERPA and GDPR
- Operational efficiency: Reduces manual effort by automating retention and deletion
- Risk mitigation: Prevents premature deletion or unauthorized edits to critical records
- Audit readiness: Maintains defensible records with full audit trails and disposition logs

## Microsoft Purview Insider Risk Management

Microsoft Purview Insider Risk Management is a compliance and security solution included with Microsoft 365 A5 license for education. It helps schools, colleges, and universities detect, investigate, and mitigate internal risks, such as data leaks, policy violations, and insider threats—while maintaining user privacy.

**What is Insider Risk Management?**

Insider Risk Management uses machine learning and behavioral analytics to identify risky user activities across Microsoft 365 services. It enables institutions to proactively manage threats from within—whether accidental or intentional—by analyzing signals from email, Teams, SharePoint, OneDrive, and more.

**Capabilities included with the Microsoft 365 A5 license for education:**

| Feature | Description |
| --- | --- |
| Risk policy templates | Prebuilt templates for scenarios like data leaks, data theft by departing users, and security violations |
| HR connector integration | Triggers risk policies based on HR events like resignations or terminations |
| Data loss prevention \(DLP\) integration | Connects with Microsoft Purview Data Loss Prevention to trigger alerts based on high-severity incidents |
| Adaptive protection | Dynamically adjusts DLP enforcement based on user risk levels |
| Privacy controls | Pseudonymizes user identities during investigations to protect privacy |
| Alert management | Centralized dashboard for triage and investigating insider risk alerts |
| Automated remediation | Supports actions like user education, policy reminders, or escalation to security teams |

**Benefits for education institutions:**

- Protect student and faculty data: Detects unauthorized access or sharing of sensitive information like student records or research data
- Support compliance: Helps meet FERPA, GDPR, and other education-specific regulatory requirements
- Reduce investigation time: Automates detection and prioritization of high-risk activities, reducing manual effort
- Enable responsible AI use: Supports governance frameworks for AI tools like Copilot in education settings

## Purview EndPoint Data Loss Prevention \(DLP\)

Microsoft Endpoint Data Loss Prevention \(Endpoint DLP\) is a feature included in the Microsoft 365 A5 for education license. It extends traditional DLP capabilities to Windows 10 and 11 endpoints, allowing educational institutions to monitor and protect sensitive data directly on devices used by students, faculty, and staff.

**What is Endpoint DLP?**

Endpoint DLP helps prevent the accidental or intentional sharing of sensitive information by monitoring and controlling actions on endpoints such as:

- Copying data to USB drives
- Printing sensitive documents
- Uploading files to unauthorized cloud services
- Copying content to clipboard or third-party apps

It integrates with Microsoft Purview’s broader DLP policies, ensuring consistent enforcement across Exchange, SharePoint, OneDrive, Teams, and local devices.

**Why it matters in education:**

| Use Case | Benefit |
| --- | --- |
| Student records protection | Prevents unauthorized export or sharing of FERPA-protected data |
| Faculty research security | Blocks sensitive research data from being copied to personal devices or cloud apps |
| Device compliance | Ensures that school-issued laptops and desktops comply with institutional data handling policies |
| Remote learning security | Extends data protection to hybrid and remote learning environments |

**Key features:**

- Activity monitoring: Tracks actions like copy, paste, print, and file transfers
- Policy enforcement: Applies DLP rules based on content sensitivity and user risk level
- User notifications: Warns or blocks users in real time when risky actions are detected
- Audit logging: Captures detailed logs for compliance and investigation
