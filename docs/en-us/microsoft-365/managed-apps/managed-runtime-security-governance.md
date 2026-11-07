<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/managed-runtime-security-governance?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# Security and governance in the Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

The Copilot Managed Runtime helps you secure and govern AI-built apps at enterprise scale. This article explains its built-in protections and the administrative controls IT can use to manage sharing, data access, and oversight. Apps on the Copilot Managed Runtime help organizations innovate with protections already in place and controls that IT can adapt to their requirements.

Regardless of where apps are created, including Copilot Cowork, Microsoft Copilot Studio, the CLI, or other creation surfaces, those protections come from two complementary parts of the platform:

- **The managed host** provides the foundation for developers to build and run apps, enforcing authentication, data request boundaries, and governed access to business services.
- **Administrative controls** let IT admins review and adapt the policies that control app sharing, data source availability, and permitted operations.

This article explains how those protections work together and links to the guidance for reviewing or configuring each feature. For app creation options, see [What is Copilot Managed Runtime](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide).

Important

- This feature is in preview.
- These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?LinkId=2373139) and are available before an official release so that customers can get early access and provide feedback.

## Built-in protections for app builders

The managed host is where apps run, handling Microsoft Entra authentication, app loading, and runtime governance. This is the sandbox where IT policies are enforced to secure the assets running inside.

### App access requires sign-in and permission

Knowing an app's address isn't enough to open it. The platform delivers app content, including code and assets, only after checking that the user signs in and has permission to access the app.

Users sign in with Microsoft Entra ID, Microsoft's identity service for organizational accounts, so developers don't need to configure a separate identity integration. By default, the app remains private to its owners until shared.

For the host's authentication responsibilities, see [Runtime architecture](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/architecture?view=o365-worldwide). To grant or revoke app access, see [Share an app with users and groups](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/share-app?view=o365-worldwide).

### App code runs within enforced boundaries

App code runs inside a sandboxed iframe within the managed host. This setup separates the app code from the surrounding host and keeps host-managed authentication tokens out of the app code's reach.

Two complementary controls govern how apps run:

