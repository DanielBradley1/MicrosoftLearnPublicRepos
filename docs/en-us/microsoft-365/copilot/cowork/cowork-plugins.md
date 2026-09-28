<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins -->
<!-- Sitemap-Last-Modified: 2026-08-27 -->

# Use plugins with Copilot Cowork

Microsoft Copilot Cowork supports plugins that add new skills and connectors to extend what Cowork can do. Find plugins in the Microsoft 365 plugin marketplace. Your organization's admin can also deploy plugins for you automatically.

A plugin can contain skills, connectors, or both. Skills are specialized capabilities that teach Cowork new domain expertise, such as financial analysis, legal research, or HR workflows. Connectors link Cowork to external data sources and services so it can retrieve or act on information outside of Microsoft 365.

## Browse and acquire plugins

Explore plugins that are available for Cowork directly from the plugin menu. Each plugin listing shows the plugin name, publisher, a short description, and an icon, so you can quickly identify what it does.

1. Open a conversation in Cowork or go to the Cowork home page.
2. Select the **+** button and select **Customize**.
3. Scroll through the list or use the search field to find a specific plugin by name or category.
4. Select a plugin to view more details, including a full description, the publisher name, and the skills or connectors the plugin provides.

Tip

If you don't see a plugin you expected, check with your IT admin. Your organization might need to approve some plugins before they appear in the list.

To learn more about managing plugins, visit [Customize Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize).

## Manage your plugins

After you acquire plugins, you control which ones are active in your conversations. You can enable or disable any acquired plugin at any time from the **Sources & Skills** panel.

- To enable or disable a plugin, open the **Sources & Skills** panel and toggle the switch next to the plugin name.
- When a plugin is enabled, its skills appear alongside Cowork's built-in skills. Plugin skills show up as chips in the side panel, just like built-in skills.
- Plugin connectors appear in the connector list within the plugin details when the plugin is enabled. You can view connector status in the **Sources & Skills** panel.
- When you disable a plugin, its skills and connectors are hidden from your conversations until you enable it again.

Tip

If your side panel feels crowded, disable plugins you aren't actively using. You can always re-enable them later.

## Connect to plugin services

Some plugins include connectors that link Cowork to external services. When you use a connector for the first time, you might need to complete a one-time sign-in to authorize access.

A connector can also work with files from your session—for example, to convert a document or attach a receipt to a record in another system. When a connector tool needs a file, Cowork sends the file you point to and asks for your approval before the tool runs. For authoring details, learn more in [Accept files from the Cowork workspace](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#accept-files-from-the-cowork-workspace).

1. Start a conversation that uses a plugin connector, or select the connector from the side panel.
2. When Cowork needs the connector, it prompts you to connect. A dialog or notification appears with a sign-in link.
3. Select **Connect** or follow the sign-in link.
4. Complete the sign-in or consent flow in the window that opens. You might need to enter your credentials or approve permissions.
5. Once connected, Cowork can access that service in all your conversations going forward.

Note

You only need to sign in once per connector. After the initial connection, Cowork remembers your authorization unless you or your admin revoke it.

## Admin-deployed plugins

Your organization's IT admin can deploy plugins on your behalf. Admin-deployed plugins work a bit differently from plugins you acquire yourself.

| Behavior | Details |
| --- | --- |
| Automatically available | Admin-deployed plugins appear in your account without any action from you. You don't need to browse or acquire them. |
| Can't be removed | Only your admin can add or remove these plugins. You can't uninstall them from your account. |
| Scoped visibility | Admin-deployed plugins might be visible to your entire organization or to specific groups, depending on how your admin configured them. |

Even though you can't remove admin-deployed plugins, you can still enable or disable them for your own sessions. Open the **Sources & Skills** panel and toggle the plugin on or off as needed.

Important

If an admin-deployed plugin requires a service connection, you still need to complete the one-time sign-in yourself. Your admin can't sign in on your behalf.

## Remove a plugin

If you acquired a plugin yourself \(not admin-deployed\), you can remove it when you no longer need it.

1. Open the **Customize** dialog by selecting the **+** button.
2. Find the plugin you want to remove.
3. Select **Remove from Cowork** to remove the plugin.

Removing a plugin removes its skills and connectors from future conversations. Any active conversations that already use the plugin aren't interrupted—they continue to work until the conversation ends.

Note

If you change your mind, you can always re-acquire the plugin from the **Browse plugins** dialog.

## Upload your own plugin package

If you have a plugin package, upload it to Cowork from the **Customize** page and choose who can use it.

1. Select the **+** button, **Customize**, and then select the **Plugins** tab.
2. Select **Upload plugin** and choose a plugin package \(a `.zip` file\).
3. If you upload a package built for Claude or another compatible format, Cowork automatically converts it into a publishable package. The package includes any bundled skills and external connectors.
4. When the **Share** dialog opens, choose who can use the plugin:

   - Select **Only you** to keep the plugin available to your account.
   - Select **Specific users in your organization** to add people by name or email.

5. Select **Apply** to publish the plugin.

When you upload a newer version of a plugin you already shared, open the plugin's detail page and select **Re-share** to update everyone you shared it with.

For full step-by-step instructions, see [Customize Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize#upload-a-plugin-package).

## How plugin skills work

Plugin skills integrate directly into the Cowork experience alongside the built-in skills. Here's what to expect when you use them.

- **Automatic activation**—Cowork selects the appropriate plugin skill based on your conversation context. You don't need to invoke plugin skills manually. When a plugin skill activates, you see a skill notification in the chat, just like with built-in skills.
- **Skill priority**—If a plugin skill has the same name as a built-in skill, the agent determines which skill to use.
- **Side panel visibility**—You can see which skills are active in the side panel during a conversation. Active plugin skills appear alongside built-in skills so you can follow what Cowork is using.
- **Conversation scope**—Plugin skills work within the current conversation context. They can read files you attached, reference earlier messages, and coordinate with other active skills.

## Request a plugin

If you need a plugin that isn't available, contact your IT admin. Admins can request new plugins through the Microsoft 365 admin center or work with partners to develop custom solutions.

## Related content

- [Available plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-available-plugins)
- [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)
- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Build plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development)
- [Manage Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
