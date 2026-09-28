<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Manage plugins for Copilot Cowork

Microsoft Copilot Cowork supports plugins that add skills and connectors to extend what Cowork can do. As an IT administrator, you control which plugins are available in your organization, how they're deployed, and who can use them. This article covers plugin governance from an admin perspective.

Learn how users browse and use plugins in [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins) and [Customize Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize). Learn about building plugins in [Build plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development).

## What are Cowork plugins?

A Cowork plugin is a package distributed through the Microsoft 365 App Store that can contain:

- **Skills**: Prompt-based workflows that teach Cowork new domain expertise, such as financial analysis, legal research, or HR workflows.
- **Connectors**: Links to external data sources and services that Cowork can use during conversations.

Plugins use the same M365 app package format as Teams apps, Copilot agents, and Office add-ins. You manage them with the same admin tools you use for other Microsoft 365 apps.

Important

[Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers) aren't currently supported for plugin or skill management and sharing. In tenants where IB is enabled, embedded knowledge file uploads are blocked at the tenant level. This prevents affected plugins and skills from being uploaded or published.

## Prerequisites

To manage Cowork plugins for your organization, you need:

- **Microsoft 365 admin center access**: You must be a tenant administrator, or have the Copilot administrator role.
- **Microsoft 365 Copilot licenses**: Users who use Cowork plugins must have Microsoft 365 Copilot licenses assigned.

## Deploy plugins to your organization

You can deploy plugins to your entire organization or to specific users and groups, the same way you deploy other Microsoft 365 apps.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Select **Agents** along with either **All agents** or **Tools**.

   Note

   You can find Cowork plugins in **Agents** > **All Agents** or **Agents** > **Tools**. This is because some agents also function as Cowork plugins. To find out whether it includes Cowork capabilities, review the agent description.
3. Find the plugin you want to deploy. You can search by name or browse the available plugins.
4. Select the plugin to open its details.
5. Select **Installed for**, and select **All users** or **Specific users/groups**.
6. Select **Next** and install.

When you install a plugin, it's automatically acquired for the target users. Users don't need to browse the plugin catalog or install it themselves. The plugin's skills and connectors become available in their Cowork conversations.

Tip

Cowork provides several plugins for Microsoft applications, including Dynamics 365 Customer Service, Dynamics 365 ERP, Dynamics 365 Sales, and Fabric IQ. You can find these plugins in the Microsoft 365 App Store and deploy them like any other plugin.

Learn more in [Deploy agents in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-lifecycle/agent-deploy).

## Control plugin availability

After you deploy a plugin, you can configure who can see it and how users interact with it.

### Deployment types and user permissions

| Deployment type | Who gets the plugin | User can remove it? |
| --- | --- | --- |
| Deployed to entire organization | All licensed Copilot users—acquired automatically | No |
| Deployed to specific groups | Target users—acquired automatically; visible to others if configured | No \(for target users\) |
| Available in the App Store | Users acquire it themselves | Yes |

Admin-deployed plugins display a **Managed by your organization** label in the user's plugin detail view. Users can't remove these plugins, but they can enable or disable them for their own conversations from the **Sources & Skills** panel.

### Allow or block specific plugins

Manage plugin availability through the same app governance controls used for other Microsoft 365 apps:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), select **Agents** > **Tools**.
2. Find the plugin you want to manage and go to the **Users** tab.
3. Adjust the availability setting:

   - **Available to all users**: All licensed Copilot users in your tenant can find and acquire the plugin.
   - **Available to specific users or groups**: Only the users or security groups you specify can see the plugin.

4. Select **Block**: No users in your tenant can access the plugin.

Note

Country or region-based scoping isn't supported for plugin availability. Use security groups to represent geographic or organizational segments.

