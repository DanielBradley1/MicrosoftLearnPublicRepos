<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-advanced/start-adv-identity -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Overview - Advanced identity for A5 licenses

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/advancedsm.png)

This article provides an overview of advanced identity features included with the Microsoft A5 education license.

## Microsoft Entra ID and Microsoft Entra ID Protection

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Microsoft Entra ID Plan 2](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity#microsoft-entra-id-p2) |
|  |  | - **Establish Identity Strategy and Stakeholders** - Begin by identifying key stakeholders \(for example, security owner, identity architect, application owners\) and defining roles using a RACI model to ensure accountability and alignment across business, IT, and compliance teams. |
|  |  | - **Assess Current Environment and Readiness** - Use tools like the Readiness Assessment Tool to evaluate your on-premises Active Directory \(AD\) environment and determine prerequisites for transitioning to Microsoft Entra ID. This includes identifying legacy dependencies, app compatibility, and device readiness. |
|  |  | - **Design Identity Architecture** - Define your identity architecture, including hybrid identity \(if applicable\), device join strategy \(for example, Entra join, hybrid join\), and authentication methods. Plan for Conditional Access, multifactor authentication \(MFA\), and passwordless sign-in. |
|  |  | - **Configure Microsoft Entra ID Protection and Governance** - Enable features like risk-based Conditional Access, Identity Protection, and lifecycle workflows. These are core to Plan 2 and help automate identity governance and secure access. |
|  |  | - **Migrate Applications and Integrate Workloads** - Plan and execute the migration of apps to Microsoft Entra ID using phased rollouts. Prioritize apps that support modern authentication and SSO. Use tools like the Application Activity Report to guide this process. |
|  |  | - **Deploy and Monitor Multifactor Authentication \(MFA\)** - Roll out MFA using Conditional Access policies. Start with pilot groups, then expand in waves. Use Microsoft Entra ID Protection to enforce registration and monitor risky sign-ins. |
|  |  | - **Implement Lifecycle Workflows and Access Reviews** - Automate user provisioning, deprovisioning, and access reviews using Microsoft Entra ID Governance capabilities. This ensures compliance and reduces manual overhead. |
|  |  | - **Monitor, Audit, and Optimize** - Use Microsoft Entra Connect Health, audit logs, and Identity Secure Score to monitor system health, detect anomalies, and continuously improve your identity posture. |
| ☐ |  | [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity#microsoft-entra-id-protection) |
|  |  | - **Engage Stakeholders and Define Roles** - Identify key stakeholders \(for example, security admins, identity architects\) and assign roles using least privilege principles. Use Privileged Identity Management \(PIM\) to manage just-in-time access. |
|  |  | - **Review Existing Risk Reports** - Before enabling policies, review current risk detections in the Microsoft Entra ID Protection dashboard to understand your baseline and investigate any suspicious activity. |
|  |  | - **Configure Risk-Based Policies** - Set up risk-based Conditional Access policies for: User risk: Block or require password reset for users flagged as high risk and Sign-in risk: Require MFA or block access based on real-time sign-in risk levels. |
|  |  | - **Enable Self-Remediation** - Allow users to self-remediate risk events \(for example, via password reset or MFA challenge\) to reduce admin overhead and improve response time. |
|  |  | - **Integrate with Microsoft Defender XDR** - Enhance detection by integrating with Microsoft Defender for Endpoint, Office 365, Identity, and Cloud Apps to enrich risk signals. |
|  |  | - **Test with Pilot Users** - Apply policies to a test group before full deployment to validate behavior and minimize disruption. |
|  |  | - **Monitor and Tune Policies** - Use Microsoft Sentinel, Azure Monitor, or other SIEM tools to track risk events and policy effectiveness. Adjust thresholds and actions as needed. |
|  |  | - **Communicate Changes to Users** - Proactively inform users about new sign-in experiences, MFA prompts, and remediation steps to ensure smooth adoption. |

## Microsoft Identity Governance

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Microsoft Identity Governance](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-governance) |
|  |  | - **Assess Identity Landscape and Define Governance Goals** - Begin by using the Identity Governance dashboard to assess your tenant’s current state—number of users, guest accounts, privileged roles, and app access—and define your governance objectives based on security, compliance, and productivity needs. |
|  |  | - **Automate the Identity Lifecycle** - Implement lifecycle automation for onboarding, role transitions, and offboarding. Use inbound provisioning from HR systems like Workday or SuccessFactors, and configure lifecycle workflows to trigger tasks such as welcome emails or temporary access passes. |
|  |  | - **Assign and Manage Access to Resources** - Use entitlement management to define access packages for employees and guests. Automate access requests, approvals, and expiration policies to ensure users only have access to what they need, when they need it. |
|  |  | - **Govern Guest and Partner Access** - Establish policies for external users by linking your tenant to a subscription for monthly active user \(MAU\) billing. Use access packages and reviews to manage guest access lifecycle and ensure compliance. |
|  |  | - **Secure and Govern Privileged Identities** - Protect high-risk accounts using Privileged Identity Management \(PIM\). Define just-in-time access, approval workflows, and audit trails for roles like Security Administrator. |
|  |  | - **Conduct Access Reviews and Monitor Compliance** - Schedule periodic access reviews for users, groups, and applications. Use built-in reports and dashboards to monitor policy coverage, identify gaps, and ensure continuous compliance. |
|  |  | - **Iterate and Improve with the Governance Dashboard** - Use the Identity Governance dashboard to track implementation progress, identify automation gaps, and take action using embedded links to documentation and configuration tools. |

## Microsoft identity protection

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Risk-based conditional access \(sign-in risk, user risk\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#risk-based-conditional-access-sign-in-risk-user-risk) - Uses real-time assessments of sign-in risk \(for example, unfamiliar location or device\) and user risk \(for example, leaked credentials or suspicious behavior\) to automatically enforce policies like MFA, password reset, or access blocking—helping organizations proactively mitigate identity threats while maintaining user productivity. |
| ☐ |  | [Authentication context \(step-up authentication\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#authentication-context-step-up-authentication) - Enables step-up authentication by requiring stronger access controls—such as multifactor authentication or compliant device checks—when users access sensitive apps or perform high-risk actions, based on the context of their session and Conditional Access policies. |
| ☐ |  | [Device and application filters for Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#device-and-application-filters-for-microsoft-entra-conditional-access) - Allows administrators to enforce granular access policies by targeting specific device attributes \(like compliance state or operating system\) and application properties \(such as app ID or publisher\), enabling precise control over which users can access resources under defined conditions. |
| ☐ |  | [Token Protection](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#token-protection) - Ensures that access tokens are cryptographically bound to the device they were issued on—preventing token theft and replay attacks—by enforcing Conditional Access policies that validate token use only from trusted, compliant endpoints. |
| ☐ |  | [Vulnerabilities and risky accounts](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#vulnerabilities-and-risky-accounts) - Vulnerabilities refer to weaknesses in configurations or systems that could be exploited, while risky accounts are user identities flagged due to suspicious behaviors—such as leaked credentials, atypical sign-ins, or malware-linked activity—detected through machine learning and threat intelligence to enable automated remediation and Conditional Access enforcement. |
| ☐ |  | [Risk event investigation](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-protection#risk-event-investigation) - Structured process of identifying, analyzing, and responding to suspicious identity-related activities—such as risky sign-ins, leaked credentials, or anomalous behavior—by using risk reports, user timelines, and remediation actions like password resets or Conditional Access enforcement to mitigate threats and maintain organizational security. |

## Microsoft Insider Risk Management

|  |  |  |
| --- | --- | --- |
| ☐ |  | [Microsoft risk management](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-insider-risk-management) - Enables schools to detect, investigate, and mitigate internal threats like data leaks or policy violations by analyzing user behavior across Microsoft 365 services, while preserving privacy and supporting compliance with regulations such as FERPA and GDPR. |
| ☐ |  | [Microsoft privileged access management \(PAM\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/4-advanced/identity/advanced-identity-insider-risk-management#microsoft-privileged-access-management) - Enables institutions to detect and mitigate internal threats—such as misuse of elevated permissions or unauthorized data access—by enforcing just-in-time access, monitoring privileged activities, and applying adaptive policies that protect sensitive student and faculty data while supporting compliance with FERPA and GDPR. |
