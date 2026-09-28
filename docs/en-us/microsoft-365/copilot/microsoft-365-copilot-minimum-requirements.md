<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Minimum requirements to deploy Microsoft Copilot in your organization

[Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview) is an AI-powered tool that helps with your work tasks. Microsoft Copilot is integrated into Microsoft 365 apps such as Word, Excel, Outlook, and Teams. It uses the latest AI models and data from the web and your organization to answer questions, generate content and ideas, and find information. For more information, see [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview).

| Category | Required to deploy | Strongly recommended |
| --- | --- | --- |
| Licensing | ✅ |  |
| Exchange Online mailbox | ✅ |  |
| Entra ID \(Azure AD account\) | ✅ |  |
| Supported OS and browsers | ✅ |  |
| Network endpoints | ✅ |  |
| SharePoint governance |  | ✅ |
| Purview labeling |  | ✅ |
| Phased rollout |  | ✅ |

Before you deploy Microsoft Copilot, your organization must meet all required prerequisites in licensing, identity, mailbox location, supported platforms, and network access. You can find optional but strongly recommended readiness steps in the following articles:

- [Microsoft Copilot data and compliance readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-data-compliance)
- [Rollout Microsoft Copilot to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-rollout)

## Licensing requirements

Before your users can use Microsoft Copilot, they must be assigned a Microsoft Copilot license along with a qualifying pre-requisite license.

For more information, see [License options for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing).

Note

Chat experiences in Word, Excel, PowerPoint vary depending on your tenant configuration and license. Learn more in [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview#copilot-features-in-microsoft-365-apps). If you'd like to enable users with priority access to these capabilities, learn more about [Microsoft Copilot](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise).

## Mailbox requirements

User's primary mailbox must be in Exchange Online. Copilot uses mailbox content \(mailbox grounding\), including emails, calendar events, and metadata to generate summaries, draft replies, and surface relevant responses. This process is only supported when the mailbox resides in Exchange Online. On-premises and hybrid mailboxes do not support this grounding.

## Sign-in requirements

Before your users can use Microsoft Copilot, they must also have a [Microsoft Entra ID \(Azure AD\)](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra) account.

## Browser requirements

Any modern browser with third-party cookies enabled for online apps. Recommended browsers:

- Microsoft Edge \(recommended for best compatibility and performance\)
- Google Chrome
- Mozilla Firefox
- Apple Safari

## Network requirements

Microsoft Copilot enables AI scenarios that access the web, so it may need to connect to specific network endpoints \(domains\). See the full documentation of network requirements for Microsoft Copilot, which provides a complete list of domains and WebSockets \(WSS\) that an organization's network shouldn't block. For more information, see [Microsoft 365 app and network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-requirements).

## Mobile device requirements

- iPhone: iOS 16.0 or later
- iPad: iPadOS 16.0 or later
- Android 10 or later

## Related topics

For more information on data and compliance requirements, see [Data and compliance readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-data-compliance).

For more information on best practices for how to roll out Microsoft Copilot in your organization, see [Rollout Microsoft 365 to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-rollout).

Tip

We recommend using the [Copilot License Details](https://aka.ms/CopilotLicenseDetails) diagnostic to verify that a specific user account meets the necessary requirements to access Copilot features.
