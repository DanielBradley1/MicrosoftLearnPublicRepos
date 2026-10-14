<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin -->
<!-- Sitemap-Last-Modified: 2026-10-12 -->

# Make your plugin available

Make a published or shared plugin available to its intended users. Complete only the review, installation, assignment, and access actions that the publishing or sharing method requires.

Start with the plugin package. Check separately managed agents, connectors, or remote MCP servers only when their settings are required for the plugin to work.

## Before you begin

Have:

- The exact plugin package identity and version.
- How the plugin was delivered: direct sharing, organization upload, or Microsoft Marketplace.
- The intended users or groups and supported Microsoft 365 experiences.
- Required licenses, permissions, consent, connections, and external services.

If the package is still awaiting review, track its status before completing steps that require publication. If the publishing result is unclear, return to [Publish or share your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish).

## Choose the distribution method

Use the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map to locate the relevant controls. Use the instructions for the method that delivered your package.

### Direct sharing

Some authoring experiences let an owner share a plugin with specific people, groups, or an organization. Approval depends on the sharing method and audience.

1. Confirm that the owner shared the plugin with the intended audience. For Work IQ Dev Tools, `wiqd plugin share` publishes the plugin to the plugin registry for the selected audience. For other methods, follow the method-specific guidance to confirm where the plugin is published and who can access it.
2. Complete any review required by that sharing method. For example, in Cowork, [organization-wide sharing requires administrator approval](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins#org-wide-sharing-requires-admin-approval); sharing with specific people doesn't require that approval.
3. Have users complete any required sign-in, consent, or connections.
4. Verify that an intended user can find and use the plugin.

Direct sharing doesn't create a Microsoft Marketplace offer. Check the selected method before assuming the plugin appears in an organization-wide catalog.

### Organization upload

When an administrator uploads the package to your organization:

1. In the Microsoft 365 admin center, go to **Agents** > **Tools** > **Registry**. [Upload the plugin package](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#upload-plugins-or-skills), review its components, and select the intended users.
2. If the plugin is already in the registry but isn't installed for those users, find it under **Agents** > **Tools** > **Plugins** and [install it](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#install-a-tool) for the intended audience.
3. Open **Users** and [confirm the availability scope](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#manage-plugin-availability-for-users).
4. If access is blocked by policy, check the **your organization** publisher category under **Agents** > **Settings** > **Agent and plugin access**.
5. Complete any required permissions, consent, connections, or external-service configuration.

For the administration procedures, see [Manage plugins, skills, and MCP servers](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context).

### Microsoft Marketplace distribution

For a plugin published through Microsoft Marketplace:

1. Confirm the exact offer, publisher, and package version.
2. Follow the offer's customer acquisition and installation instructions. If administrator installation applies, find the plugin under **Agents** > **Tools** > **Plugins** and follow [Install a tool](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?context=/microsoft-365/copilot/extensibility/context#install-a-tool).
3. Confirm that the appropriate publisher category is allowed under **Agents** > **Settings** > **Agent and plugin access** when organization policy restricts access.
4. Set user availability when the method requires administrator action.
5. Complete the documented permissions, consent, connections, or customer configuration.
6. Verify that intended users can find and use the plugin.

Publication through Microsoft Marketplace doesn't automatically make the plugin available in every customer organization.

## Complete required configuration

Configure a packaged agent, connector, remote MCP server, connection, permission, or external service separately only when the plugin requires that setting to work.

For component boundaries and task routing, see the [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365) administration map.

## Verify availability

1. Confirm that the expected plugin version is installed or shared with the intended audience.
2. Confirm that the intended users or groups have access.
3. Test the plugin in its supported Microsoft 365 experiences.
4. Verify any required sign-in, consent, connections, and external services.
5. Confirm that an intended user can successfully perform the intended task.
6. If the method restricts access to a selected audience, confirm that a user outside that audience can't use it.

If users can't access the plugin, check its status, publisher-category policy, user availability, installation, and required connections. In Cowork, users can also [turn a plugin off for their own conversations](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins#how-users-interact-with-deployed-plugins). Record the audience, experience, package version, verification result, and owner of any issue.

## Next step

[Govern plugin access and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)

## Related content

- [Manage plugins with Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins#manage-plugins-with-microsoft-agent-365)
- [Publish or share your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [Govern plugin access and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)
- [Monitor your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/monitor-plugin)
- [Improve and update your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
- [Retire your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/retire-plugin)
- [For administrators](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide)