Learn more in [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

## Prevent plugin sharing in your tenant

Separate from the plugins you deploy, users can upload their own plugin package from the Cowork **Customize** page and then use the **Share** dialog to make it available to other people. A user can share a plugin with specific users in your organization, or request that it be published to your whole organization. Use the controls in this section to limit that.

Important

There's currently no single tenant setting that turns off plugin sharing for every user. Organization-wide sharing requires your approval, and you can block or unpublish any plugin after the fact. A user can still share an uploaded plugin with specific people they choose.

### Org-wide sharing requires admin approval

When a user requests that a plugin be published to your entire organization, the plugin doesn't go live on its own. The request is held in a pending state, and the plugin only becomes available to your organization after a tenant administrator approves it. If you reject the request, the plugin stays unavailable to everyone else in your tenant.

This approval step applies to org-wide publication only. It doesn't apply when a user shares a plugin with specific people.

### Block a plugin that's already been shared

Blocking a plugin makes it inaccessible to everyone in your tenant, including the people it was shared with. To block a specific plugin, follow the steps in [Allow or block specific plugins](#allow-or-block-specific-plugins).

Blocking takes effect for new conversations. Conversations already in progress that use the plugin continue until they end.

### Limit what a shared plugin can reach

A shared plugin can only do what the underlying Microsoft 365 controls allow. Sharing a plugin doesn't grant the recipient any access they don't already have:

- Plugin connectors can't be authorized on a user's behalf. Each recipient must complete the connector's own sign-in or consent flow before the connector does anything. Learn more in [Manage connector authentication](#manage-connector-authentication).
- Recipients can turn any plugin off for their own conversations from the **Sources & Skills** panel.

### Monitor sharing activity

Plugin activity, including interactions with shared plugins, appears in Microsoft Purview audit logs under **Copilot activities**. Learn more in [Monitor plugin usage](#monitor-plugin-usage).

## How users interact with deployed plugins

Understanding how plugins appear to users helps you plan your deployment:

- Admin-deployed plugins appear in the user's **Added Plugins** tab automatically. The plugin detail view shows a **Managed by your organization** label.
- Users can enable or disable any plugin—including admin-deployed ones—from the **Sources & Skills** panel. These preferences are saved per device.
- Disabling a plugin hides its skills and connectors from new conversations but doesn't remove the plugin from the user's account.

Learn more about the full user experience, including browsing, acquiring, and using plugin skills, in [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins).

## Manage connector authentication

Some plugins include connectors that link Cowork to external services. When a plugin connector requires authentication:

- **You can't sign in on behalf of your users.** Each user must complete the sign-in or consent flow themselves the first time they use that connector.
- After the initial sign-in, Cowork remembers the user's authorization unless you or the user revokes it.

### Dynamics 365 connectors

Dynamics 365 plugins \(Customer Service, Sales, and ERP\) use Microsoft Entra ID authentication and require users to select the Dynamics 365 environment they want to connect to. If only one environment is available, Cowork selects it automatically. If multiple environments are available, Cowork prompts the user to choose one.

Dynamics 365 Customer Service and Sales integrations are enabled by default and can be disabled in the [Microsoft 365 admin center](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-intelligence#enable-microsoft-365-admin-center-copilot-dataverse-settings).

## Monitor plugin usage

Microsoft Purview audit logs capture Copilot activities for your organization, including interactions with Cowork and its plugins. Audit entries appear under **Copilot activities** in Microsoft Purview. Audit Standard provides these logs at no extra cost.

Learn more in [Audit log activities for Microsoft Copilot](https://learn.microsoft.com/en-us/purview/audit-copilot).

## Plugin support for MCP servers

Cowork supports plugins with MCP servers and/or skills, packaged as Teams apps. Cowork performs dynamic tool discovery—when a plugin declares an MCP server, Cowork calls initialize and tools/list at runtime to discover available tools automatically. Plugins declare their MCP servers and skills in manifest.json:

```json
{
    "$schema": "https://developer.microsoft.com/en/json-schemas/teams/vDevPreview/MicrosoftTeams.schema.json",
    "manifestVersion": "devPreview",
    "version": "1.0.0",
    "name": {
      "short": "Contoso Analytics",
      "full": "Contoso Analytics"
    },
    "description": {
      "short": "A Cowork plugin for data analysis workflows.",
      "full": "The Contoso plugin integrates Contoso's MCP server..."
    },
    "agentSkills": [
      { "folder": "./skills/data-summary" },
      { "folder": "./skills/trend-analysis" },
      { "folder": "./skills/report-builder" }
    ],
    "agentConnectors": [
      {
        "description": "Remote MCP server providing tools for Contoso",
        "toolSource": {
          "remoteMcpServer": {
            "mcpServerUrl": "https://api.contoso.com/mcp",
            "mcpToolDescription": {
              "file": "./tools/contoso.json"
            },
            "authorization": {
              "type": "OAuthPluginVault",
              "referenceId": "Y29udG9zby1tY3Atc2VydmVyLWF1dGg="
            }
          }
        },
        "id": "contoso",
        "displayName": "Contoso MCP Server"
      }
    ]
  }
```

### Supported MCP features

The following MCP features are currently supported:

| Feature | Notes |
| --- | --- |
| Core MCP \(`initialize`, `tools/list`, `tools/call`, `notifications/initialized`\) | Full tool lifecycle with JSON Schema definitions, capabilities exchange, Streamable HTTP transport; title annotation used as tool display name |
| Auth | None \(anonymous\), `OAuthPluginVault`, and `ApiKeyPluginVault`. Configured via `agentConnectors` schema with a `referenceId` from Teams Dev Center |

## Plugin validation and compliance

Plugins that you publish to the Microsoft 365 App Store go through validation before they're available to your organization. The review process covers manifest integrity, skill and connector validation, and compliance with Microsoft 365 app security requirements.

You can find the full list of validation rules in [Validation rules](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#validation-rules) in the plugin development guide.

### Testing as the plugin author

As the plugin author, test the package yourself first, before you distribute it more widely. You can install your own package directly in Cowork without going through the Microsoft 365 admin center:

1. In Cowork, open the **Customize** page and select the **Plugins** tab.
2. Select **Add plugin** and choose your `.zip` package.
3. When the **Share** dialog opens, choose **Only you** to keep the plugin private to your account while you test.

This approach gives you the fastest loop to confirm that your skills, connectors, and tool calls work end to end before you roll the plugin out to other users, groups, or your whole tenant. Learn more in [Upload a plugin package](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize#upload-a-plugin-package).

### Testing in your tenant

Before you publish a plugin to the Microsoft 365 App Store, you can distribute it within your own tenant to test it with a controlled audience. Admins upload the plugin package through **M365 admin center** > **Manage apps** > **Upload custom app**, then choose who the package is available to:

- **Specific users**: Assign the plugin to individual people for early validation.
- **Specific groups**: Roll it out to a security group or team.
- **Your entire organization**: Make the plugin available to everyone in the tenant.

Tenant-distributed packages don't go through Microsoft 365 App Store validation, so use this path for development, testing, and internal-only plugins.

Learn more about packaging and uploading a plugin to your tenant in [Build plugins for Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#step-8-publish-to-your-tenant).

## Related content

- [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)
- [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins)
- [Build plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development)
- [Manage Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps)
