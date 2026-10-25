<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/app-builder-migration -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# Migrate apps from App Builder

The App Builder is being retired. If you've built apps with App Builder, you can rebuild them in Copilot Cowork or Apps in Copilot Studio. In both experiences, you chat with an agent to create and update apps. You can access your App Builder apps until November 30, 2026.

An automated migration option is planned for mid-October.

To migrate an app manually, download its source code and follow the steps in this article to rebuild it in Copilot Cowork or Copilot Studio.

## How migration works

Migration rebuilds your app instead of moving it. You attach your app's source code to a prompt, and the agent builds a new app that matches the original as closely as possible.

1. **Find your app's data.** Collect the address of the SharePoint site and the names of the lists that store your app's data.
2. **Download your app's source code** from App Builder.
3. **Rebuild your app** in Copilot Cowork or Copilot Studio by attaching the source code to a migration prompt.
4. **Review, publish, and share** your new app.

The new app is separate from your original app. Keep your original app until you confirm that the new app works as expected.

| Part of your app | What happens during migration |
| --- | --- |
| Screens, navigation, components, and logic | Rebuilt from your source code. |
| Data in SharePoint lists | Stays where it is. Your new app connects to the same lists. |
| Data connections | Not carried over. The agent reconnects your new app to your lists. |
| Sharing and app links | Not carried over. Share your new app after you publish it. |

## Choose where to rebuild your app

In both experiences, you attach your source code to a prompt, and an agent rebuilds the app. Use this table to choose where to rebuild.

| Feature | Copilot Cowork | Apps in Copilot Studio |
| --- | --- | --- |
| Where you build | Microsoft 365 Copilot. | Copilot Studio. |
| Environment | Your personal developer environment. | Your personal developer environment. |
| Availability | Available only through the Frontier program. | Public preview. |
| Licensing | Requires a Microsoft 365 Copilot license. | Requires access to Copilot Studio. |
| Billing | Uses Copilot Credits. | Uses Copilot Credits. |
| Share your app | Share a link with people in your organization who can use Microsoft 365 Copilot. | Share with specific people or groups. |

## Find your app's data

App Builder apps connect to data in SharePoint lists. If your app uses lists, your data stays in them during migration, and your new app connects to the same lists.

If your prompt doesn't name your lists, the agent might create sample data instead of connecting to your existing data. Collect these details for your prompt:

- **Site URL**: The address of the SharePoint site that contains your lists, such as `https://contoso.sharepoint.com/sites/DemoSignupSheet`.
- **List names**: The name of each list that your app uses.

Important

Don't delete the SharePoint site that contains your app's lists. Your new app uses the same lists. Deleting your App Builder app doesn't delete the site.

## Download your app's source code

