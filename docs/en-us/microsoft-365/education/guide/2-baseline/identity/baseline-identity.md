<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 1: Understand Identity definitions

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

After you created a tenant, populated it with users, and configured the domains, you're ready to configure the core identity services.

This article covers identity baseline configurations and best practices for education customers using Microsoft 365.

**Baseline Overview:** The identity baseline configuration focuses on advanced configuration of users, identity security, groups of various types, and identity related tenant configurations. All configurations within this baseline are available to every Education \(EDU\) verified tenant, for free, and within the A1 license entitlement.

## Prerequisites

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/license/a1.png) Microsoft 365 A1 for devices

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/products/entraid.png) Microsoft Entra ID - Basic

## Roles and responsibilities

- IT Admin
- Identity Admin
- EXO Admin
- OneDrive Admin
- SharePoint Admin

## Types of identity management systems \(IdM\) or Identity and access management systems \(IAM\)

| **System** | **Description** | **Examples** |
| --- | --- | --- |
| **Centralized Identity Management** | All user identities are stored in a central location, or single "source of truth." | Microsoft Entra ID Directory, LDAP, Lightweight Directory Access Protocol, Okta, Ping Identity, Zluri |
| **Decentralized Identity Management** | Decentralized identity management employs a distributed network to store and manage user identities. | Self-Sovereign Identity \(SSI\) for individuals, Decentralized Finance \(DEFI\), Identification Verification for Digital Onboarding, Healthcare Identity Management, Supply Chain Management, Voting and Elections, Access Control and Authentication, Digital Notarization |
| **Federated Identity Management** | Allows users to access resources across different organizations or domains using a single set of credentials. | Microsoft Active Directory Federated Service \(ADFS\), Microsoft Entra ID Federation, Okta, Google Cloud Identity, OneLogin |
| **Privileged Access Management \(PAM\)** | Focuses on managing privileged accounts and their access to critical systems. | Human Privileged accounts \(Super Users, Local Admins\), Non-Human Accounts \(Application and Service Accounts, Secure Socket Shell\), Privileged Levels, and Rights \(Read, Write, Execute, Modify, Delete, Create, and Administrative Rights\), Just-in-Time Access, Compliance and Reporting, Automating User Lifecycle, Monitoring, and Recording |
| **Customer Identity and Access Management \(CIAM\)** | Handles customer identities, registrations, authentication, and authorization for services such as online banking or e-commerce. | Preventing Fraudulent Activity, Amazon, Social Media Platforms \(Facebook, X\), Healthcare Portals, E-Commerce Platforms |
| **API Access Management** | Focuses on securing APIs \(Application Programming Interfaces\). It ensures proper authentication and authorization for API customers. | Okta API Access Management, Azure API Management, Custom Authorization Servers |
| **Web Access Management \(WAM\)** | Controls users access to web applications. They handle authentication, authorization, and sessions management for web-based services. | CA Technologies SiteMinder, Oblix Access Manager |

## Next steps

Next, you're ready review and configure Microsoft Entra ID basics.

[Next: Configure Microsoft Entra ID basics>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-entrabasics)
