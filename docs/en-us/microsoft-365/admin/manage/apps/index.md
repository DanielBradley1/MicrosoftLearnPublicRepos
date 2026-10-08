<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Copilot Managed Runtime overview and key concepts for admins \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Copilot Managed Runtime helps teams build internal line-of-business apps that automatically comply with your organization's IT governance policies. Every app is governed from the moment you create it - no extra setup required. Each app appears in the Microsoft 365 admin center, where admins can track usage, monitor health, and manage its lifecycle.

Important

- This is a preview feature.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139), and are available before an official release so that customers can get early access and provide feedback.

Copilot Managed Runtime brings three audiences together around the same governed app:

- **Users** discover and run apps from a web portal.
- **Makers and developers** build apps using tools and languages they already know.
- **Administrators** govern apps across the tenant.

To learn how people create apps across Cowork, Copilot Studio, and the CLI, see [What is Copilot Managed Runtime \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide).

## Key features

- Microsoft Entra authentication and authorization out of the box
- Access to 1,500+ connectors, callable directly from JavaScript and TypeScript
- A native Git inner loop with a repository for source control and collaboration
- Automatic adherence to your IT policies, including sharing limits, conditional access, advanced connector policies, and data loss prevention \(DLP\)
- Centralized inventory, usage analytics, and operational health in the Microsoft 365 admin center

## Common scenarios

Copilot Managed Runtime fits scenarios where teams need flexibility while staying within enterprise governance boundaries:

- **Personal productivity apps.** Tools an individual builds and uses in their own developer environment.
- **Team productivity apps.** Shared apps that small teams use to automate workflows and collaborate.
- **Organizational apps.** Broader solutions that IT or development teams deploy across the tenant with admin-controlled distribution.

## Key concepts

To work more effectively with Copilot Managed Runtime, it's important to understand the following key concepts:

| Term | Description |
| --- | --- |
| **Copilot Managed Runtime SDK** | The developer libraries and tooling used to build apps with Copilot Managed Runtime. Provides built-in Microsoft Entra authentication, connectivity to more than 1,500 data sources, and enforcement hooks for governance policies. |
| **Personal developer environment** | A dedicated, isolated sandbox provisioned for each developer, separate from production, so they can build and test safely. |
| **Governance policies** | Rules that control how apps built with Copilot Managed Runtime are deployed, who can access them, what data they connect to, and how their lifecycle is managed. The app creation process enforces these policies automatically. |
| **App inventory** | A centralized, real-time view in the Microsoft 365 admin center of all apps built with Copilot Managed Runtime across the tenant, including usage, health, and compliance state. |
| **Distribution controls** | Admin-managed settings that determine who can discover and use each app built with Copilot Managed Runtime across the tenant. |

## Enable Copilot Managed Runtime for your tenant

Configure Copilot Managed Runtime enablement separately for each app creation method.

Note

Creating apps with Copilot Managed Runtime by using the Cowork skill is governed by your tenant's Frontier onboarding rather than the tenant switch. After your tenant is onboarded to Frontier, app creators who have access to Cowork can build apps.

### Defaults by app creation path

