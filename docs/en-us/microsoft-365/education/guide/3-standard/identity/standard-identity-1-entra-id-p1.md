<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/identity/standard-identity-1-entra-id-p1 -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 1: Microsoft Entra ID Plan 1

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

This article provides an overview of Microsoft Entra ID Plan 1, a comprehensive identity and access management solution designed for educational institutions. It covers the key features, requirements, roles, and responsibilities associated with Microsoft Entra ID P1, and includes detailed comparisons with other Microsoft Entra ID plans.

## Requirements

- Microsoft A3 license
- Microsoft Entra ID Plan 1

## Roles and responsibilities

- IT Admin
- Identity Admin

## Microsoft Entra ID P1

Microsoft Entra ID P1 is a powerful identity and access management solution that offers significant benefits for educational institutions. It provides advanced security features such as conditional access, which helps protect sensitive data by ensuring that only authorized users can access specific resources based on predefined conditions. This is useful in education, where safeguarding student information and academic records is paramount. Additionally, Microsoft Entra ID P1 supports dynamic group management, allowing administrators to automate group memberships based on specific criteria, which simplifies user management and enhances operational efficiency. With features like multifactor authentication and role-based access control, educational institutions can ensure secure and streamlined access to their digital resources, fostering a safe and productive learning environment.

**Key features of Microsoft Entra ID P1 in education:**

- **Conditional Access:** Ensures that only authorized users can access specific resources based on predefined conditions.
- **Multi-factor authentication \(MFA\):** Adds an extra layer of security by requiring multiple forms of verification.
- **Dynamic group management:** Automates group memberships based on specific criteria, simplifying user management.
- **Role-based access control \(RBAC\):** Allows administrators to assign permissions based on user roles, enhancing security and efficiency.
- **Self-service password reset:** Enables users to reset their passwords without IT assistance, reducing administrative workload.
- **Application proxy:** Provides secure remote access to on-premises web applications.
- **Identity protection:** Detects and responds to identity-based threats, safeguarding sensitive information.
- **Single sign-on \(SSO\):** Allows users to access multiple applications with one set of credentials, improving user experience

## Microsoft Entra ID A3 features and products

| Feature | Description | Learn more Links |
| --- | --- | --- |
| **Fraud Alert** | Allow users to report fraud attempts via unknown MFA prompts | [Configure Microsoft Entra multifactor authentication settings](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-mfasettings#fraud-alert) |
| **MFA Reports** | Review MFA events and sign-ins | [Sign-in event details for Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-reporting) |
| **MFA Caller ID and Phone Greetings** | Configure phone call mfa with Caller ID and customer greetings | [Configure Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-mfasettings) |
| **Trusted IPs** | Configure CA with trusted locations and IP addresses | [Conditional Access: Network assignment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-assignment-network) |
| **ADFS Extranet lockout** | Protect against brute force password-guessing attacks, while letting valid AD FS users continue to use their accounts | [Secure your organization's identities with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/concept-secure-remote-workers) |
| **MFA for on prem apps** | Enable MFA for hybrid on-premises environments | [Microsoft Entra multifactor authentication versions and consumption plans - Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-licensing) |
| **Self Service Password Reset** | Empower users to reset and recover their own passwords | [Reset your work or school password using security info](https://support.microsoft.com/account-billing/reset-your-work-or-school-password-using-security-info-23dde81f-08bb-4776-ba72-e6b72b9dda9e) |
| **Banned Passwords for on prem AD** | Extend the banned password list to your on-premises directory | [Microsoft Entra Password Protection](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad-on-premises) |
| **CA - MFA for some users** | Enable Multi-factor auth for some users in your organization | [Deployment considerations for Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-getstarted) |
| **CA - Block Legacy Authentication** | Block legacy auth like POP, SMTP, IMAP, and MAPI w/o support for MFA | [Block legacy authentication with Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/block-legacy-authentication) |

## Microsoft Entra ID license comparison

| Feature | Microsoft Entra ID Free | Microsoft Entra ID P1 | Microsoft Entra ID P2 |
| --- | --- | :---: | --- |
| [**Conditional Access**](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) | No | **-Yes-** | Yes |
| [**Multi-Factor Authentication \(MFA\)**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks) | Yes \(basic\) | **-Yes-** | Yes |
| [**Dynamic Group Management**](https://learn.microsoft.com/en-us/entra/identity/users/groups-create-rule) | No | **-Yes-** | Yes |
| [**Role-Based Access Control \(RBAC\)**](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-overview) | Yes \(basic\) | **-Yes-** | Yes |
| [**Self-Service Password Reset**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sspr-howitworks) | Yes \(cloud users only\) | **-Yes-** | Yes |
| [**Application Proxy**](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) | No | **-Yes-** | Yes |
| Identity Protection | No | -No- | Yes \(includes risk-based Conditional Access\) |
| Privileged Identity Management \(PIM\) | No | -No- | Yes \(helps manage and monitor privileged accounts\) |
| Access Reviews | No | -No- | Yes |
| Entitlement Management | No | -No- | Yes |
| Identity Governance | No | -No- | Yes |
| [**Single Sign-On \(SSO\)**](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on) | Yes \(limited\) | **-Yes-** | Yes |
