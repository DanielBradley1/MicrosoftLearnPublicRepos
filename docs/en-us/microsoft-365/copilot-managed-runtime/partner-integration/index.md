<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Copilot Managed Runtime partner integration overview

This guide helps engineers integrate an app-building product with Copilot Managed Runtime. It explains the platform's integration surfaces and how it compares with Power Platform and Azure. For an example of a partner integration, see [Publish a Lovable app](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/publish-from-lovable?view=o365-worldwide).

## What is Copilot Managed Runtime?

Copilot Managed Runtime provides a platform for creating and operating intelligent internal applications in the context of a Microsoft Entra tenant. It offers a fast path for generated or hand-written web apps to access organizational data and intelligence with automatic hosting, governance, and security.

For product concepts and capabilities, see the [Copilot Managed Runtime overview](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/overview?view=o365-worldwide).

Copilot Managed Runtime supports both AI-assisted makers and professional developers. The primary integration surfaces are the `ms` command-line interface, the Copilot Managed Runtime SDK \(`@microsoft/cmr-apps`\), and the Copilot Managed Runtime app host.

For deeper detail on how these pieces fit together, see [Copilot Managed Runtime architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/architecture?view=o365-worldwide).

## Copilot Managed Runtime vs. other products

Copilot Managed Runtime combines developer flexibility with automatic governance for IT administrators:

[![Screenshot of an opinionated-to-open spectrum showing Copilot Managed Runtime between Power Platform and Azure.](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/opinionated-to-open.svg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/opinionated-to-open-large.svg?view=o365-worldwide#lightbox)

| Capability | Power Platform | Copilot Managed Runtime | Azure custom apps |
| --- | --- | --- | --- |
| Development and application model | Governed, more opinionated application model | Open-standard, full-stack application model | Open; customer-selected frameworks and services |
| Source control | Git support varies by app type | Platform-managed Git preferred; external Git and artifact options supported | Git supported |
| AI and organizational intelligence integration | AI added through connectors, flows, and copilots | Native Work IQ and agentic app integration | AI services integrated by the app team |
| Governance and security | Governance and security built into the platform model | Governance, Microsoft Entra identity, policy enforcement, and audit built into the host | Customer configures governance and security controls |
| Hosting and lifecycle responsibility | Platform manages infrastructure within its lifecycle model | Microsoft-operated host provides runtime, hosting, monitoring, and lifecycle | Customer or partner operates hosting, monitoring, and deployments |
| Developer focus | App logic within Power Platform models, rather than infrastructure | Open-standard app logic, rather than hosting infrastructure | App logic and infrastructure |

## Next step

Continue with [Plan your partner integration](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/integration?view=o365-worldwide).

## Questions and support

For questions or integration support, contact [CMRIntegration@microsoft.com](mailto:CMRIntegration@microsoft.com).
