<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 1: Identity and access management

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides an overview of advanced identity and access management capabilities available to educational institutions through the Microsoft 365 Education A5 license. It covers key features, licensing, and deployment considerations for tools such as Microsoft Entra ID P2 and Microsoft Entra ID Protection, helping IT administrators secure and manage user identities in a modern learning environment.

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

## Microsoft Entra ID P2

Microsoft Entra ID Plan 2 \(formerly Azure AD Premium P2\) is the most advanced tier of Microsoft’s identity and access management solution. It includes all features of Plan 1, plus advanced identity protection and governance capabilities. It's designed to help organizations manage identities securely and efficiently across cloud and on-premises environments.

In education, Microsoft Entra ID P2 is typically bundled with Microsoft 365 Education A5 licenses.

**Key features for education:**

- Identity Protection

  - Uses risk-based Conditional Access to detect and respond to identity threats in real time.
  - Protects student, faculty, and staff accounts from compromise using machine learning and behavioral analytics.

- Identity Governance

  - Includes Privileged Identity Management \(PIM\), entitlement management, access reviews, and lifecycle workflows.
  - Helps automate and audit access to sensitive resources like student records, research data, and administrative systems.

- Verified ID and External Collaboration

  - Enables secure collaboration with external partners, such as guest lecturers or research collaborators, using Verified ID and External ID capabilities.

- Integration with School Data Sync \(SDS\)

  - Supports automated provisioning of student and teacher accounts, class groups, and Teams using SIS data.

**Licensing and availability:**

- Included in Microsoft 365 Education A5: Microsoft Entra ID P2 is bundled with A5, making it accessible to many educational institutions without additional licensing.
- Add-on Options: Institutions with A3 or standalone P1 licenses can purchase Microsoft Entra ID Governance as an add-on.
- Microsoft Entra Suite: For broader needs, Microsoft Entra ID P2 is also part of the Microsoft Entra Suite, which includes additional services like Private Access and Internet Access.

**Deployment considerations:**

- Prerequisite: Microsoft Entra ID P1 is required to use P2 or the full Microsoft Entra Suite.
- Setup: Institutions can configure Microsoft Entra ID using Microsoft 365 admin center or Intune for Education. Integration with on-premises directories is supported via Entra Connect.
- Governance Add-ons: Some advanced governance features \(for example, Verified ID-based entitlement workflows\) may require additional licensing even with P2.

## Microsoft Entra ID Protection

**What is Microsoft Entra ID Protection?**

Microsoft Entra ID Protection \(formerly Azure AD Identity Protection\) is a cloud-based identity security solution that uses machine learning, threat intelligence, and behavioral analytics to detect and respond to identity-based risks in real time. It's included in the Microsoft Entra ID Plan 2 license and the broader Microsoft Entra Suite.

**Core capabilities:**

- Risk detection and classification

  - User risk: Probability that a user’s identity is compromised.
  - Sign-in risk: Probability that a sign-in attempt wasn’t performed by the legitimate user.
  - Workload identity risk: Risk associated with service principals or applications.

- Risk-based conditional Access

  - Automatically enforces policies based on detected risk levels \(for example, block access, require MFA, password reset\).
  - Supports real-time remediation and continuous risk evaluation.

- Threat intelligence integration

  - Uses Microsoft’s global threat intelligence and signals from Defender for Endpoint, Defender for Cloud Apps, and other sources.
  - Detects anomalies like atypical travel, leaked credentials, malicious IPs, and suspicious inbox rules.

**Why it matters in education:**

Education is one of the most targeted sectors for cyberattacks, especially phishing and credential theft. Microsoft Entra ID Protection helps institutions:

- Secure student, faculty, and staff identities.
- Meet compliance requirements for FERPA, HIPAA, and cybersecurity insurance.
- Enable secure remote learning and collaboration without compromising user experience.

**Example use cases:**

- Automatically block access for a student account showing sign-ins from multiple countries/regions within minutes.
- Require password reset for a teacher account flagged for leaked credentials.
- Enforce MFA for administrative staff when sign-in risk is medium or high.

**Limitations and considerations:**

- Third-Party MFA: Currently, third-party MFA solutions aren't fully supported with Microsoft Entra ID Protection’s automation. Custom controls are limited and still in preview.
- Licensing: Requires Microsoft Entra ID Plan 2 or Microsoft 365 A5 for Education. Not included in A1 or A3 tiers.

**Deployment in education:**

- Integration with School Data Sync \(SDS\): Supports automated provisioning and risk-based access for student and teacher accounts.
- Passwordless Options: Supports Windows Hello, Temporary Access Pass \(TAP\), and FIDO2 keys—ideal for students without phones.
- Monitoring and Reporting: Dashboards provide insights into attack patterns, risky sign-ins, and remediation effectiveness
