<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/security/advanced-security-threat-protection -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 8: Threat protection in Microsoft 365 A5 for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

Microsoft 365 A5 for education offers advanced security features to protect educational institutions from sophisticated cyber threats. This article outlines the key components of the advanced security threat protection included in the A5 license, focusing on Microsoft Defender for Identity and Safe Documents.

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

## Safe Documents

Microsoft Safe Documents is a premium security feature included with the Microsoft 365 A5 education license. It enhances protection for students, faculty, and staff by automatically scanning Microsoft Office documents opened in Protected View or Application Guard using the cloud backend of Microsoft Defender for Endpoint, even if Defender for Endpoint isn't installed on the local device.

**What does Safe Documents do?**

Safe Documents helps prevent users from accidentally opening malicious files by:

- Automatically scanning Office files \(Word, Excel, PowerPoint\) when opened in Protected View.
- Blocking users from exiting Protected View until the document is confirmed safe.
- Using Microsoft Defender for Endpoint’s cloud intelligence to assess threats in real time.
- Requiring no local Defender installation, making it ideal for education environments with diverse device setups.

**Why it matters in education:**

| Benefit | Impact |
| --- | --- |
| Student safety | Prevents students from opening malware-laden attachments or downloads |
| Faculty protection | Shields educators from phishing attempts embedded in Office files |
| Simplified IT management | Reduces the need for endpoint installations while maintaining strong protection |
| Compliance support | Helps meet FERPA, GDPR, and other data protection standards by reducing exposure to document-based threats |

**Licensing and requirements:**

- Included in Microsoft 365 A5 for Faculty and Students.
- Not included in Microsoft Defender for Office 365 standalone plans.
- Requirements:

  - Microsoft 365 Apps for enterprise \(formerly Office 365 ProPlus\), version 2004 or later.
  - Safe Documents must be enabled in the Microsoft Defender portal.
  - Appropriate admin roles \(for example, Security Administrator\) are required to configure settings.

## Microsoft Defender for Identity

Microsoft Defender for Identity, formerly known as Azure Advanced Threat Protection \(Azure ATP\), is a security solution included with the Microsoft 365 A5 education license. It's designed to help educational institutions detect and respond to identity-based threats across hybrid environments.

**What Does It Do?**

Microsoft Defender for Identity monitors and analyzes user activities and information across your on-premises Active Directory and Microsoft 365 environments. It uses behavioral analytics and machine learning to detect:

- Suspicious user behavior
- Compromised identities
- Lateral movement attempts
- Privilege escalation
- Pass-the-ticket and pass-the-hash attacks

**Why it matters in education:**

| Use Case | Benefit |
| --- | --- |
| Protect student and faculty accounts | Detects compromised credentials and insider threats in real time |
| Hybrid identity security | Monitors both on-premises Active Directory and cloud-based Microsoft Entra ID \(formerly Azure AD\) |
| Compliance readiness | Supports FERPA, GDPR, and HIPAA by securing identity infrastructure |
| Simplified investigation | Provides a timeline of suspicious activities and integrates with Microsoft Sentinel and Microsoft Defender XDR |

**Included in Microsoft 365 A5 for education:**

- Microsoft Defender for Endpoint \(Plan 2\)
- Microsoft Defender for Office 365 \(Plan 2\)
- Microsoft Defender for Cloud Apps
- Microsoft Purview Insider Risk Management
