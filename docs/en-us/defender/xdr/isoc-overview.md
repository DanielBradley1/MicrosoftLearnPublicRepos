<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/isoc-overview -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# ISOC in Microsoft Defender \(preview\)

Integrated Security Operations Center \(ISOC\) in Microsoft Defender brings leading XDR and SIEM capabilities, threat intelligence, automation, and AI together in the Microsoft Defender portal. ISOC gives security teams shared security signals, context, and workflows to detect, investigate, and respond to threats faster from one integrated experience.

Note

ISOC is in preview. Capabilities and availability might change during the preview period.

[![Screenshot of the Microsoft Defender home page showing the Integrated Security Operations Center capabilities banner.](https://learn.microsoft.com/en-us/defender-xdr/media/isoc-overview/integrated-security-operations-defender-home.png)](https://learn.microsoft.com/en-us/defender-xdr/media/isoc-overview/integrated-security-operations-defender-home.png#lightbox)

## ISOC advantages

ISOC helps security teams:

- **Integrated security operations** - Leading SIEM capabilities are available out of the box in Microsoft Defender, delivering immediate security operations value from day one without requiring a traditional SIEM deployment as a starting point.
- **Value from Microsoft 365 investments** - Eligible customers receive 30 days of included retention for Defender data during this phase of the preview. For broader visibility, bring in additional Microsoft and non-Microsoft data through more than 500 data connectors. Additional ingestion charges might apply depending on the data you ingest.
- **Path for agentic security** - Security teams and Perception agents work together on a common set of signals, context, and workflows, enabling faster investigations, coordinated response, and improved security outcomes.

## Who can use ISOC?

During this phase of the preview, ISOC is available to eligible customers with Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7 that don't have an active Microsoft Sentinel workspace.

If your organization has an active Microsoft Sentinel workspace, continue using your existing Microsoft Sentinel experience during this phase. Don't disconnect a production Microsoft Sentinel workspace only to qualify for the ISOC preview.

## Prerequisites

To use ISOC, you need an active, eligible Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7 license.

To create an ISOC workspace and use workspace-dependent capabilities, you also need an Azure subscription with [the required permissions](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace).

## Licensing and pricing

For Microsoft 365 E5 plan details and pricing, see [Microsoft 365 E5 for Enterprise](https://www.microsoft.com/microsoft-365/enterprise/e5#Pricing).

To compare the security capabilities included with Microsoft 365 enterprise plans, see [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

## ISOC capabilities

ISOC lets eligible customers start with security operations capabilities built into Microsoft Defender and expand with additional data and capabilities when needed.

- Start immediately with case management, workbooks, and natural-language playbook generation.
- Add an ISOC workspace when you need additional Microsoft and non-Microsoft data ingestion, UEBA, Content hub connectors, repositories \(CI/CD\), threat intelligence, and other workspace-dependent capabilities.

The following table summarizes the workspace requirements for the capabilities covered in this preview.

| Capability | ISOC workspace required | Learn more |
| --- | --- | --- |
| Case management | No | [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management) |
| Natural-language playbook generation | No | [Generate playbooks using AI with ISOC](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-generate-playbooks) |
| Enhanced automation rule | No | [Create automation rules with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-create-automation-rules) |
| Workbooks | No | [Create and manage workbooks with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-workbooks) |
| User and Entity Behavior Analytics \(UEBA\) | Yes | [Add UEBA to Microsoft 365 E5 data](https://learn.microsoft.com/en-us/defender-xdr/extend-ueba) |
| Content hub | Yes | [Use Content hub with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/content-hub-defender) |
| CI/CD | Yes | [Deploy content as code from your repository for an ISOC workspace](https://learn.microsoft.com/en-us/defender-xdr/deploy-content-integrated-security-operations) |
| Threat intelligence | Yes | [Threat intelligence in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/defender-threat-intelligence) |
| Azure and third-party security data | Yes | [Data ingestion and billing for ISOC](https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention) |

Note

This table shows whether an ISOC workspace is required for each capability during this preview. It doesn't indicate licensing or availability for the same capabilities in other Microsoft security experiences.

## Get started

If the capabilities you want to use require an ISOC workspace, see [Create an ISOC workspace in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/onboard-isoc-workspace).

For information about ingesting additional security data and understanding billing, see [Data ingestion and billing for ISOC](https://learn.microsoft.com/en-us/defender-xdr/integrated-security-operations-data-billing-retention).
