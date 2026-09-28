<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Prepare for Microsoft Copilot by comparing E3, E5, and E7 license features

Choosing between Microsoft 365 E3, E5, and E7 licenses requires understanding the key feature differences that prepare your data for AI-powered productivity and enable your organization to operate at the frontier of agentic AI.

The Microsoft 365 E3, E5, and E7 licenses offer different features that help you get your data ready for Copilot. These features can:

- Help prevent oversharing
- Declutter data sources
- Identify and label sensitive data in your Microsoft 365 app files
- Enable your security team to implement agentic AI workflows securely
- Help govern AI agents at enterprise scale \(E7\)
- Extend identity and network access controls to users, apps, and agents \(E7\)

This article helps you understand the features available to your organization based on [your license](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing). If your organization is not yet licensed, this article can also help you decide. Choose which license is right for you based on the features your organization wants and needs.

This article applies to:

- Microsoft Copilot
- Microsoft Purview
- Microsoft SharePoint Advanced Management
- Microsoft Security Copilot
- Microsoft Entra Suite
- Microsoft Agent 365

## What's in each license?

Before diving into the feature comparison, it helps to understand what each license tier includes:

| Component | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| **Core productivity apps** | ✅ | ✅ | ✅ |
| **Microsoft Copilot** | Add-on available | Add-on available | ✅ Included |
| **Security baseline** | Entra ID P1, Defender basics | Entra ID P2, full Defender XDR | Full Entra Suite + Agent security |
| **Compliance baseline** | Core Purview | Advanced Purview | Advanced Purview + agentic governance |
| **Microsoft Entra Suite** | — | Entra ID P2 only | ✅ Full Suite |
| **Agent 365** | — | — | ✅ Included |
| **Security Copilot** | — | ✅ | ✅ |

Note

Microsoft 365 E7 \(the "Frontier Suite"\) became generally available on May 1, 2026. E7 = E5 + Microsoft Copilot + Microsoft Entra Suite + Agent 365 in a single SKU. E7 is a strict superset of E5, it only adds capabilities, it never removes them.

## Microsoft 365 E3 vs E5 vs E7 license features

The following sections list some of the features that can help get your data ready for Copilot. These features affect Copilot results and can help you manage Copilot interactions.

For more information on these features, see [Copilot controls security and governance](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/security-governance).

Note

As of early 2025, SharePoint Advanced Management is included with your Microsoft Copilot license. Security Copilot is included with Microsoft 365 E5 and E7 licenses.

