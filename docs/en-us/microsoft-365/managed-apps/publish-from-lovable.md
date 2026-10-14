<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/publish-from-lovable?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-10-12 -->

# Publish a Lovable app to Microsoft Copilot Managed Runtime \(preview\)

\[This article is prerelease documentation and is subject to change.\]

You can build an internal line-of-business app in [Lovable](https://lovable.dev/) and publish it to Microsoft Copilot Managed Runtime. The published app runs in a Microsoft-hosted environment, requires Microsoft Entra sign-in, and follows your organization's governance policies. Administrators can discover and manage it with other Copilot Managed Runtime apps.

Lovable remains the authoring experience for the project. Copilot Managed Runtime hosts the published app and provides its runtime identity, governance, inventory, and lifecycle controls.

Important

The Microsoft Copilot Managed Runtime integration is a third-party feature provided by Lovable. According to Lovable, it requires a Lovable Business or Enterprise plan and is being released gradually. Lovable controls availability and Lovable workspace requirements.

## Before you begin

You need:

- A Microsoft work account in the tenant where you want to publish.
- Access to the Microsoft Copilot Managed Runtime connector in your Lovable workspace.
- Permission to create a connection in Lovable.
- Permission to create an app in the target Microsoft environment.
- A Microsoft environment ID if your administrator requires you to publish to a designated environment.

A tenant administrator must also [configure Lovable for Copilot Managed Runtime](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/configure-lovable?view=o365-worldwide) before you connect. In each environment or environment group approved for Lovable, the administrator must [allow app creation with the Copilot Managed Runtime CLI](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#control-whether-apps-can-be-created-using-the-cli) and [allow external artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

## Understand the service boundary

Before you publish, understand which service manages each part of the solution.

| Component | Where it's managed |
| --- | --- |
| Lovable project source and project chat | Lovable, according to your Lovable workspace settings |
| Published application | Copilot Managed Runtime in your Microsoft tenant |
| App sign-in | Microsoft Entra ID |
| Runtime connectors and data access | The Microsoft environment, subject to your organization's connector and data policies |
| App inventory, health, blocking, and deletion | Microsoft 365 admin center |
| Lovable connection used to publish | Lovable |

Publishing doesn't move the Lovable project source or chat history into Microsoft. Review your organization's policies for using third-party authoring services before you add data, prompts, or source content to a Lovable project.

## Build and publish the app

### 1. Create a Copilot Managed Runtime project

Create a project in Lovable and specify that the app is for Microsoft Copilot Managed Runtime. For example:

```text
Create an app for Microsoft Copilot Managed Runtime that tracks purchase order approvals.
```

When prompted to choose where the app runs, select **Microsoft Copilot Managed Runtime**. Use standard Lovable publishing instead if you need a public or anonymous website. Copilot Managed Runtime apps are for authenticated users in your organization.

For current Lovable project creation steps, see [Build and publish apps to Microsoft Copilot Managed Runtime](https://docs.lovable.dev/integrations/microsoft-copilot-managed-runtime) in the Lovable documentation.

### 2. Connect your Microsoft work account

When Lovable prompts you to connect, sign in with your Microsoft work account and review the requested permissions. Lovable uses this connection to act under your identity when it creates and publishes the app.

If your administrator gave you an environment ID, enter it when you create the connection. Otherwise, Lovable requests an environment from Microsoft and reuses it for your later projects.

Note

A project uses one Copilot Managed Runtime connection. Publishing runs under the Microsoft identity that created that connection, even if the connection or project is shared with other Lovable workspace members.

If sign-in or environment creation fails, contact your administrator.

### 3. Build the app and connect to data

Describe the app and its data requirements in the Lovable project chat. Copilot Managed Runtime apps can use Microsoft connectors that your organization's policies allow.

Common data sources include SharePoint, Outlook, OneDrive, Excel Online, Teams, Dataverse, Dynamics 365, and Business Central. Some connectors, such as SQL Server, might require an administrator to create a connection in the target environment before you use it.

The standalone [Microsoft 365 connectors in Lovable](https://docs.lovable.dev/integrations/microsoft) use Lovable's connector architecture. Follow the [Copilot Managed Runtime instructions from Lovable](https://docs.lovable.dev/integrations/microsoft-copilot-managed-runtime) when your app is intended to run in Copilot Managed Runtime.

### 4. Preview the app

Use the live preview in Lovable to test your app. The preview loads inside the Copilot Managed Runtime host, so Microsoft might ask you to sign in the first time it opens.

Test the app by using the same Microsoft account and corporate network that you plan to use for publishing. Verify that:

- The app opens after Microsoft Entra sign-in.
- Each connector operation succeeds.

If the preview is blank, ask your administrator to verify the [network requirements](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/configure-lovable?view=o365-worldwide#5-configure-network-access).

### 5. Publish the app

In Lovable, open the publish experience and select **Microsoft Copilot Managed Runtime** as the destination. Confirm the Microsoft connection and environment, and then select **Publish**.

When publishing finishes, open the app URL and test the deployed version. After you edit the project, publish the changes again to update the app.

Note

Lovable uses the Copilot Managed Runtime app-creation path and builds the deployment artifact outside the Microsoft-managed build system. The target environment or its environment group must allow both [app creation with the Copilot Managed Runtime CLI](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#control-whether-apps-can-be-created-using-the-cli) and [external artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

### 6. Share the app

Publishing doesn't grant everyone in your organization access. Share the app with the intended users or groups from the [Copilot Managed Runtime portal](https://managedapps.cloud.microsoft/).

People you share with open the app by using their Microsoft work account. They can also find apps they have access to in the Copilot Managed Runtime portal.

## Limitations

- Apps published to Copilot Managed Runtime don't support public or anonymous access.
- Lovable Cloud databases, backend functions, and secrets aren't part of the published Copilot Managed Runtime app. Use Microsoft connectors and services supported by the runtime.
- Publishing is tied to the Microsoft identity that owns the Lovable connection.
- Removing a project or connection in Lovable doesn't delete an app that is already deployed in your Microsoft tenant.
- Your organization controls which connectors, environments, and users are allowed.

## Troubleshoot publishing

| Issue | What to do |
| --- | --- |
| The Copilot Managed Runtime connector isn't available | Confirm that your Lovable plan and workspace are eligible and that a Lovable workspace administrator allows members to create the connection. See [Lovable's Copilot Managed Runtime documentation](https://docs.lovable.dev/integrations/microsoft-copilot-managed-runtime). |
| Microsoft sign-in fails | Use a Microsoft work account. Ask your tenant administrator to verify that admin consent was granted for the Lovable enterprise application. |
| Environment setup fails | Request an approved environment ID from your administrator and add it to the Lovable connection. |
| App creation is blocked | Ask your administrator to [allow app creation with the Copilot Managed Runtime CLI](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#control-whether-apps-can-be-created-using-the-cli) for the target environment or environment group. |
| Publishing is blocked | Ask your administrator to allow [external artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment) for the target environment or environment group. |
| A connector is blocked | The connector might be restricted by a data loss prevention or advanced connector policy. Ask your administrator which data sources are approved. |
| Preview doesn't load | Ask your administrator to verify proxy, firewall, Conditional Access, and embedded-content policies. |

## Related information

- [What is Microsoft Copilot Managed Runtime?](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/?view=o365-worldwide)
- [Set up Microsoft Copilot Managed Runtime for Lovable](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/configure-lovable?view=o365-worldwide)
- [Build and publish apps to Microsoft Copilot Managed Runtime](https://docs.lovable.dev/integrations/microsoft-copilot-managed-runtime) \(Lovable documentation\)
- [Copilot Managed Runtime overview and key concepts for admins](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/?view=o365-worldwide)
