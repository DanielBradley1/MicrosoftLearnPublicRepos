<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/security-microsoft-365-copilot -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Security for Microsoft Copilot

Note

**The Microsoft 365 Copilot app is now called Microsoft Copilot**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

Security is foundational to Microsoft's approach to Microsoft Copilot. This article explains how Microsoft secures Copilot and how it inherits Microsoft 365 security, compliance, and privacy protections.

[![Diagram depicting ways Microsoft secures Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/security-microsoft-365-copilot/microsoft-secures-copilot.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/security-microsoft-365-copilot/microsoft-secures-copilot.png#lightbox)

Note

This article describes Microsoft's security approach for Microsoft Copilot. It doesn't include deployment or data-readiness steps.

For rollout planning and readiness guidance, see [Configure a secure and governed data foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot).

For deep technical details about data flow, protections, and auditing, see:

- [Microsoft Copilot data protection architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing)
- [How does Microsoft Copilot work?](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture)

## Microsoft's defense-in-depth approach

Microsoft applies a multilayered, defense-in-depth strategy to secure Microsoft Copilot at every level, grounded in enterprise security, privacy, and compliance standards. This layered approach helps ensure that if one control is compromised, other protections remain in place.

For more information, see [Microsoft Copilot prompt defense in depth](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-prompt-defense-in-depth).

## Identity and access protection

Microsoft Copilot is built on Microsoft 365 identity and access controls and aligns with Zero Trust principles such as strong identity verification, least-privilege access, and continuous evaluation.

For more information, see [Apply principles of Zero Trust to Microsoft Copilot](https://learn.microsoft.com/en-us/security/zero-trust/copilots/zero-trust-microsoft-365-copilot).

## Data protection and compliance

Microsoft Copilot honors your organization's existing security and data protection controls. Copilot only accesses data that users are authorized to access, and it respects Microsoft 365 compliance, privacy, and data residency commitments.

For more information, see [How data is protected and audited in Microsoft 365 and Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing).

### Enterprise data protection

Enterprise data protection \(EDP\) describes the contractual and technical commitments that apply to customer data for Microsoft Copilot and Microsoft Copilot Chat under Microsoft Product Terms and the Data Protection Addendum.

For details, see the following articles:

- [Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)

## Preventing oversharing

Microsoft Copilot operates within existing permissions and access controls. Overshared or poorly governed content can affect Copilot results and increase risk.

For prescriptive remediation guidance, see the following articles:

- [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance)
- [How to configure a secure and governed foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot)
- [Get ready for Microsoft Copilot and agents with SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/get-ready-copilot-sharepoint-advanced-management)

## Security dashboard

Microsoft Copilot includes built-in security controls from [Microsoft Purview](https://learn.microsoft.com/en-us/purview/ai-m365-copilot). To help you monitor, investigate, and act on AI-related risk, Microsoft provides **two complementary dashboards**:

- The [**Copilot security dashboard** in the Microsoft 365 admin center](#copilot-security-dashboard-in-the-microsoft-365-admin-center) focuses on Microsoft Copilot data protection, oversharing, and compliance insights.
- The [**Microsoft Security Dashboard for AI**](#microsoft-security-dashboard-for-ai) provides a cross-product view of AI risk that spans Microsoft Copilot, Copilot Studio agents, Microsoft Foundry apps and agents, and third-party AI apps and agents.

Use the Microsoft 365 admin center dashboard for day-to-day Copilot data governance, and use the Security Dashboard for AI when you need a unified, organization-wide view of AI security posture across Microsoft Defender, Microsoft Entra, and Microsoft Purview.

### Copilot security dashboard in the Microsoft 365 admin center

The Copilot security dashboard provides insights and controls to help you:

- Prevent data leaks with a [data loss prevention \(DLP\) policy](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about).
- Manage data oversharing.
- Strengthen data compliance.

To view the dashboard in the [Microsoft 365 admin center](https://admin.microsoft.com/), select **Copilot** > **Overview** > **Security**.

To display the **Security** section, you need the [Global Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) role. To make changes, the [AI administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) role is required.

### Microsoft Security Dashboard for AI

**Microsoft Security Dashboard for AI** is a unified dashboard that helps CISOs and AI risk leaders understand and address AI risk across the enterprise. It aggregates posture and real-time risk signals from **Microsoft Defender**, **Microsoft Entra**, and **Microsoft Purview** into a single interactive experience. Security leaders can govern and collaborate while security teams continue to work in the tools they already use.

The dashboard provides:

- **Real-time AI risk visibility.** An AI risk scorecard on the Overview tab highlights where risks exist and assesses your organization's implementation of Microsoft security-for-AI capabilities.
- **Comprehensive AI inventory.** Broad coverage of AI assets, including:

  - Microsoft Copilot
  - Microsoft Copilot Studio agents
  - Microsoft Foundry applications and agents
  - Third-party AI models, applications, and agents such as Google Gemini, OpenAI ChatGPT, and MCP servers
  - Unmanaged and shadow AI agents discovered in your environment

- **AI-powered insights with Security Copilot.** Suggested prompts help you drill down into risk assessments, correlate identity, data, and security signals, and prioritize the incidents that matter most for Microsoft Copilot and related agentic workloads.
- **Tailored recommendations and remediation paths.** The dashboard surfaces prioritized recommendations, supports **task delegation**, and integrates with **Microsoft Teams** to coordinate remediation of oversharing and data-leak risks in Copilot and other AI agents.
- **Executive reporting.** Board-ready analytics and compliance insights for leadership reviews.

#### Access and permissions

Open the Security Dashboard for AI at **[ai.security.microsoft.com](https://ai.security.microsoft.com)**, or enter it from the **Microsoft Defender**, **Microsoft Entra**, or **Microsoft Purview** portals.

The dashboard uses your **existing Defender, Entra, and Purview permissions** - no separate role is required. Eligible Defender, Entra, and Purview customers can access the Security Dashboard for AI at **no additional licensing cost**.

For the full list of supported products, permissions details, and how to review and assign security recommendations, see [Assess your organization's AI risk with Microsoft Security Dashboard for AI](https://learn.microsoft.com/en-us/security/security-for-ai/security-dashboard-for-ai).

### Compare the two dashboards

| Capability | Copilot security dashboard \(Microsoft 365 admin center\) | Microsoft Security Dashboard for AI |
| --- | --- | --- |
| **Primary scope** | Microsoft Copilot data protection, DLP, oversharing, and compliance | Cross-product AI risk across agents, apps, and platforms |
| **AI asset coverage** | Microsoft Copilot | Microsoft Copilot, Copilot Studio agents, Microsoft Foundry apps and agents, and third-party models/apps/agents \(for example, Google Gemini, OpenAI ChatGPT, MCP servers\), including unmanaged and shadow AI agents |
| **Signals aggregated** | Microsoft Purview signals for Copilot | Microsoft Defender + Microsoft Entra + Microsoft Purview signals |
| **AI-powered insights** | — | Security Copilot–powered prompts, summaries, and risk prioritization |
| **Remediation workflow** | Purview-based policies \(for example, DLP\) | Tailored recommendations, task delegation, and Microsoft Teams integration |
| **Access path** | [admin.microsoft.com](https://admin.microsoft.com/) → **Copilot** > **Overview** > **Security** | [ai.security.microsoft.com](https://ai.security.microsoft.com) or entry points in Defender, Entra, and Purview portals |
| **Roles / licensing** | **Global Reader** to view; **AI Administrator** to make changes | Uses existing Defender/Entra/Purview permissions; no additional licensing for eligible customers |
| **Availability** | Generally available | Public preview |

Note

The Security Dashboard for AI is currently in preview. Capabilities and coverage might change before general availability. Check the [security for ai](https://learn.microsoft.com/en-us/security/security-for-ai/security-dashboard-for-ai) article for the latest supported products and permissions.

## Related guidance

Use these articles for deeper coverage of related articles:

- **Deployment and readiness**

  - [Configure a secure and governed data foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/configure-secure-governed-data-foundation-microsoft-365-copilot)
  - [Minimum requirements to deploy Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements)

- **Architecture and data handling**

  - [How does Microsoft Copilot work?](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture)
  - [Microsoft Copilot data protection architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing)

- **Oversharing remediation**

  - [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance)
