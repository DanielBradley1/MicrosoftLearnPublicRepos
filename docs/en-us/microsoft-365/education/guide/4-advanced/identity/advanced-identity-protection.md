<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 3: Identity protection

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides advanced guidance for educational institutions on implementing identity protection with a Microsoft 365 A5 license. It covers risk-based conditional access, step-up authentication, device and application filters, token protection, and best practices for investigating identity-related risks. The goal is to help IT and security teams secure student, faculty, and staff identities while supporting compliance and modern learning environments.

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

## Risk-based conditional access \(sign-in risk, user risk\)

**What is risk-based Conditional Access?**

Risk-based conditional access is a security feature in Microsoft Entra ID Protection that dynamically evaluates the risk level of sign-ins and user accounts, then enforces access policies based on that risk. It helps educational institutions protect sensitive data and systems by automatically responding to suspicious activity without requiring constant manual oversight.

This capability is especially critical in education, where users \(students, faculty, staff, and guests\) often access resources from a wide range of devices and locations.

**Two Core Risk Types:**

| Risk Type | Description | Example Triggers | Recommended Action |
| --- | --- | --- | --- |
| Sign-in Risk | The probability that a specific authentication attempt isn't legitimate | Unfamiliar sign-in properties, anonymous IPs, atypical travel, malware-linked IPs | Require MFA or block access |
| User Risk | The probability that a user account is compromised | Leaked credentials, repeated risky sign-ins, suspicious behavior | Require secure password change with MFA or block access |

**How it works in education:**

- Real-time detection: Microsoft Entra ID Protection analyzes hundreds of signals during each sign-in to calculate a risk score.
- Policy enforcement: Based on the risk level, Conditional Access policies can:

  - Block access
  - Require multifactor authentication \(MFA\)
  - Require a secure password reset

- Self-remediation: Users can resolve some risks themselves \(for example, by completing MFA\), reducing IT burden.

**Education-specific benefits:**

- Protects student and faculty identities from phishing, credential theft, and unauthorized access.
- Supports hybrid learning by securing access across personal and institutional devices.
- Reduces IT workload through automated risk detection and remediation.
- Improves compliance with FERPA, GDPR, and other data protection regulations.

**Licensing and deployment:**

- Included in Microsoft 365 A5: Risk-based Conditional Access is part of Microsoft Entra ID Plan 2, which is bundled with A5 education licenses.
- Add-on for A3: Institutions using A3 can purchase Microsoft Entra ID Plan 2 to enable this feature.
- Works with third-party IdPs: Supports federated identity environments common in education.

**Limitations for B2B and guest users:**

While risk-based policies can be applied to B2B users, they have limitations:

- Guest users can't reset passwords in the resource directory.
- Risky guest users don't appear in the local risky user reports.
- Admins can't dismiss or remediate guest user risks from the resource tenant

## Authentication context \(step-up authentication\)

**What is authentication context?**

Authentication context is a feature in Microsoft Entra Conditional Access that enables step-up authentication—a security mechanism that prompts users for stronger authentication \(like MFA or device compliance\) only when accessing sensitive data or performing high-risk actions within an application.

Instead of applying strict access policies at the app level, authentication context allows granular, in-app enforcement. This means users can access general features with standard credentials but must meet higher security requirements for privileged operations—like viewing student records, accessing financial data, or modifying grading systems.

**How it works in education:**

- Role-based access: For example, a teacher accessing general Teams content might not need MFA, but accessing a SharePoint site with student individualized education programs \(IEPs\) would trigger a step-up.
- Data sensitivity enforcement: Accessing sensitive Power BI dashboards or administrative portals can require compliant devices or trusted IPs.
- Minimized user friction: Students and staff aren’t overburdened with MFA prompts unless necessary, improving usability while maintaining security.

**Key capabilities:**

| Feature | Description |
| --- | --- |
| Granular conditional access | Apply policies to specific actions or data within an app, not just the app as a whole |
| Step-up authentication | Trigger stronger authentication \(for example, MFA, compliant device\) only when needed |
| Developer integration | Apps using OpenID Connect can invoke authentication context to enforce policies dynamically |
| Zero Trust alignment | Supports least-privilege access and real-time risk evaluation |

**Education-specific use cases:**

- Student information systems \(SIS\): Require MFA when accessing or editing student health or disciplinary records.
- Financial aid portals: Enforce device compliance for staff accessing sensitive financial data.
- Faculty portals: Trigger step-up when modifying grades or accessing HR records.