| Communication path | Control |
| --- | --- |
| Direct browser activity | [Content Security Policy](https://developer.mozilla.org/docs/Web/HTTP/Guides/CSP) \(CSP\) governs which resources an app can load, which destinations it can contact, and which websites can embed it. |
| Connector requests to business services | Requests to business services pass through the managed host, where authentication and connector policies apply. |

These controls apply to different communication paths.

Browser requests are subject to CSP, while connector requests pass through the platform's authentication, authorization, and connector policy checks. Allowing a connector doesn't require adding the connected service's address to the app's CSP allow list.

For more information, see [Runtime architecture](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/architecture?view=o365-worldwide) and [How CSP applies to apps](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/content-security-policy?view=o365-worldwide#how-csp-applies-to-copilot-managed-runtime-apps).

### Content Security Policy governs browser activity

CSP tells the browser which sources and activities are permitted. The browser enforces it by default, so it blocks activity that violates the policy rather than merely recording it. The default CSP configuration for apps is restrictive.

The default policy restricts several types of browser activity:

- **Sending information to external services.** Direct browser requests are limited to the app's own origin by default. For example, an app can't send data directly to an external analytics endpoint unless the applicable policy allows it.
- **Loading scripts from another website.** The browser blocks scripts from unapproved third-party hosts.
- **Running unsafe scripting patterns.** The default script policy doesn't enable inline scripts or unsafe string evaluation.
- **Embedding apps elsewhere.** The browser checks whether the website attempting to embed an app is permitted by the applicable policy.

These restrictions apply to the entire app, including bundled third-party packages. If a package attempts to send information directly to an external endpoint that CSP doesn't allow, the browser blocks that request.

Together, the sandbox and browser-enforced policy reduce what malicious code can do at runtime. Administrators can configure the applicable CSP settings when a business scenario requires additional capabilities, as detailed in the [Administrative controls for your organization](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/managed-runtime-security-governance?view=o365-worldwide#administrative-controls-for-your-organization) section. These protections don't replace reviewing app code and dependencies.

For the default directives, see [Content security policy](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#content-security-policy). For developer troubleshooting, see [Identify a CSP violation](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/content-security-policy?view=o365-worldwide#identify-a-csp-violation).

### Connector policies govern access to business services

Apps use Microsoft connectors to work with business services without requiring developers to build each integration from scratch. Each connector exposes actions, such as retrieving records or performing an operation in the connected service.

By default, end users consent to connection creation, and the app uses each user's own connection to retrieve data according to their permissions in the connected service. For more information, see [End-user connection consent](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/connect-to-data?view=o365-worldwide#end-user-connection-consent).

A maker can intentionally configure a supported shared connection instead. The app then uses the shared connection's credentials rather than each user's own connection. A platform-enforced connection proxy restricts requests to the actions configured for the app. Users don't receive a connection they can reuse in other apps. For configuration and security considerations, see [Use shared connections in an app](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/shared-connections?view=o365-worldwide).

Connector requests pass through the SDK and managed host, where authentication and governance are applied centrally. Administrators govern this access through advanced connector policies \(ACP\), which determine both which connectors an app can use and which actions it can perform. Approving a connector does not automatically permit every action it offers.

The Microsoft-curated default policy provides a starting configuration at both levels:

- **Selected connectors are permitted.** These connectors include SharePoint, OneDrive for Business, Microsoft Teams, Outlook, Excel Online, and Dataverse. Selection criteria include Microsoft publication, general availability, Microsoft Entra ID authentication, and connections that keep data within the organization's tenant or use Microsoft-managed services. The default allow list excludes third-party and custom connectors, along with infrastructure and administrative connector categories.
- **Specified higher-risk actions remain blocked.** Even within approved connectors, the default policy blocks specified actions that construct arbitrary HTTP requests, execute scripts or freeform queries, or invoke arbitrary custom platform APIs.

The default policy also governs Model Context Protocol \(MCP\) servers, which expose tools and services to AI capabilities.

Together, these restrictions allow apps to perform supported business tasks without granting every capability exposed by a connected service. Connector governance applies during development, deployment, and runtime. Existing environments can have different effective policies.

For the current defaults, see [Connectors and MCP servers](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#connectors-and-mcp-servers) and [Blocked connector actions](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#blocked-connector-actions). To understand how existing policies apply, see [How connector policies are evaluated for existing environment groups](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#how-connector-policies-are-evaluated-for-existing-environment-groups).

### Build protections and deployment traceability

By default, the platform stores apps in platform-managed Git repositories, so they have source control built in. Microsoft-managed builds of the source in these platform-managed repositories run in a sandbox that restricts network access to help prevent data exfiltration during the build process. This feature complements the controls that govern app behavior at runtime.

Each of these builds is associated with a source Git commit, so teams can trace deployed code back to its source and investigate changes over time. Publishing is an explicit deployment step, so teams can continue development without changing the live app and deploy an earlier successful commit when needed. Together, build isolation and deployment traceability help teams control both how app code is built and which version reaches users.

For information about source control, preview, and deployment behavior, see [Build, preview, and deploy apps](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/dev-inner-loop?view=o365-worldwide).

Important

Developers can also use a supported external GitHub repository. The build protections and deployment behavior described in this section apply to apps that use platform-managed repositories, not external GitHub repositories. For an example of building and deploying apps through an external pipeline, see [Deploy apps with GitHub Actions](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/deploy-managed-apps-github-actions?view=o365-worldwide).

Administrators can separately allow externally built artifacts. These artifacts bypass the Microsoft-managed build system, so your organization is responsible for validating them and securing their build pipeline. For this control, see [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

## Administrative controls for your organization

The hosting platform enforces protections, while administrators determine the configuration that's appropriate for their organization. IT can review where apps are created, how they're shared, and which additional browser destinations or connector capabilities to permit.

To review governance settings, go to **Apps** > **Settings** > **Environment groups** in the Microsoft 365 admin center. For the permissions needed to view or change settings, see [Roles and responsibilities](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/roles-responsibilities?view=o365-worldwide).

### Route app creators to governed environments

An *environment* is a workspace where apps are created and managed, with settings that govern their use. An *environment group* brings environments together so administrators can apply common governance policies across them. Environment routing directs app creators to the environment where they build their apps, determining which policies apply.

Organizations that already use Microsoft Power Platform keep their existing environment routing, environment groups, and advanced connector policies. Apps respect those configurations rather than replacing decisions administrators already made. The effective connector restrictions depend on the group's ACP, its **Advanced connector policies only** setting, and applicable data policies.

For organizations without an existing routing configuration, creators create apps in environments within a Microsoft-managed default environment group, where Microsoft-curated default policies apply. Creators receive these environments when they create an app, so they have guardrails from the start.

For routing behavior and existing configurations, see [Routing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#routing) and [If you're an existing Power Platform customer](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#if-youre-an-existing-power-platform-customer).

### Control how apps are shared

Owners can grant access directly to users or groups or use an organization-only share link, like sharing Word or PowerPoint files stored in SharePoint. Owners can revoke access when business needs or responsibilities change.

Administrators control whether organization-only links are available or whether owners must share explicitly with users and groups. They also control whether apps can be shared with guest users. Review these settings together when determining the intended audience for apps.

Important

Organization-only links can include guest users when guest sharing is allowed because guests are part of the organization's directory. "Organization-only" doesn't mean "employees only" in the case of guests.

For administrative controls, see [Sharing settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#sharing). For commands to grant and revoke access, see [Share an app with users and groups](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/apps/share-app?view=o365-worldwide#grant-access-to-users-or-groups).

### Configure CSP for approved browser activity

When an app requires an additional external destination, script source, or embedding location, administrators can review the business need and configure the applicable CSP settings for an environment group or specific environment. These settings allow IT to approve specific sources rather than grant unrestricted browser access.

For example, an app might need to retrieve shipping estimates from an external logistics API that the company trusts. An administrator can allow that API's specific origin in the applicable `connect-src` directive while continuing to restrict requests to other external destinations.

Administrators can also configure violation reporting to understand attempted activity. Report-only mode helps assess a policy's impact before enforcing it. It records what the policy would block without interrupting those activities. For example, IT can use it to identify app dependencies that a proposed restriction would affect and determine whether an exception is appropriate.

For policy values and configuration instructions, see [Content security policy](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#content-security-policy) and [Customize the default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#customize-the-default-settings).

### Configure permitted connectors, actions, and MCP servers

Administrators can review the default advanced connector policy \(ACP\) configuration and customize it for business scenarios that require additional connectors, actions, or MCP servers. A request for another connector should include a review of the actions the app needs. Administrators can permit the required operations without enabling every action available through that connector.

For example, an inventory app might need to retrieve records from the company's SQL Server database. Because the Microsoft-curated default policy doesn't include the SQL Server connector, an administrator needs to configure an applicable policy for that app's environment that permits it. The policy can allow the actions needed to read records while keeping unnecessary write or delete actions blocked. Changes apply within the relevant environment scope. This approach lets IT enable additional capabilities where needed without making them available throughout the organization.

For configuration instructions, see [Customize connector settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#connectors-and-mcp-servers-1) and [Taking full control](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#taking-full-control).

### Review apps and dependencies centrally

The Microsoft 365 admin center provides a centralized inventory of apps on the Copilot Managed Runtime with details like ownership, status, usage, connectors, and environment group information. This inventory helps administrators identify the right owner for a review and understand an app's organizational context without relying on each creator to provide that information separately.

When administrative action is needed, administrators can **Block** the app directly from the inventory. This action blocks end-user access while retaining the app and its data. Administrators can unblock it after resolving the issue.

For inventory and dependency details, see [View and oversee apps across your tenant](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/inventory?view=o365-worldwide#app-detail-panel). For administrative actions, see [Block an app](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/inventory?view=o365-worldwide#block).

### Monitor health and investigate activity

The **Monitor** view in the Microsoft 365 admin center helps administrators check that apps are performing as expected and identify problems affecting production use. Administrators can review app-open success, session counts, responsiveness, and data-request performance, then configure alerts for selected thresholds. For example, an alert for a drop in app-open success can prompt IT to investigate rather than wait for users to report a problem.

Metrics are aggregated from runtime activity, not reported in real time. For available metrics and alert configuration, see [Monitor the health of apps](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide).

## Adopt apps with ongoing oversight

The Microsoft-provided defaults give your organization a starting configuration for broad adoption without setting up governance from scratch. Use the following steps to review those defaults, confirm they meet your requirements, and establish ongoing oversight:

1. **Confirm the environment group policies.** Review the applicable governance configuration. Start with [Default governance settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide).
2. **Validate access and connectivity.** Check [sharing settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#sharing), alongside [permitted browser destinations](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#content-security-policy) and [connectors and actions](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#connectors-and-mcp-servers).
3. **Establish ownership and oversight.** Identify the [app inventory](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/inventory?view=o365-worldwide) for your tenant, and establish [health monitoring and alerts](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide#create-alerts-for-your-apps).
4. **Expand capabilities deliberately.** Review requests for broader sharing or additional capabilities against business needs and adjust the relevant policies. For configuration guidance, see [Customize the default settings](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#customize-the-default-settings).

The platform foundation and configurable policies work together. Creators start with protections in place, while IT retains responsibility for reviewing the configuration, approving exceptions, and overseeing broader adoption.