### Microsoft Purview features

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| [Sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels) | ✅<br><br>- Create custom labels<br>- Manually apply labels | ✅<br><br>- Create custom labels<br>- Create default labels and their policies<br>- Manually apply labels<br>- Automatically apply labels<br>- Apply labels to containers, like a SharePoint or Teams site | ✅<br><br>All E5 capabilities, plus:<br><br>- Label-aware agent interactions<br>- Sensitivity context flows to AI agents |
| [Data Loss Prevention \(DLP\)](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) | ✅<br><br>Policies can target:<br><br>- SharePoint<br>- Exchange<br>- OneDrive | ✅<br><br>Policies can target:<br><br>- SharePoint<br>- Exchange<br>- OneDrive<br>- Teams<br>- Endpoints | ✅<br><br>All E5 capabilities, plus:<br><br>- DLP policies extend to agent interactions<br>- Prevent loss of sensitive data across apps, agents, browsers, on-premises file shares, and endpoints |
| [Adaptive Protection](https://learn.microsoft.com/en-us/purview/insider-risk-management-adaptive-protection) | n/a | ✅ | ✅ |
| [Data lifecycle management](https://learn.microsoft.com/en-us/purview/data-lifecycle-management) | ✅<br><br>- Create retention policies<br>- Manually apply retention labels<br>- Use Content explorer | ✅<br><br>- Create retention policies<br>- Manually apply retention labels<br>- Automatically apply retention labels<br>- Use Content explorer<br>- Use Activity explorer<br>- Use Data Lifecycle Management or Records Management | ✅<br><br>All E5 capabilities, plus:<br><br>- Classify and govern data at scale across agents<br>- Manage the lifecycle of records with agentic audit trails |
| [Communication Compliance](https://learn.microsoft.com/en-us/purview/communication-compliance) | n/a | ✅ | ✅<br><br>Plus:<br><br>- Establish content safety controls to detect, retain, and investigate unethical agent interactions |
| [eDiscovery](https://learn.microsoft.com/en-us/purview/edisc) | ✅ Can search. | ✅ Can search and delete. | ✅ All E5 capabilities \(search and delete\), plus:<br><br>- Discover and manage agent interaction data for legal matters or internal investigations |
| [Data Security Posture Management \(DSPM\) for AI](https://learn.microsoft.com/en-us/purview/dspm-for-ai) | ✅<br><br>- View app info<br>- Export activity<br>- Turn on auditing | ✅<br><br>- View app info<br>- Export activity<br>- Turn on auditing<br>- View prompt & response | ✅<br><br>All E5 capabilities, plus:<br><br>- Gain visibility into AI-related data exposure<br>- Protect the data agents create and use from oversharing, leaks, and risky behavior |
| [Insider Risk Management](https://learn.microsoft.com/en-us/purview/insider-risk-management) | n/a | ✅ | ✅ Plus:<br><br>- Detect, investigate, and address potential insider risks related to agent activity |
| [Audit](https://learn.microsoft.com/en-us/purview/audit-solutions-overview) | ✅ Standard Audit | ✅ Advanced Audit \(up to 10-year retention\) | ✅<br><br>All E5 capabilities, plus:<br><br>- Strengthen visibility and traceability of agent actions and interactions with logging, reporting, and audit |
| [Compliance Manager](https://learn.microsoft.com/en-us/purview/compliance-manager) | ✅ Basic | ✅ Advanced | ✅ All E5 capabilities, plus:<br><br>- Streamline multicloud and regulatory compliance with agentic AI templates and step-by-step guidance |

For more information, see the following articles:

- [Learn about Microsoft Purview](https://learn.microsoft.com/en-us/purview/purview)
- [Microsoft Purview service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)

### SharePoint Advanced Management features

Note

SharePoint Advanced Management is included with your Microsoft Copilot license. For E3 and E5, this requires the Copilot add-on. For E7, Copilot \(and therefore SAM\) is included.

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Site ownership policy | ✅ | ✅ | ✅ |
| Site lifecycle management | ✅ | ✅ | ✅ |
| Data access governance \(DAG\) reports | ✅ | ✅ | ✅ |
| Restricted access control \(RAC\) | ✅ | ✅ | ✅ |
| Restricted content discoverability policy \(RCD\) | ✅ | ✅ | ✅ |
| Change history report | ✅ | ✅ | ✅ |

For more information, see the following articles:

- [SharePoint Advanced Management overview](https://learn.microsoft.com/en-us/sharepoint/advanced-management)
- [Microsoft SharePoint Advanced Management licensing](https://learn.microsoft.com/en-us/sharepoint/advanced-management#licensing)

### Security Copilot features

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Implement secure agentic AI workflows |  | ✅ | ✅ |
| Understand risks and manage security posture of the organization |  | ✅ | ✅ |
| Investigate and remediate threats |  | ✅ | ✅ |
| Define and manage security policies |  | ✅ | ✅ |
| Develop reports for stakeholders |  | ✅ | ✅ |
| Security Copilot features to support security and IT operations |  | ✅ | ✅ |

For more information, see the following articles:

- [Learn about Security Copilot inclusion in Microsoft 365 E5 subscription](https://learn.microsoft.com/en-us/copilot/security/security-copilot-inclusion)
- [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)
- [Security Copilot use cases and roles](https://learn.microsoft.com/en-us/copilot/security/use-case-role-overview)

### Microsoft Copilot in apps \(feature availability\)

E7 includes Microsoft Copilot natively. There is no add-on required. For E3 and E5, Copilot is available as a paid add-on. When the Copilot license is present \(either via add-on or E7\), the following features are available:

| Feature | E3 + Copilot add-on | E5 + Copilot add-on | E7 \(Copilot included\) |
| --- | --- | --- | --- |
| Microsoft Copilot app \(web, desktop, mobile\) | ✅ | ✅ | ✅ |
| Copilot Chat \(work data–grounded\) | ✅ | ✅ | ✅ |
| Copilot Search | ✅ | ✅ | ✅ |
| Copilot Notebooks | ✅ | ✅ | ✅ |
| Copilot Pages | ✅ | ✅ | ✅ |
| Copilot Prompt Gallery | ✅ | ✅ | ✅ |
| Copilot in Teams | ✅ | ✅ | ✅ |
| Copilot in Outlook | ✅ | ✅ | ✅ |
| Copilot in Word | ✅ | ✅ | ✅ |
| Copilot in Excel | ✅ | ✅ | ✅ |
| Copilot in PowerPoint | ✅ | ✅ | ✅ |
| Copilot in OneNote | ✅ | ✅ | ✅ |
| Copilot in Loop | ✅ | ✅ | ✅ |
| Copilot in Clipchamp | ✅ | ✅ | ✅ |
| Copilot in Whiteboard | ✅ | ✅ | ✅ |
| Copilot in OneDrive | ✅ | ✅ | ✅ |
| Copilot in SharePoint | ✅ | ✅ | ✅ |
| SharePoint agents | ✅ | ✅ | ✅ |
| Declarative Agents for Microsoft Copilot | ✅ | ✅ | ✅ |
| Microsoft 365 Copilot connectors | ✅ | ✅ | ✅ |
| Power Platform Connectors ¹ | ✅ | ✅ | ✅ |
| Microsoft Purview \(extended to Copilot data\) | ✅ | ✅ | ✅ |
| Viva Insights \(Copilot analytics\) | ✅ | ✅ | ✅ |

> ¹ Power Platform licenses are not included with Microsoft Copilot. For more information, see [Learn more about Power Platform licensing](https://learn.microsoft.com/en-us/power-platform/admin/pricing-billing-skus).

### Microsoft Agent 365 features

Microsoft Agent 365 is the control plane for AI agents, which is a new component included exclusively in Microsoft 365 E7. It enables organizations to centrally manage, govern, and secure AI agents across the enterprise.

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Centralized agent governance and visibility | — | — | ✅ |
| Agent Conditional Access and identity protection | — | — | ✅ |
| Agent lifecycle management \(provisioning → expiration\) | — | — | ✅ |
| Agent management rules \(bulk governance actions\) | — | — | ✅ |
| Agent Security Posture Management \(SPM\) | — | — | ✅ |
| Detect suspicious agent activity, alerts, and blocking | — | — | ✅ |
| Investigate and hunt for threats in agents with unified observability logs | — | — | ✅ |
| Agent access packages and entitlement management | — | — | ✅ |

Note

Agent 365 is also available as a standalone add-on. When included in E7, it is fully integrated with the Entra Suite and Purview for end-to-end agent governance.

For more information, see the following articles:

- [Agent settings in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings)
- [Secure and govern Microsoft Copilot agents](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-deployment)

### Microsoft Entra Suite features

Microsoft 365 E5 includes Entra ID Plan 2. E7 includes the **full Microsoft Entra Suite**, which adds several capabilities on top of Entra ID P2:

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Microsoft Entra ID | Plan 1 | Plan 2 | Plan 2 \(full Entra Suite\) |
| Conditional Access | ✅ Basic | ✅ Risk-based | ✅ Risk-based + agent-aware |
| Multi Factor Authentication | ✅ | ✅ | ✅ |
| Single sign-on \(SSO\) | ✅ | ✅ | ✅ |
| Privileged Identity Management \(PIM\) | — | ✅ | ✅ |
| Identity Protection \(risk detection\) | — | ✅ | ✅ |
| Access reviews and certifications | — | ✅ | ✅ |
| Entitlement management | — | ✅ | ✅ |
| Entra Internet Access \(Secure Web Gateway / AI Gateway\) | — | — | ✅ |
| Entra Private Access | — | — | ✅ |
| Entra ID Governance \(full — lifecycle workflows\) | — | — | ✅ |
| Entra Verified ID \(issuance and verification\) | — | — | ✅ |
| Universal continuous access evaluation | — | — | ✅ |
| Agent identity, Conditional Access, and access packages for agents | — | — | ✅ |

Note

The full Microsoft Entra Suite is also available as a standalone add-on \(requires Entra ID P1 or higher\). In E7, it is included at no additional cost.

### Threat protection comparison

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Antivirus and antimalware | ✅ | ✅ | ✅ |
| Email and collaboration security \(enhanced phishing protection\) | — | ✅ | ✅ |
| Extended detection and response \(XDR\) | — | ✅ | ✅ |
| Full endpoint security \(EDR + ransomware protection\) | — | ✅ | ✅ |
| Full SaaS security \(malicious OAuth app protection\) | — | ✅ | ✅ |
| Shadow IT discovery | ✅ Basic | ✅ | ✅ |
| Agent Security Posture Management \(SPM\) | — | — | ✅ |
| Detect suspicious agent activity and receive alerts / blocking | — | — | ✅ |
| Investigate and hunt for threats in agents \(unified observability logs\) | — | — | ✅ |

### Endpoint management comparison

| Feature | Microsoft 365 E3 | Microsoft 365 E5 | Microsoft 365 E7 |
| --- | --- | --- | --- |
| Cross-platform device management \(Intune\) | ✅ P1 | ✅ P1 + P2 | ✅ P1 + P2 |
| Endpoint security policy management and baselines | ✅ | ✅ | ✅ |
| Device compliance policies and conditional access enforcement | ✅ | ✅ | ✅ |
| Application protection policies and device configuration | ✅ | ✅ | ✅ |
| Endpoint analytics | ✅ | ✅ | ✅ |
| Windows 11 Enterprise | ✅ | ✅ | ✅ |
| Windows Autopilot | ✅ | ✅ | ✅ |

## Next step

The next step is to start using the features in your license:

- **E3 and E5 users:** See [Configure a secure and governed data foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot).
- **E7 users:** In addition to the above, explore [Agent settings in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings) and [Secure and govern Microsoft Copilot agents](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-deployment).

## Related content

- [Copilot controls overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/overview)
- [Microsoft Copilot licensing](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing)
- [Microsoft Copilot resources on Microsoft Adoption](https://adoption.microsoft.com/copilot)
- [Microsoft 365 E7 for Enterprise](https://www.microsoft.com/microsoft-365/enterprise/e7)
- [Compare Microsoft 365 Enterprise plans](https://www.microsoft.com/microsoft-365/enterprise/microsoft-365-plans-and-pricing)
- [Microsoft Security enterprise plan comparison](https://www.microsoft.com/security/pricing/enterprise-plans)
- [Introducing Microsoft 365 E7: The Frontier Suite \(Partner blog\)](https://microsoftpartners.microsoft.com/abs/Blog/?title=Introducing+Microsoft+365+E7%3A+The+Frontier+Suite)
