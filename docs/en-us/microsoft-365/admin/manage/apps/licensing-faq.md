<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/licensing-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# Copilot Managed Runtime licensing FAQ \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Microsoft Copilot Managed Runtime hosts internal line-of-business apps that comply with your organization's governance policies from the moment they're created. This article answers common questions about the licenses and Copilot Credits that makers, developers, and users need to build and run these apps. It also explains where administrators manage Copilot Credits.

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

## Licensing at a glance

| Activity | What's required | Where administrators manage credits |
| --- | --- | --- |
| Build an app in Cowork | A Microsoft Copilot license and Copilot Credits billed through the maker's Cowork spending policy | Microsoft 365 admin center |
| Build an app in Copilot Studio | Copilot Credits billed through existing Copilot Studio billing for the environment | Power Platform admin center |
| Build an app with the Copilot Managed Runtime CLI | No license is required for development activities other than running the app locally | Not applicable |
| Run an app, including running it locally with the CLI | A Power Apps Premium license or Copilot Credits | Microsoft 365 admin center |

## General

### Do administrators need to buy or enable anything for Copilot Managed Runtime to be available in the tenant?

No. All eligible tenants in the commercial cloud get Copilot Managed Runtime automatically, with no separate installation step. Each app creation path has its own enablement default. For example, Copilot Studio app creation is on by default, while CLI app creation is off by default. For details, see [Enable Copilot Managed Runtime for your tenant](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide#enable-copilot-managed-runtime-for-your-tenant).

### Are build costs and runtime costs billed together?

No. Building apps consumes Copilot Credits and follows the spending policies and credit allocations you configure in the product where the app is created. Runtime usage is billed per user, and administrators configure separate spending policies and credit allocations for it in the Microsoft 365 admin center.

## Building apps

### How is building an app billed?

Building an app is billed through the product you use to create it. For details, see the documentation for that product:

- **Cowork**: [Manage Copilot Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- **Copilot Studio**: [Overview of billing for agents and workflows powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/billing-credit-overview)

### Do developers who use the Copilot Managed Runtime CLI need a license?

A license is required only when a developer runs an app locally with the CLI. Other CLI development activities, such as creating, building, and deploying an app, don't require a license. To run an app locally, developers need the same Power Apps Premium license or Copilot Credits that users need to run apps.

### Do makers need a Power Apps Premium license because their personal developer environment is a managed environment?

No. Personal developer environments created for Copilot Managed Runtime are managed environments. However, license auto-claiming doesn't apply to makers who use these environments only to create apps hosted on Copilot Managed Runtime. These makers don't need a premium license.

If makers also build Power Apps or Power Automate flows in the same personal developer environment, license auto-claiming applies, and they might need a premium license. For more information, see [Environment routing for Copilot Managed Runtime](https://learn.microsoft.com/en-us/power-platform/admin/default-environment-routing-copilot-managed-runtime) and [Licensing requirements for managed environments](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-licensing).

## Running apps

### What license do users need to run an app?

Users need one of the following:

- **Power Apps Premium license**: Covers running apps without consuming Copilot Credits.
- **Copilot Credits**: Usage is billed through Copilot Credits.

These requirements apply to users running apps and to developers running apps locally with the CLI.

### Which actions consume Copilot Credits?

Copilot Managed Runtime measures app usage in API calls. Typical actions that count as API calls include:

- Launching an app.
- Calling data through a connector, such as reading or writing records.
- Publishing an app.

Each API call consumes 0.1 Copilot Credits. Specialized services that an app uses, such as Work IQ APIs, are charged separately at their own rates.

For the authoritative metric and rate, see the [Copilot Credits Guide](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/ai/Copilot-Credits-Guide.pdf).

### Do Power Apps Premium users consume Copilot Credits?

No. Users with a Power Apps Premium license don't consume Copilot Credits when they run apps. Their API calls count toward the daily [Power Platform request limits](https://learn.microsoft.com/en-us/power-platform/admin/api-request-limits-allocations) for their license, and usage above those limits is billed through Copilot Credits. Specialized services, such as Work IQ APIs, are still charged at their own rates.

### Can users run apps with Power Apps use rights included in Microsoft 365 or Dynamics 365?

No. Power Apps use rights included with Microsoft 365 or Dynamics 365 licenses don't provide access to apps hosted on Copilot Managed Runtime, regardless of the type of connector the app uses. These users need a Power Apps Premium license or Copilot Credits to run the apps.

### Do users need a Microsoft 365 Copilot license to run an app?

No. Users need a Power Apps Premium license or Copilot Credits to run an app.

### Does sharing an app give recipients a license to run it?

No. Sharing grants access to the app, but each recipient still needs a Power Apps Premium license or Copilot Credits to run it. Recipients also need the appropriate permissions and connections for the app's underlying data.

## Managing costs

### What do administrators need to set up so users can run apps with Copilot Credits?

Before users who don't have a Power Apps Premium license can run apps, complete the following setup in the [Microsoft 365 admin center](https://admin.microsoft.com):

1. Turn on usage-based billing for Copilot Credits.
2. Create a spending policy for managed applications, and include the users or groups who run apps.
3. Set credit allocations and per-user limits as needed.

Copilot Credits are pooled at the tenant level. For more information, see [Usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

### Where do administrators manage credits for building apps?

Administrators manage credits for building apps in the product where the app is created. For more information, see [Manage Copilot Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance) and [Manage costs for agents powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/power-platform/admin/manage-usage-github-copilot-harness).

### Where do administrators allocate credits and monitor runtime consumption?

In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Copilot** > **Cost management**. You can configure spending policies for managed applications, select covered users, groups, and services, set policy-level and per-user limits, and monitor consumption. For more information, see [Usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

## Related content

- [Copilot Managed Runtime overview and key concepts for admins \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide)
- [FAQ about Microsoft Copilot Managed Runtime \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/faq-about-apps?view=o365-worldwide)
- [Copilot Managed Runtime SDK overview \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide)
- [Environment routing for Copilot Managed Runtime](https://learn.microsoft.com/en-us/power-platform/admin/default-environment-routing-copilot-managed-runtime)
- [Manage costs for agents powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/power-platform/admin/manage-usage-github-copilot-harness)
- [Power Apps licensing FAQs](https://learn.microsoft.com/en-us/power-platform/admin/powerapps-licensing-faq)
