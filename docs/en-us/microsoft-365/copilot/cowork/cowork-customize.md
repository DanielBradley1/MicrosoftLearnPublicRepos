<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Customize Copilot Cowork

Copilot Cowork uses the **Customize** page as the place where you manage everything that extends Cowork—the plugins you added and the skills you created—in one place.

## Open the Customize page

Open the **Customize** page when you want to review or change the plugins and skills available to Cowork.

1. Open Cowork.
2. In the left navigation, select **Customize**. The page opens with three tabs: **Preferences**, **Plugins**, and **Skills**.

   [![Screenshot of the Cowork Customize page showing the Plugins tab with installed Microsoft plugins.](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/media/customize-plugins.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/media/customize-plugins.png#lightbox)

## Custom instructions in Cowork

On the **Preferences** tab, add custom instructions that describe how you prefer to work, such as your preferred tone, document formatting, or scheduling rules. Cowork applies these instructions to every task, so you don't have to repeat them.

You can format your instructions using rich text. Type `/` to reference a specific skill, file, person, or meeting.

Your custom instructions are personal to you and can contain up to 20 KB, approximately 3,000 English words. A live counter in the editor shows how much space you've used.

Tip

Keep your custom instructions focused and relevant. Cowork includes them as context for every task, so lengthy or conflicting instructions can leave less room for task-specific information and affect response quality.

## Manage your plugins

Use the **Plugins** tab to review plugins you added and find plugins that are available to you.

The **Installed** section shows plugins that you or your admin added. The **Discover** grid shows plugins available from the Marketplace and plugins you published. The page can also show plugins shared with you.

1. Select a plugin card to open its detail page, where you can review the publisher, description, and included skills or connectors.
2. Select **Add** on the detail page to add an available plugin.
3. Select an installed plugin to open its detail page. From the detail page, you can turn the plugin on or off for the current conversation, see what data it connects to, and remove it.
4. To add a plugin package of your own, select **Upload plugin** at the top of the **Plugins** tab. See [Upload a plugin package](#upload-a-plugin-package).

For step-by-step instructions, see [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins).

## Manage your skills

To manage the skills that Cowork can use in conversations, use the **Skills** tab.

The tab has two lists: **Your skills** for skills you created or added through plugins, and **Built-in** for the skills that ship with Cowork.

1. Use the search box and source filters at the top of the tab to narrow the list.
2. Select **Add** to start a guided conversation that helps you write and save a new skill. Select the arrow next to **Add** to choose **Create new** \(the guided flow\) or **Upload skill** to import a skill file from your device. See [Upload a skill](#upload-a-skill).
3. Select any skill to open its detail page. For skills you created, you can edit instructions, download the skill file, open it in OneDrive, share it, or delete the skill. To test changes, start a new conversation.

For more on writing skills, see [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#cowork-skills).

## Upload a skill

If you already have a skill file—for example, one you exported, received from a colleague, or built outside of Cowork—you can import it from the **Skills** tab instead of recreating it.

1. Select the **+** button and **Customize** , then select the **Skills** tab.
2. Select the arrow next to **Add**, then select **Upload skill**.
3. In the file picker, choose a skill file. Cowork accepts:

   - A `.md` file containing a single `SKILL.md`.
   - A `.zip` or `.skill` archive that has a `SKILL.md` at its root, plus any companion files the skill uses.

4. Cowork validates the file and saves the skill to your OneDrive. The new skill appears in **Your skills** after it finishes syncing, which can take a few moments.

The skill file must include a `name` and a `description` in its frontmatter. If a skill with the same name already exists, Cowork keeps both and adds a number to the new skill's name.

Important

A skill runs as instructions to the AI. Only upload skills from sources you trust. The first time you upload a skill, Cowork shows a reminder about this.

Note

A `.md` skill file can be up to 1 MB. An archive can be up to 10 MB compressed, up to 50 MB uncompressed, and can contain up to 100 files.

## Upload a plugin package

You can upload your own plugin package from the **Plugins** tab to make it available in Cowork and, optionally, share it with other people in your organization.

1. Open the **Customize** page and select the **Plugins** tab.
2. Select **Upload plugin** at the top of the tab.
3. In the file picker, choose a plugin package \(a `.zip` file\).
4. If your file is a Claude or other compatible plugin package, Cowork automatically converts it into a publishable package, including any bundled skills and external connectors it contains.
5. The **Share** dialog opens so you can choose who can use the plugin. See [Share skills and plugins](#share-skills-and-plugins).

For more about plugins, see [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins).

## Share skills and plugins

You can share a skill or a plugin you created so that other people in your organization can use it. Sharing makes the item available either to only you or to specific people you choose.

1. Open the detail page for a skill \(in **Your skills**\) or a plugin you published.
2. Select **Share** in the top-right corner of the detail page.
3. In the **Share** dialog, choose who can use the item:

   - **Only you** keeps the item private to your account.
   - **Specific users in your organization** lets you add people by name or email. Everyone you add can use the item.

4. Select **Apply**. Cowork makes the item available to the people you chose.

When you change a skill or plugin you've already shared, open the detail page and select **Re-share** to send the latest version to everyone you shared it with. Their copy stays up to date with your changes.

Note

When you share an item with specific people, you can copy a link from the **Share** dialog to send to them directly.

## Tips

- Use the conversation **Sources** picker to choose the plugins and skills you need for a request.
- Turn off a plugin you're not using for a conversation to keep results focused.
- Test a new skill in a new conversation before using it in your main conversation.
- Add a skill description that explains *when* Cowork should use the skill. This description helps Cowork pick the right skill for each request.

## Related content

- [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins)
- [Available plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-available-plugins)
- [Manage plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins)
- [Build plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development)
- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
