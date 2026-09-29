<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# What is Microsoft Defender XDR?

Microsoft Defender XDR is a unified pre- and post-breach enterprise defense suite that natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.

Microsoft Defender helps security teams protect their organizations and detect threats by using information from other Microsoft security products, including:

- [**Microsoft Defender for Endpoint**](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [**Microsoft Defender for Office 365**](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)
- [**Microsoft Defender for Identity**](https://learn.microsoft.com/en-us/defender-for-identity/what-is)
- [**Microsoft Defender for Cloud Apps**](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)
- [**Microsoft Defender Vulnerability Management**](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
- [**Microsoft Defender for Cloud**](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)
- [**Microsoft Entra ID Protection**](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection)
- [**Microsoft Data Loss Prevention**](https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-learn-about-dlp)
- [**App Governance**](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)
- [**Microsoft Purview Insider Risk Management**](https://learn.microsoft.com/en-us/purview/insider-risk-management-solution-overview)
- [**Microsoft Security Exposure Management**](https://learn.microsoft.com/en-us/security-exposure-management)

With the integrated Microsoft Defender solution, security professionals can stitch together the threat signals that each of these products receive and determine the full scope and impact of the threat; how it entered the environment, what it's affected, and how it's currently impacting the organization. Microsoft Defender takes automatic action to prevent or stop the attack and self-heal affected mailboxes, endpoints, and user identities.

Note

Microsoft Defender correlates signals from Microsoft security products that you have licensed and provisioned access to.

## Microsoft Defender protection

Microsoft Defender services protect:

- **Endpoints with Defender for Endpoint** - Microsoft Defender for Endpoint is a unified endpoint platform for preventative protection, post-breach detection, automated investigation, and response.
- **Assets with Defender Vulnerability Management** - Microsoft Defender Vulnerability Management delivers continuous asset visibility, intelligent risk-based assessments, and built-in remediation tools to help your security and IT teams prioritize and address critical vulnerabilities and misconfigurations across your organization.
- **Email and collaboration with Defender for Office 365** - Defender for Office 365 safeguards your organization against malicious threats posed by email messages, links \(URLs\) and collaboration tools.
- **Identities with Defender for Identity and Microsoft Entra ID Protection** - Microsoft Defender for Identity is a cloud-based security solution that uses your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization. Microsoft Entra ID Protection uses the learnings Microsoft acquired from their position in organizations with Microsoft Entra ID, the consumer space with Microsoft Accounts, and in gaming with Xbox to protect your users.
- **Applications with Defender for Cloud Apps** - Microsoft Defender for Cloud Apps is a comprehensive cross-SaaS solution bringing deep visibility, strong data controls, and enhanced threat protection to your cloud apps.

Microsoft Defender's unique cross-product layer augments the individual service components to:

- Help protect against attacks and coordinate defensive responses across the services through signal sharing and automated actions.
- Narrate the full story of the attack across product alerts, behaviors, and context for security teams by joining data on alerts, suspicious events and impacted assets to incidents.
- Automate response to compromise by triggering self-healing for impacted assets through automated remediation.
- Enable security teams to perform detailed and effective threat hunting over endpoint, identity, email, and cloud app data.

Microsoft Defender XDR cross-product features include:

- **Cross-product single pane of glass in the Microsoft Defender portal** - A central view for all information on detections, impacted assets, automated actions taken, and related evidence in a single queue and a single pane in [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139).
- **Combined incidents queue** - To help security professionals focus on what is critical by ensuring the full attack scope, impacted assets and automated remediation actions are grouped together and surfaced in a timely manner.
- **[Automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption)** - Microsoft Defender XDR correlates high-confidence signals from multiple workloads and automatically applies containment actions to stop in-progress attacks and limit lateral movement.

  For example, if a malicious file is detected on an endpoint protected by Defender for Endpoint, it instructs Defender for Office 365 to scan and remove the file from all email messages. The file is blocked on sight by the entire Microsoft 365 security suite.
- **Self-healing for compromised devices, user identities, and mailboxes** - Microsoft Defender uses AI-powered automatic actions and playbooks to remediate impacted assets back to a secure state. Microsoft Defender leverages automatic remediation capabilities of the suite products to ensure all impacted assets related to an incident are automatically remediated where possible.
- **Cross-product threat hunting** - Security teams can leverage their unique organizational knowledge to hunt for signs of compromise by creating their own custom queries over the raw data collected by the various protection products. Microsoft Defender XDR provides query-based access to 30 days of historic raw signals and alert data from Defender for Endpoint, Defender for Office 365, Defender for Identity, and Defender for Cloud Apps.

## Get started

Microsoft Defender XDR licensing requirements must be met before you can enable the service in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). For more information, see:

- [Licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements)
- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable)
- [Microsoft Defender XDR in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
