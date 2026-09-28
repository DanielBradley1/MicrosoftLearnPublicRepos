<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-brand-templates -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Use brand templates with Copilot Cowork

Copilot Cowork uses brand templates to apply your organization's fonts, colors, logos, and slide layouts to the files it creates for you. When a template is available, Cowork uses that styling so your PowerPoint decks match your team's look.

## What brand templates are

A brand template is a PowerPoint file that defines your organization's visual style, including colors, fonts, logos, and slide layouts. When a brand template is available, Cowork uses it whenever it creates a PowerPoint deck for you.

You see the matching styling in the file Cowork produces, without having to ask for it.

## Where brand templates come from

Brand templates can come from your organization or from a template you choose for your own work. The source determines who sets up the template and when Cowork applies it.

| Source | Who sets it up | When it applies |
| --- | --- | --- |
| **Organization template** | Your admin | Applies to everyone in your organization unless you choose a different template. |
| **Personal template** | You | Applies only to artifacts you create. |

## Select an organizational brand template

Ask Cowork to use a brand template when you give it a task that should match your organization's style.

1. In Cowork, start or open a conversation and describe the deck you want.
2. Ask Cowork to use one of your organization's brand templates.
3. Cowork shows the brand templates it finds in your organization's library. Tell Cowork which one to use, and it creates the deck from that template.

## Select a personal template

If your organization doesn't use shared brand templates, or if you want to use a different template, you can provide a personal template when you create your task.

1. In Cowork, create or open the conversation where you want to use a template.
2. Attach the .potx PowerPoint template as an attachment by selecting the **+** and **Upload images and files** or you can use template files in the root of your OneDrive.
3. Include in your task description that Cowork should use the attached template or a specific template from your OneDrive root.

## Override a brand template for one document

When you want to create a one-off document without your brand styling, ask Cowork to skip the template for that artifact.

Example prompt: "Create a plain PowerPoint presentation without our brand template."

## Publish your organization's brand templates in SharePoint

If your organization publishes templates to its [organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library) in SharePoint, Cowork can surface them for you. Libraries are typically organized into company-wide templates \(letterhead, datasheets, whitepapers, general-purpose decks\) and product- or team-specific templates. Cowork shows the PowerPoint template files \(.potx\) it finds in the library for you to choose from. You can also point Cowork to a specific full presentation \(.pptx\) to use as the starting point for a new deck.

## Supported PowerPoint template branding elements

When Cowork generates a deck from a template file, the template's branding is inherited automatically. Verified to carry through into the finished deck are:

- **Theme palette**: your brand's background, heading, and accent colors
- **Brand fonts**: your heading and body typefaces, preserved in the file
- **Logos**: placed by the template, for example, on title and section slides
- **All named layouts and the slide master**: title, agenda/contents, section dividers, multi-column content, closing slides, and any others the template defines
- **Slide geometry and placeholder positions**: Cowork doesn't change these; it rewrites the text content while leaving the design intact

Cowork can take a template's example slides and replace the content, including titles, bullets, and agenda items, while keeping colors, fonts, logo, and positioning untouched.

## Tips for best results

- Point Cowork to a specific template file, or pick one from your template library, rather than asking for a generic deck.
- Make sure your template's branding lives in its slide master, theme, and layouts, as Cowork uses those areas to determine branding.
- Confirm recipients have your brand fonts installed, or embed the fonts in the file before sharing externally.

## Troubleshoot

Use these checks if a generated artifact doesn't match the expected brand styling.

- **The template didn't apply.** Confirm the template is published to your organization's assets library in SharePoint, or saved in the root of your OneDrive, then ask Cowork to use that template by name.
- **Fonts look wrong in the generated file.** PowerPoint substitutes a different font when a brand font isn't installed on the device viewing the file. Embed the fonts in the file or make sure viewers have the brand fonts installed.

## Related content

- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Manage Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Best practices](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/best-practices)