1. Sign in to [Microsoft Copilot](https://www.microsoft365.com/).
2. In the left navigation pane, under **Agents**, select **App Builder**.
3. Find your app in the app list, and open it for editing.
4. Select **App Builder settings** > **Debug** > **Download app**.

Your app's source code downloads as a .zip file. You attach this file to your migration prompt, so don't extract it.

## Write your migration prompt

The agent uses attached files as reference material, not as instructions. Your prompt tells the agent what to build and how to use your source code. A good migration prompt:

- Says that you're migrating your own app.
- Describes what the app does, even though the source code is attached.
- Tells the agent exactly which lists to connect to.
- Ends with instructions to rebuild the app from the exact source code.

Copy the following template, and replace the placeholders in angle brackets \(`<>`\). Keep the last three paragraphs as they are.

```text
I'm migrating my app, <app name>, from App Builder. I built this app, and the attached .zip file contains its complete source code. Name the new app <app name>.

<App name> helps <who uses the app> <do what>. It has these screens: <screen names>. Users can <main tasks, such as adding, updating, and approving items>.

<Data instruction. Choose one from the "Data instructions" section.>

Rebuild this app by referencing the exact source code in the attached .zip file. Before you start, extract the .zip file and read every file, including pages, components, styles, and configuration files. Treat the source code as the specification, and make the new app match the original as exactly as possible:
- Keep the same screens, navigation, and layout.
- Keep all visible text, including headings, labels, buttons, and messages, word for word.
- Keep the same fields, columns, forms, and views.
- Keep the same business logic, calculations, validation rules, filters, and sorting.
- Keep the same create, edit, and delete actions for each list.
- Match the colors, fonts, icons, and spacing in the source code's styles as closely as possible.

Reuse the original code wherever it works in the new app, and change only what's needed for it to run there, such as data connections. Don't add, remove, rename, or redesign anything. If you can't reproduce something exactly, use the closest match and tell me what's different.

This is the full scope of the app. If you build it in stages, then after each stage, list the screens and features from the source code that aren't built yet, so we can continue until the app is complete.
```

### Data instructions

Replace the data placeholder in the template with the instruction that matches your app.

#### Apps that use SharePoint lists

```text
Connect the app to my existing SharePoint lists on <site URL>: <list names>. Use only these lists for the app's data. Don't create new lists, and don't use sample data.
```

#### Apps that don't use lists

```text
This app doesn't connect to a data source. Keep the same data that's in the source code.
```

### Example

This example shows the first three paragraphs of a migration prompt for an app that uses lists. Add the last three paragraphs of the template after them, unchanged.

```text
I'm migrating my app, Demo Signup Sheet, from App Builder. I built this app, and the attached .zip file contains its complete source code. Name the new app Demo Signup Sheet.

Demo Signup Sheet helps my team sign up to present demos at our weekly team meeting. It has these screens: Upcoming demos, Sign up, and My demos. Users can sign up for an open slot, edit or cancel their own signups, and see each presenter's details on a card.

Connect the app to my existing SharePoint lists on https://contoso.sharepoint.com/sites/DemoSignupSheet: Demos, Presenters. Use only these lists for the app's data. Don't create new lists, and don't use sample data.
```

Tip

- Use phrases like "I'm migrating my app" and "I built this app." Avoid phrases like "similar to" or "inspired by," which ask the agent for a new design instead of a faithful rebuild.
- Use data source names exactly as they appear in SharePoint lists.
- Attach the .zip file to the same message as your prompt.

## Migrate your app to Copilot Cowork

Use the App skill in Copilot Cowork to rebuild your app in Microsoft 365 Copilot.

### Prerequisites for Copilot Cowork

- Get a Microsoft 365 Copilot license, and ask your admin to turn on Copilot Cowork for your organization.
- Make sure your organization participates in the [Frontier program](https://www.microsoft.com/copilot/resources/frontier-program). The App skill in Cowork is available only to tenants that have opted into the Frontier program. Your organization might already participate because App Builder also requires the Frontier program.
- Use Copilot Credits. Cowork uses usage-based billing, and building apps consumes Copilot Credits. For more information, see [Usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).
- Have your app's .zip file and your migration prompt ready.

### Rebuild your app in Cowork

1. Go to [Microsoft 365 Copilot](https://copilot.cloud.microsoft), and select **Cowork** at the top of the page.
2. In the message box, enter `/app`, a space, and then paste your migration prompt.
3. Select **Add attachments** \(**+**\) > **Upload images and files**, and then select your app's .zip file.
4. Select **Send**.
5. If Cowork asks you to confirm an action or approve access to your lists, review the request, and then approve it.
6. When the agent finishes, review your app. If the agent built the app in stages, reply **Continue with the deferred items** until the app is complete.
7. Compare the new app with your original app, and ask for any changes.

### Publish and share your app in Cowork

Your app saves automatically as you work. Publishing makes your app, and your latest changes, available to the users you share it with.

1. Select **Publish**.
2. Open the app for editing, and then select **Share** to generate a link.
3. Send the link to people in your organization who use the app. They need to be able to use Microsoft 365 Copilot.

## Migrate your app to Copilot Studio

Important

The Apps experience in Copilot Studio is in public preview. Preview features aren't intended for production use and might have restricted functionality.

### Prerequisites for Copilot Studio

- Get access to Copilot Studio, and make sure app creation is turned on. The **App \(Preview\)** tile is on by default, but your admin can turn it off.
- Use Copilot Credits. App creation is powered by the GitHub Copilot harness. Usage-based billing applies when you use, build, preview, and test apps. For more information, see [Overview of usage-based billing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/billing-credit-overview).
- Have your app's .zip file \(10 MB or smaller\) and your migration prompt ready.

### Rebuild your app in Copilot Studio

1. Sign in to [Copilot Studio](https://copilotstudio.microsoft.com).
2. On **Home**, make sure the **New experience** toggle is on.
3. Select the **App** tile. You can also select **Apps \(Preview\)** > **New app**.
4. Paste your migration prompt into the message box.
5. Select **+**, and then attach your app's .zip file.
6. Select **Submit**.
7. Answer any follow-up questions. If Copilot Studio asks you to approve access to your lists, review the request, and then approve it.
8. When the agent finishes, test your app in the preview.
9. From the app's dropdown menu, review **Data** and **Connections** to confirm that the app uses your existing lists.
10. Compare the new app with your original app, and ask for any changes. For example prompts, see [Refine your rebuilt app](#refine-your-rebuilt-app).

### Publish and share your app in Copilot Studio

1. Select **Publish**.
2. Select **Share**, and then share the app with people or groups in your organization.

## Verify your data connections

Your new app doesn't inherit your original app's data connections. Your data stays in your lists, and the agent reconnects your new app to them based on the data instruction in your prompt.

After the agent builds your app, confirm that the app uses your data:

1. Confirm that the app shows your existing list items, not sample data.
2. Create, edit, and delete a test item to confirm that the app can update your lists.
3. In Copilot Studio, review the app's **Data** and **Connections**.

If the app shows sample data, send a prompt like this one:

```text
This app is using sample data instead of my data. Connect it to my existing SharePoint lists on <site URL>: <list names>. Don't create new lists, and don't use sample data.
```

## Refine your rebuilt app

The agent might not reproduce every detail on the first try. Use follow-up prompts to close the gaps.

| Task | Example prompt |
| --- | --- |
| Find what's different | `Compare the new app with the source code in the attached .zip file. List every screen, field, label, and rule that's missing or different, and then fix them.` |
| Finish a staged build | `Continue with the deferred items.` |
| Fix one screen | `Make the <screen name> screen match <file path> in the attached source code exactly.` |
| Restore exact text | `Use the exact headings, labels, and button text from the source code on every screen.` |
| Restore logic | `Use the same validation rules as the original app. Use <file path> in the source code as the reference.` |

If the agent can't find your source code, attach the .zip file again.

## Known limitations

1. Migration creates a new app. Your original app's link, sharing, and data connections aren't migrated.
2. Your new app might not look identical to the original. The agent uses tested color themes, so it picks the closest match to your colors.
3. In Copilot Studio, attachments must be 10 MB or smaller, with up to 10 files per message.

## Troubleshooting

| Issue | What to do |
| --- | --- |
| The app shows sample data instead of your data. | Send the prompt in [Verify your data connections](#verify-your-data-connections) with your site URL and list names. |
| The agent can't find your list. | Check the site URL and list names in your prompt, and make sure you have access to the site. |
| The agent says your environment is being set up. | Setting up an environment for the first time takes a few minutes. Wait, and then ask the agent to continue. |
| Copilot Studio doesn't accept your .zip file. | Attach the .zip file instead of individual code files. If the file is larger than 10 MB, remove generated folders such as `node_modules` and `dist`, and then compress the remaining files again. |
| You don't see the App skill in Cowork. | The App skill is available only to Frontier program members. Contact your admin. |
| You don't see the **App** tile in Copilot Studio. | On **Home**, turn on the **New experience** toggle. If you still don't see the tile, your admin might have turned off app creation. |

## Related content

- [What is Microsoft Copilot Managed Runtime \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/index)
- [Get started with Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/get-started)
- [Build apps with Microsoft Copilot](https://support.microsoft.com/topic/build-apps-with-microsoft-365-copilot-a50c7eb7-ed36-45b5-baa4-b24e70f3b550)
- [Usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
