<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/backend-integration/fabric-integration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Fabric integration with Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Important

- This feature is in preview.
- This feature is subject to [supplemental terms of use](https://azure.microsoft.com/support/legal/preview-supplemental-terms/), and is available before an official release so that you can get early access and provide feedback.

Copilot Managed Runtime integrates with Fabric to provide backend as a service for Copilot Managed Runtime apps. In this integration, Copilot Managed Runtime hosts and governs your app, and Fabric provides its database backend.

Fabric provides a source code-driven, low-cost relational data store for your apps.

Backend as a service \(Fabric\) is powered by Microsoft Fabric's [Fabric Apps](https://learn.microsoft.com/en-us/fabric/apps/overview) workload. Microsoft Fabric licensing and [preview terms](https://go.microsoft.com/fwlink/?linkid=2240967) apply.

To use Fabric as a backend for Copilot Managed Runtime apps, you need both:

1. One of the following Microsoft Fabric licenses: Power BI Premium Per-User \(PPU\), Power BI Pro, or Fabric Free license.
2. Copilot Credits usage-based billing enabled. For information about how credits are used, see the section on **Copilot Managed Runtime and Microsoft Fabric integration** in the [Copilot Credits Guide](https://go.microsoft.com/fwlink/?linkid=2368800).

This article covers the integration between these services, not standalone Fabric Apps development or deployment. Database is currently the only backend capability available through the integration. Additional backend capabilities are planned for future releases.

## How the integration works

The integration separates the app runtime from its database backend:

| Component | Role in the integration |
| --- | --- |
| Copilot Managed Runtime | Hosts and governs your Copilot Managed Runtime app. |
| Fabric Apps | Provides the database backend that your Copilot Managed Runtime app uses to persist application data. |

When you share apps through Copilot Managed Runtime, you automatically share the data stored in Fabric Apps with the same users.

## Use a database for application data

Use this integration when your Copilot Managed Runtime app needs a database to persist application data.

After an administrator enables the integration for the environment, add the Fabric backend to the app with the [`ms app add backend` command](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-add-backend).

```console
ms app add backend --provider fabric
```

Then ask a coding agent to create an app. For example, a request-tracking app can run in Copilot Managed Runtime and use the database backend provided by Fabric Apps to store requests and their status.

The schema for the database is defined in the `rayfin` folder of your app. It contains TypeScript files that define the entities for the data. See the [Rayfin SDK overview](https://learn.microsoft.com/en-us/javascript/api/fabric-apps-sdk-javascript/rayfin-overview) for more details.

For Fabric Apps capabilities and development workflows outside this integration, see [What is Fabric Apps?](https://learn.microsoft.com/en-us/fabric/apps/overview).

## Control access to the integration

Administrators control whether Copilot Managed Runtime apps can use this integration in the environments in an environment group.

In the Microsoft 365 admin center, the rule is named **Allow Backend as a Service \(Fabric\) for Copilot Managed Runtime**. Its **Enable Backend as a Service \(Fabric\)** setting controls access to the Fabric Apps integration for Copilot Managed Runtime apps in those environments.

To find and review the rule, see [Backend as a Service \(Fabric\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#backend-as-a-service-fabric) in the governance documentation.

## Related information

- [What is Copilot Managed Runtime \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/overview?view=o365-worldwide)
- [Copilot Managed Runtime default governance settings \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide)
- [What is Fabric Apps?](https://learn.microsoft.com/en-us/fabric/apps/overview)