**Deployment considerations:**

- Define access packages and sensitivity labels for resources.
- Use Microsoft Entra Conditional Access policies to bind authentication context to specific actions.
- Ensure apps are integrated with OpenID Connect and support claims challenges.

## Device and application filters for Microsoft Entra Conditional Access

Device and application filters are advanced conditions in Microsoft Entra Conditional Access that allow IT administrators to target or exclude specific devices or applications when enforcing access policies. These filters enable granular control over who can access what, from where, and under what conditions—critical for securing educational environments with diverse device types and user roles.

**Device filters:**

Device filters evaluate access based on device attributes registered in Microsoft Entra ID. These attributes include:

- device.operatingSystem
- device.trustType
- device.extensionAttributes1–15
- device.isCompliant
- device.managementType \(for example, Intune-managed\)

**Use cases in education:**

- Block access from unmanaged student devices while allowing compliant faculty laptops.
- Allow access only from Intune-managed lab computers.
- Exclude Teams Phones or Surface Hubs from MFA requirements for service accounts.

**Policy Behavior:**

- Filters apply only to registered devices.
- When using extensionAttributes, the device must be compliant or hybrid joined.
- Unregistered devices aren't evaluated by the filter and are excluded from policy enforcement.

**Application filters \(preview\):**

Application filters allow Conditional Access policies to target specific applications based on custom attributes assigned to their service principals. This is useful when:

- You want to apply different policies to apps with similar names or functions.
- You need to enforce stricter controls on high-risk apps \(for example, grading systems, SIS platforms\).

**Use cases in education:**

- Require MFA for accessing financial aid systems, but not for general learning portals.
- Block access to legacy or unapproved apps used by students.

**Integration with Microsoft Defender for Cloud Apps:**

In education, these filters are often used in tandem with Microsoft Defender for Cloud Apps to:

- Detect and block Shadow IT \(unauthorized apps\).
- Apply session-level controls \(for example, block downloads, monitor uploads\).
- Enforce real-time Conditional Access App Control based on device or app risk.

**Practical implementation guidance:**

- Define device compliance policies in Microsoft Intune.
- Use device filters to enforce access only from compliant or hybrid-joined devices.
- Use application filters to tag and control access to sensitive apps.
- Combine with risk-based policies for dynamic enforcement.

## Token Protection

**What is token protection?**

Token protection is a security feature in Microsoft Entra ID \(formerly Azure AD\) that helps prevent token theft and replay attacks by binding authentication tokens to specific conditions—such as the device, user, or session context. It ensures that even if a token is stolen, it can't be reused from a different device or location. This is important in education, where students, faculty, and staff often access cloud resources from personal or shared devices, increasing the risk of token compromise.

**Why it matters in education:**

- Prevent lateral movement by attackers who gain access to a token.
- Secure hybrid learning by ensuring tokens are only valid on trusted or compliant devices.
- Support Zero Trust by enforcing strong identity and device verification before granting access to sensitive systems like SIS, LMS, or financial aid portals.

**Key capabilities:**

| Capability | Description |
| --- | --- |
| Token binding | Ties tokens to a specific device or session, preventing reuse elsewhere |
| Session revocation | Automatically invalidates tokens when risk is detected \(for example, sign-in from a new country/region or risky IP\) |
| Integration with Conditional Access | Works with Conditional Access policies to enforce token protection based on risk, device compliance, or app sensitivity |
| Support for risk-based policies | Enhances protection when combined with Microsoft Entra ID Protection and Intune compliance policies |

**Education-specific use cases:**

- Block token reuse from unmanaged student devices.
- Force re-authentication if a session token is used from a new country/region or flagged IP address.
- Protect access to Microsoft 365 A5 EDU workloads, including Teams, SharePoint, and Exchange Online.

**Deployment guidance:**

- Ensure licensing: Requires Microsoft Entra ID Plan 2 \(included in Microsoft 365 A5\).
- Enable Conditional Access policies: Define rules that enforce token binding and session controls.
- Use Intune and Defender for Endpoint: Harden devices and enforce compliance before issuing tokens.
- Educate IT staff: Many institutions underutilize these features due to lack of awareness or training.

## Vulnerabilities and risky accounts

