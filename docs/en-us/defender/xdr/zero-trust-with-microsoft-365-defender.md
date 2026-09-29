<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/zero-trust-with-microsoft-365-defender -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Zero Trust with Microsoft Defender XDR

**Applies to:**

- Microsoft Defender XDR

Microsoft Defender XDR contributes to a strong Zero Trust strategy and architecture by providing extended detection and response \(XDR\). Microsoft Defender XDR works together with other Microsoft XDR tools and services and can be integrated with Microsoft Sentinel as a security information and event management \(SIEM\) source for a complete XDR/SIEM solution.

Microsoft Defender XDR is an XDR solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your Microsoft 365 environment, including endpoints, email, applications, and identities.

[![Diagram that shows the Microsoft Defender XDR in the Zero Trust architecture.](https://learn.microsoft.com/en-us/defender-xdr/media/zero-trust-with-microsoft-365-defender/m365-zero-trust-architecture-defender.png)](https://learn.microsoft.com/en-us/defender-xdr/media/zero-trust-with-microsoft-365-defender/m365-zero-trust-architecture-defender.png#lightbox)

In the illustration: Microsoft Defender provides XDR capabilities for protecting:

- Endpoints, including laptops and mobile devices
- Data in Office 365, including email
- Cloud apps, including other SaaS apps that your organization uses
- On-premises Active Directory Domain Services \(AD DS\) and Active Directory Federated Services \(AD FS\) servers

Microsoft Defender helps you apply the principles of Zero Trust in the following ways:

| Zero Trust principle | Met by |
| --- | --- |
| Verify explicitly | Microsoft Defender provides XDR across users, identities, devices, apps, and emails. |
| Use least privileged access | If used with Microsoft Entra ID Protection, Microsoft Defender blocks users based on the level of risk posed by an identity. Microsoft Entra ID Protection is licensed separately from Microsoft Defender and is included with Microsoft Entra ID P2. |
| Assume breach | Microsoft Defender continuously scans the environment for threats and vulnerabilities. It can implement automated remediation tasks, including automated investigations and isolating endpoints. |

## Extend Zero Trust with unified security operations

Unified security operations in the Defender portal extends Zero Trust beyond Defender XDR:

- **Verify explicitly** by using Microsoft Sentinel analytics and automation, Defender Threat Intelligence enrichment, Microsoft Security Exposure Management context, Defender for Cloud signals, and Microsoft Entra ID Protection risk.
- **Use least privilege** with Defender unified role-based access control \(RBAC\), Microsoft Entra Privileged Identity Management \(PIM\), Conditional Access app control, and Security Copilot on-behalf-of authentication.
- **Assume breach** with Defender XDR automatic attack disruption, Microsoft Sentinel automation rules and playbooks, Defender for Cloud response capabilities, and Microsoft Entra risk notifications.

To add Microsoft Defender to your Zero Trust strategy and architecture, go to [Pilot and deploy Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-overview) for a methodical guide to piloting and deploying Microsoft Defender components. The following table summarizes what these topics include.

| Includes | Prerequisites | Doesn't include |
| --- | --- | --- |
| Set up the evaluation and pilot environment for all components:<br><br>- Defender for Identity<br>- Defender for Office 365<br>- Defender for Endpoint<br>- Microsoft Defender for Cloud Apps<br><br>  <br>Protect against threats  <br>  <br>Investigate and respond to threats | See the guidance for the architecture requirements for each component of Microsoft Defender. | Microsoft Entra ID Protection isn't included in this solution guide. It's included in [Step 1. Configure Zero Trust identity and device access protection](https://learn.microsoft.com/en-us/microsoft-365/security/microsoft-365-zero-trust#step-1-configure-zero-trust-identity-and-device-access-protection-starting-point-policies). |

## Next steps

Learn more about Zero Trust for Microsoft Defender services:

- [Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/zero-trust-with-microsoft-defender-endpoint)
- [Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/zero-trust-with-microsoft-365-defender-office-365)
- [Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/zero-trust)
- [Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/zero-trust)

Learn more about other Microsoft 365 capabilities that contribute to a strong Zero Trust strategy and architecture with the [Zero Trust deployment plan with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/security/microsoft-365-zero-trust).

Learn more about Zero Trust and how to build an enterprise-scale strategy and architecture with the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