| Creation path | Public preview | Frontier public preview |
| --- | --- | --- |
| **Cowork** | Not available. Admins are guided to sign up for Frontier. | On by default through [Frontier program](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#build-apps-with-app-builder-frontier). |
| **CLI** | Off by default. Admins can enable using environment settings and the environment group rule. | Off by default. Admins can enable using environment settings and the environment group rule. See [Control whether apps can be created using the CLI](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#control-whether-apps-can-be-created-using-the-cli). |
| **Copilot Studio** | On by default. Admins can manage it in the Microsoft 365 admin center. | On by default. Admins can manage it in the Microsoft 365 admin center. See [Create an app in Microsoft Copilot Studio \(preview\)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/create-app). |

### Permissions

| Role | What they can do |
| --- | --- |
| Global Administrator | Manage the CLI and Copilot Studio app creation paths. |
| Power Platform Administrator | Manage the CLI and Copilot Studio app creation paths. |
| Global Reader, AI Administrator, AI Reader | View only. Guided to contact an administrator to enable features. |

Enabling the **Cowork** app builder skill requires onboarding the tenant to the Microsoft Copilot Frontier Program. Power Platform administrators can't enable Frontier; they're guided to contact an administrator with the required permissions. See [Get started with the Microsoft Copilot Frontier Program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier?view=o365-worldwide).

### Where the settings live

The app creation path controls are in the Microsoft 365 admin center, under **Apps** > **Overview** > **Set up app creation spaces**. You can also enable and configure creation paths through PowerShell or the API.

The Power Platform tenant setting for the Copilot Studio app creation preview is `powerPlatform.powerApps.enableManagedAppsMcsPreview`. The setting uses string values rather than Boolean values. The following PowerShell example applies the public-preview default value, `DefaultOn`:

```powershell
$tenantSettings = Get-TenantSettings
$tenantSettings.powerPlatform.powerApps.enableManagedAppsMcsPreview = "DefaultOn"
Set-TenantSettings -RequestBody $tenantSettings
```

### Scope access to Copilot Studio app creation with security groups

To restrict Copilot Studio app creation to specific Microsoft Entra security groups, set `powerPlatform.powerApps.enabledGroupsManagedAppsMcsPreview` to a security group's object ID \(GUID\). To configure multiple groups, use a comma-separated string of object IDs.

The following example configures access for one security group. Replace `<security-group-object-id>` with the group's object ID:

```powershell
$tenantSettings = Get-TenantSettings
$tenantSettings.powerPlatform.powerApps.enabledGroupsManagedAppsMcsPreview = "<security-group-object-id>"
Set-TenantSettings -RequestBody $tenantSettings
```

For multiple security groups, use the following example:

```powershell
$tenantSettings = Get-TenantSettings
$tenantSettings.powerPlatform.powerApps.enabledGroupsManagedAppsMcsPreview = "<group-1-object-id>,<group-2-object-id>"
Set-TenantSettings -RequestBody $tenantSettings
```

When the Copilot Studio app creation path is enabled, users who belong to any configured security group can create apps.

## Control source and deployment options

Copilot Managed Runtime supports external repositories owned by GitHub Enterprise Cloud organizations. Configure repository visibility and other repository management policies in GitHub Enterprise Cloud. For more information, see [Enforcing repository management policies in your enterprise](https://docs.github.com/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#about-policies-for-repository-management-in-your-enterprise).

Administrators can use **External artifacts in managed apps** to control whether developers can deploy prebuilt artifacts produced outside the Microsoft-managed build system. The setting is disabled by default and can be configured for an individual environment or an environment group.

See [Configure source and deployment controls](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#configure-source-and-deployment-controls).

## Govern apps

Apps built with Copilot Managed Runtime are governed from the moment they're created, with no extra setup required. The governance model is built around three principles: apps are safe by default, admins can govern at scale, and the platform balances controls with developer productivity.

### Safe by default

Every app built with Copilot Managed Runtime has governance built in from the moment it's created. Developers and admins don't need to add governance as a configuration step afterward:

- **Built-in authentication.** Every app uses Microsoft Entra ID—no extra identity configuration needed.
- **Automatic policy enforcement.** Conditional access, data loss prevention \(DLP\), advanced connector policies, sharing limits, and data source restrictions apply to every app by default.
- **Isolated developer environments.** Each developer works in a personal, Microsoft-managed sandbox that inherits these policies automatically.

### Govern at scale

As the number of apps in a tenant grows, a centralized governance layer keeps them manageable:

- **Centralized inventory.** Every app appears in the Microsoft 365 admin center, so admins know what exists and who owns it—no manual registration.
- **Usage analytics and health.** Built-in adoption metrics and health alerting help admins track use and resolve issues before they affect users.
- **Lifecycle management.** Admins manage the full app lifecycle from the Microsoft 365 admin center.

### Balance controls and productivity

The Copilot Managed Runtime model is designed so that security and compliance controls don't impose unnecessary friction on developers or end users:

- **Developers keep their tools.** The SDK handles governance integration, so developers focus on the app, not compliance plumbing.
- **Admins get granular control.** Set controls around distribution, data access, and lifecycle instead of blocking custom apps entirely.
- **Users find apps easily.** Apps surface in familiar Microsoft 365 experiences, reducing shadow IT.

## Licensing and billing

Building apps consumes Copilot Credits and follows the spending policies and credit allocations you configure in the product where you create the apps. For running apps, administrators can configure separate spending policies and credit allocations in the Microsoft 365 admin center.

### Building apps

| App creation experience | How build usage is billed | Where admins manage build costs |
| --- | --- | --- |
| Cowork | Copilot Credits through the creator's Cowork spending policy, per user. | Microsoft 365 admin center |
| Copilot Studio \(preview\) | Copilot Credits through existing Copilot Studio billing, per environment. | Power Platform admin center \(PPAC\) |

**Building in Cowork.** Cowork requires a Microsoft Copilot license, but the subscription doesn't include Cowork usage. Consumption is billed separately through Copilot Credits. Administrators must also enable usage-based billing and include the creator in a spending policy that selects Cowork. Making Cowork discoverable alone doesn't enable users to start using the app-building skill.

**Building in Copilot Studio.** Apps are powered by the GitHub Copilot harness, so billable activity starts during creation, not only after publication, and includes natural-language authoring, testing, and evaluation.

### Running apps

Administrators can configure separate per-user spending policies and credit allocations for app runtime in the Microsoft 365 admin center. These policies apply to runtime usage billed through Copilot Credits, including for apps built in Copilot Studio, Cowork, and using the CLI. Configure runtime coverage for the people who will use the app, separately from the billing configuration used to build it.

Note

For users with a Power Apps Premium license, running apps doesn't consume Copilot Credits unless the app uses separately billed services such as Work IQ APIs or usage exceeds the applicable [Power Apps Premium API request limits](https://learn.microsoft.com/en-us/power-platform/admin/api-request-limits-allocations). This runtime entitlement doesn't change build billing.

Important

For apps built in Copilot Studio, build billing is managed by environment in PPAC, but runtime usage billed through Copilot Credits is managed per user in the Microsoft 365 admin center. The environment-based billing model for Copilot Studio agent runtime does not apply to apps runtime.

Note

During preview, users who don't meet the credit requirements to run an app initially receive a warning. Access is blocked after the user completes 20 app operations or uses the app for five minutes, whichever occurs first.

### Manage credits and control costs

- **Microsoft 365 admin center:** Use **Copilot > Cost management** to configure spending policies for managed applications, select covered users, groups, and services, set policy-level and per-user limits, and monitor consumption.
- **Power Platform admin center:** See [Manage costs for agents powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/power-platform/admin/manage-usage-github-copilot-harness) for more details.

For detailed requirements and configuration guidance, see:

- [Manage Copilot Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Copilot Credits Guide](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/ai/Copilot-Credits-Guide.pdf)
- [Usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Overview of billing for agents and workflows powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/billing-credit-overview)
- [Manage costs for agents powered by the GitHub Copilot harness](https://learn.microsoft.com/en-us/power-platform/admin/manage-usage-github-copilot-harness)
- [Copilot Managed Runtime licensing FAQ \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/licensing-faq?view=o365-worldwide)

## Related information

- [FAQ about Microsoft Copilot Managed Runtime \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/faq-about-apps?view=o365-worldwide)
- [Create and manage apps across Microsoft 365 \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide)
- [Copilot Managed Runtime SDK overview \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/?view=o365-worldwide)
- [Quickstart: Create an app with the CLI](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-managed-apps-cli?view=o365-worldwide)
- [Quickstart: Build an app with GitHub Copilot or Claude Code](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-github-copilot?view=o365-worldwide)
- [Govern apps in Copilot Managed Runtime at scale](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide)
- [Apps in Microsoft Copilot Studio \(preview\)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/apps-overview)
