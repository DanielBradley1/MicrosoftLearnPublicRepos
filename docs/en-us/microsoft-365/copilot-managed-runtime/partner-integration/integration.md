<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/integration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Plan your partner integration with Copilot Managed Runtime

This article helps you plan a partner integration with Copilot Managed Runtime. It covers the partner journey, personas, core concepts, and required integration scenarios. Copilot Managed Runtime doesn't replace a partner's app creation product: partners retain the authoring experience, while Copilot Managed Runtime supplies the enterprise runtime and lifecycle boundary.

## High-level partner integration journey

For product-level concepts and terminology, see the [Copilot Managed Runtime overview](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/overview?view=o365-worldwide). This page focuses on partner-specific integration.

Agree on the initial scenario with Microsoft before you implement customer onboarding. Partner application approval, resource permissions, and preview-host approval require coordination. Review the [prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/prerequisites?view=o365-worldwide) and [preview requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/local-preview?view=o365-worldwide) to understand what to prepare. Use the [integration contact](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/?view=o365-worldwide#questions-and-support) to get started.

The expected journey is:

1. **Create** - The app maker describes or builds an app in the partner product.
2. **Connect** - The app maker chooses organizational data sources allowed by tenant policy.
3. **Preview** - The partner embeds the Copilot Managed Runtime app host around the local app.
4. **Deploy** - The partner submits source or an artifact through the CLI.
5. **Share and run** - App users open the app in the Copilot Managed Runtime app host.
6. **Iterate** - App makers return to the partner to edit, rebuild, and redeploy.

[![Screenshot of the six-stage partner journey from authoring to governed runtime in Copilot Managed Runtime.](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/partner-journey.svg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/partner-journey-large.svg?view=o365-worldwide#lightbox)

## Partner integration personas

Plan your integration around the following personas and their roles in creating, running, and governing apps.

| Persona | Role |
| --- | --- |
| App maker | Uses an AI-assisted or visual builder to solve a business problem and may not work directly with source code or CLI commands. |
| App user | Runs an app that has been shared with them and authenticates with their Microsoft Entra identity. |
| Professional developer | Builds or extends TypeScript and JavaScript apps, manages source, and diagnoses build or runtime behavior. |
| IT administrator | Controls environments, access, connector policy, and operational governance for the tenant. |

## Core Copilot Managed Runtime concepts

Partner integrations rely on three core product concepts:

| Concept | What it is | Relationship in Copilot Managed Runtime |
| --- | --- | --- |
| Tenant | The top-level identity boundary. | Environments organize app and data resources within the tenant. |
| Environment | A division of app and data resources where IT can apply different policies to development and production workloads. | Each app belongs to one environment. Most partner experiences should let the CLI route an app maker automatically and expose explicit selection only when targeting a non-default environment. |
| App | A managed application registered in an environment. | The app carries its environment in `ms.config.json`. |

## Partner scenarios

Use the following table to identify which scenarios require partner integration at each stage of the app lifecycle.

| Stage | Scenario | Partner integration required? |
| --- | --- | --- |
| Create | Sign in an app maker with Microsoft Entra | Yes |
| Create | Create an app from a new or existing web project | Yes |
| Connect | Discover tenant-allowed connectors | Yes |
| Connect | Add an organizational data source and generate typed clients | Yes |
| Preview | Preview with real user data in the host | Yes |
| Deploy | Build and deploy the app | Yes |
| Deploy | Return build errors to the app maker or coding agent | Yes |
| Share & run | Host and run the app | No — apps are automatically hosted and runnable. |
| Share & run | Share with users or groups | Optional; the CLI provides this capability |
| Iterate | Find apps the app maker can edit | Yes |
| — | Administer tenant policy and environments | No — IT administrator responsibility |

See [Partner and Microsoft responsibilities](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/architecture?view=o365-worldwide#partner-and-microsoft-responsibilities).