In the context of Microsoft Entra and Defender for Education, vulnerabilities refer to weaknesses in systems, configurations, or software that could be exploited by attackers. Risky accounts are user identities flagged due to suspicious or compromised behavior—such as leaked credentials, unusual sign-ins, or malware-linked activity.

These risks are critical in education, where institutions manage large, dynamic populations of students, faculty, and staff—often with limited IT resources and a high volume of unmanaged or BYOD devices.

**Risky accounts in Microsoft Entra ID Protection:**

- Risky users: Accounts flagged due to leaked credentials, repeated risky sign-ins, or suspicious behavior.
- Risky sign-ins: Authentication attempts from unfamiliar locations, anonymous IPs, or malware-associated infrastructure.
- Risk detections: Events like impossible travel, atypical token usage, or unfamiliar sign-in properties.

Admins can investigate these risks using the Risky Users Report in the Microsoft Entra admin center, which provides detailed history, risk level, and remediation options such as password reset or MFA enforcement.

**Microsoft Defender Vulnerability Management in education:**

- Discover vulnerabilities across devices, browsers, firmware, and certificates.
- Prioritize risks using severity, exploitability, and exposure data.
- Remediate issues via Intune or Endpoint Manager with one-click workflows.
- Block vulnerable applications or warn users before launch.

This is useful in education where unmanaged devices and legacy systems are common, and where IT teams must balance security with usability and budget constraints.

**Education-specific challenges and solutions:**

- High BYOD usage: 90% of ransomware attacks in EDU begin on unmanaged devices.
- Young users: Students as young as 5 may use school systems, requiring age-appropriate security controls.
- Scale and churn: Frequent user turnover and large tenant sizes \(often millions of users\) complicate identity lifecycle management

Solutions include:

- BYOD Security Agents that enforce privacy and security settings for minors.
- Secure Testing Agents that lock down devices during assessments.
- Conditional Access with risk-based policies to block or challenge risky users.

**Licensing and integration:**

- Microsoft Entra ID Plan 2 \(included in Microsoft 365 A5\) is required for full risk detection and remediation capabilities.
- Microsoft Defender for Endpoint integrates with Microsoft Entra ID to provide unified visibility and control over vulnerabilities and risky accounts.

## Risk event investigation

Risk event investigation refers to the structured process of identifying, analyzing, and responding to identity-related security threats—such as compromised accounts, suspicious sign-ins, or insider risks—within educational institutions. This process is critical for protecting sensitive student and faculty data, maintaining compliance, and ensuring operational continuity.

**Core process of risk event investigation:**

- Monitoring risk reports: These include risky users, risky sign-ins, workload identities, and risk detections.
- Filtering and analyzing events: Admins can filter by risk level, detection type, and user attributes to prioritize investigations.
- Reviewing risk history: Each user’s risk timeline shows what triggered the risk \(for example, leaked credentials, unfamiliar sign-in\) and what actions were taken \(for example, password reset, MFA challenge\).
- Taking remediation actions: Admins can confirm or dismiss risks, reset passwords, or enforce Conditional Access policies.

This process is supported by downloadable reports and integrations with SIEM tools and Microsoft Defender, enabling deeper analysis and automation.

**Education-specific guidance and tools:**

- The five-stage investigation model:

  - Triage: Define scope, impact, and severity.
  - Evidence gathering: Collect and preserve logs and artifacts.
  - Root cause analysis: Identify how the incident occurred.
  - Remediation: Contain and resolve the issue.
  - Review: Update policies and training to prevent recurrence.

- Emphasize compliance with OSHA and internal safety protocols, including mandatory reporting and documentation of incidents involving data or physical safety.
- Microsoft Purview Insider Risk Management helps detect and investigate internal threats like data leaks or policy violations using machine learning and pseudonymized data.

**Tools and enhancements:**

- Copilot for Security: Offers natural language summaries of risk events, including why a user’s risk level was elevated and recommended next steps.
- On-demand assessments: Helps proactively identify misconfigurations and vulnerabilities in Microsoft Entra ID environments.

**Best practices for education institutions:**

- Start with high-risk users: Prioritize those with multiple detections or confirmed credential leaks.
- Automate where possible: Use Conditional Access and Identity Protection policies to enforce MFA or block access based on risk.
- Document and communicate: Maintain clear records of investigations and share findings with relevant teams.
- Train staff: Ensure IT and security teams are familiar with investigation workflows and tools.
