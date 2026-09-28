<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-cloud-access-security-broker -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 2: Cloud access security broker

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article outlines the key components of the advanced security capabilities for the Microsoft 365 A5 license for education, focusing on Microsoft Defender for Cloud Apps.

## Requirements

- Microsoft 365 A5 license
- Microsoft Defender for Cloud Apps

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin
- Security Admin
- Compliance Admin

## Microsoft Defender for Cloud Apps

**What is Microsoft Defender for Cloud Apps?**

Microsoft Defender for Cloud Apps \(formerly Microsoft Cloud App Security\) is a cloud access security broker \(CASB\) that provides deep visibility, strong data controls, and enhanced threat protection for cloud applications. In education, it helps institutions secure cloud usage across students, faculty, and staff whether apps are sanctioned or not.

**Key capabilities for education:**

| Capability | Description |
| --- | --- |
| Cloud App Discovery | Identifies all cloud apps in use, including unsanctioned "shadow IT," by analyzing traffic logs or integrating with Microsoft Defender for Endpoint |
| Risk assessment | Evaluates over 31,000 apps against 70+ risk factors \(for example, compliance, security posture, user behavior\) and assigns risk scores |
| App governance | Monitors OAuth permissions, detects overprivileged or unused apps, and enforces hygiene policies to reduce exposure |
| Threat protection | Detects anomalies like ransomware, compromised accounts, or data exfiltration using behavioral analytics |
| Information protection | Integrates with Microsoft Purview to classify and protect sensitive data across cloud apps, including third-party SaaS |
| Compliance monitoring | Ensures adherence to FERPA, COPPA, and other education-specific regulations by flagging risky or noncompliant apps |
| Policy enforcement | Enables real-time session control and conditional access via Microsoft Entra ID \(formerly Azure AD\), Intune, and Microsoft Defender for Endpoint |

**Strategic benefits for education institutions:**

- Secure shadow IT: Gain visibility into unsanctioned apps used by students and staff, and take action to block or govern them
- Protect sensitive data: Prevent data leaks of student records, research, and intellectual property
- Simplify compliance: Automate monitoring and enforcement of FERPA, GDPR, and HIPAA requirements
- Unify security stack: Integrates natively with Microsoft 365 A5, replacing fragmented third-party tools

**Deployment and integration:**

Defender for Cloud Apps integrates with:

- Microsoft Entra ID for conditional access and identity protection
- Microsoft Intune for device compliance
- Microsoft Defender for Endpoint for traffic-based app discovery and policy enforcement
