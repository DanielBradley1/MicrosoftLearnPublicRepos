<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/isoc-overview -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# ISOC in Microsoft Defender

Integrated Security Operations Center \(ISOC\) in Microsoft Defender brings leading XDR and SIEM capabilities, threat intelligence, automation, and AI together in the Microsoft Defender portal. ISOC gives security teams shared security signals, context, and workflows to detect, investigate, and respond to threats faster from one integrated experience.

[![Screenshot of the Microsoft Defender home page showing the Integrated Security Operations Center capabilities banner.](https://learn.microsoft.com/en-us/defender-xdr/media/isoc-overview/integrated-security-operations-defender-home.png)](https://learn.microsoft.com/en-us/defender-xdr/media/isoc-overview/integrated-security-operations-defender-home.png#lightbox)

## ISOC advantages

ISOC helps security teams:

- **Integrated security operations** - Leading SIEM capabilities are available out of the box in Microsoft Defender, delivering immediate security operations value from day one without requiring a traditional SIEM deployment as a starting point.
- **Value from Microsoft 365 investments** - Eligible customers receive 30 days of included retention for Defender data during this phase of the preview. For broader visibility, bring in additional Microsoft and non-Microsoft data through more than 500 [data connectors](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources?tabs=defender-portal). Additional ingestion charges might apply depending on the data you ingest.
- **Path for agentic security** - Security teams and Perception agents work together on a common set of signals, context, and workflows, enabling faster investigations, coordinated response, and improved security outcomes.

## Who can use ISOC?

ISOC is available to eligible customers with Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7.

Eligible customers without an existing Microsoft Sentinel deployment can start using ISOC directly in the Microsoft Defender portal.

Eligible customers with an existing Microsoft Sentinel deployment can choose to transition their deployment to ISOC. Existing Microsoft Sentinel customers aren't automatically moved to ISOC.

## Prerequisites

To use ISOC, you need an active, eligible Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7 license.

To create an ISOC workspace and use workspace-dependent capabilities, you also need an Azure subscription with [the required permissions](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace).

## Licensing and pricing

For Microsoft 365 E5 plan details and pricing, see [Microsoft 365 E5 for Enterprise](https://www.microsoft.com/microsoft-365/enterprise/e5#Pricing).

To compare the security capabilities included with Microsoft 365 enterprise plans, see [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

## ISOC capabilities

ISOC lets eligible customers start with security operations capabilities built into Microsoft Defender and expand with additional data and capabilities when needed.

- Start immediately with case management, workbooks, natural-language playbook generation, and SOC optimization.
- Use [Content hub](https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender) and repository connections \(CI/CD\) to deploy supported Defender-level content at tenant scope without an ISOC workspace.
- Add an ISOC workspace when you need additional Microsoft and non-Microsoft data ingestion, UEBA, threat intelligence, and other workspace-dependent capabilities.

The following table summarizes the workspace requirements for ISOC capabilities.

| Capability | ISOC workspace required | Learn more |
| --- | --- | --- |
| Case management | No | [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management) |
| Natural-language playbook generation | No | [Generate playbooks using AI with ISOC](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-generate-playbooks) |
| Enhanced automation rule | No | [Create automation rules with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-create-automation-rules) |
| SOC optimization | No | [Review SOC optimization recommendations](https://learn.microsoft.com/en-us/azure/sentinel/transition-soc-optimization-recommendations) |
| User and Entity Behavior Analytics \(UEBA\) | Yes | [Add UEBA to Microsoft 365 E5 data](https://learn.microsoft.com/en-us/defender-xdr/extend-ueba) |
| Content hub | Depends on deployment target | [Use Content hub with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender) |
| CI/CD | Depends on deployment target | [Deploy content as code with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/deploy-content-integrated-security-operations) |
| Threat intelligence | Yes | [Threat intelligence in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence) |
| Azure and third-party security data | Yes | [Data ingestion, retention, and billing for ISOC](https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention) |

Note

This table shows whether an ISOC workspace is required for each capability. For Content hub and CI/CD, workspace-level deployments require an ISOC or Microsoft Sentinel workspace. Supported Defender-level content can be deployed at tenant scope without a workspace. This table doesn't indicate licensing or availability for the same capabilities in other Microsoft security experiences.

## Get started

To deploy supported Defender-level content at tenant scope, use [Content hub](https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender) or [repository connections](https://learn.microsoft.com/en-us/defender-xdr/deploy-content-integrated-security-operations) without creating an ISOC workspace.

To use capabilities that require an ISOC workspace, see [Create an ISOC workspace in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace).

For information about security data, included retention, and additional ingestion and retention charges, see [Data ingestion, retention, and billing for ISOC](https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention).
