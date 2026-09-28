<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-information-protection -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 5: Information protection in Microsoft 365 A5 for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides an overview of advanced information protection capabilities available in the Microsoft 365 A5 license for education. It explains how educational institutions can use Microsoft Purview Information Protection to automatically classify, label, and secure sensitive data across Microsoft 365 apps and services.

## Requirements

- Microsoft 365 A5 license
- Microsoft Purview Information Protection
- Microsoft Purview Information Protection \(Plan 2\)

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin
- Security Admin
- Compliance Admin

## Advanced Message Encryption

Advanced Message Encryption \(AME\) in Microsoft 365 A5 is a powerful compliance and security feature that enhances how educational institutions protect sensitive email communications—especially when messages are sent to external recipients.

**What is Advanced Message Encryption?**

Microsoft Purview Advanced Message Encryption builds on Office Message Encryption \(OME\) by adding granular control, custom branding, and revocation capabilities. It's included in the Microsoft 365 A5 Education license and can also be added to A3 via the Information Protection and Governance add-on.

**Key capabilities for education institutions:**

| Feature | Description |
| --- | --- |
| Automatic encryption policies | Automatically encrypt emails containing sensitive data \(for example, student IDs, health records, financial info\) using DLP rules. |
| Custom branding | Customize the encrypted message portal and notification emails with your institution’s logo and colors. |
| Expiration dates | Set expiration dates for encrypted emails to limit how long recipients can access them. |
| Revocation | Revoke access to encrypted emails even after they’ve been sent, ensuring control over sensitive content. |
| Secure Web portal access | External recipients access encrypted messages through a secure Microsoft-hosted portal, with audit logging. |
| Multiple templates | Use different branding and policy templates for different departments or scenarios \(for example, HR, Registrar, Research\). |

**Why it matters in education:**

- FERPA and HIPAA compliance: Helps meet strict data protection requirements for student and health records
- Secure external collaboration: Enables safe communication with parents, vendors, and research partners
- Reduced risk: Prevents unauthorized access to sensitive emails, even after delivery
- Audit-ready: Tracks access and revocation events for compliance reporting

**Licensing:**

- Included: Microsoft 365 A5 for Education
- Add-on Required: For A3 customers, AME is available via the Microsoft 365 A5 Information Protection and Governance add-on

## Customer Key

Microsoft 365 Customer Key is a feature within the Microsoft Purview compliance suite that allows educational institutions to bring and manage their own encryption keys to protect data at rest across Microsoft 365 services. This capability is especially relevant for institutions with strict regulatory or data sovereignty requirements.

**What is Microsoft 365 Customer Key?**

Customer Key enables organizations to:

- Control encryption keys used to encrypt data at rest in Microsoft’s data centers.
- Assign specific keys to different Microsoft 365 workloads \(for example, Exchange Online, SharePoint Online, OneDrive\).
- Revoke access to encrypted data by deleting or disabling the associated key in Azure Key Vault.

This adds an extra layer of protection beyond Microsoft-managed encryption, giving institutions greater control over who can access their data—even Microsoft engineers.

**Use cases in education:**

| Scenario | How Customer Key Helps |
| --- | --- |
| FERPA/GDPR compliance | Ensures that student and faculty data is encrypted with institution-owned keys |
| Data sovereignty | Supports requirements to store and control encryption keys within a specific geographic region |
| Research data protection | Secures sensitive research data shared across departments or with external collaborators |
| Incident response | Allows revocation of access to encrypted data in case of a breach or legal hold |

**Key features:**

- Integration with Azure Key Vault: Institutions must set up and manage their keys in Azure.
- Policy-based assignment: Admins can assign keys to specific workloads or departments.
- Audit logging: All key usage and access events are logged for compliance and investigation.
- Multi-geo support: Enables key management across multiple geographic regions.

**Licensing requirements:**

According to the Microsoft 365 Education Service Description, Customer Key is included in Microsoft 365 A5 for Education, but not in A1 or A3. It may also be available through the Microsoft 365 E5 Compliance or Information Protection and Governance add-ons.
