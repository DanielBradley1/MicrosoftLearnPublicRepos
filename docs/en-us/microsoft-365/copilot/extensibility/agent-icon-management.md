<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-icon-management -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# Design icons for agent acquisition and management

A Copilot agent is an app for Microsoft 365, and its [app package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agents-are-apps#app-package) must include two icon files that represent the agent in the app acquisition and management UI of Teams, Office, Copilot, and other Microsoft 365 applications. This article describes the requirements and best practices for creating these icons.

## Apps for Microsoft 365 icons

The app package for any App for Microsoft 365 must include two icons that represent the extension in several places including the following:

- The app stores in the various Microsoft 365 applications, such as the Teams app store.
- The **Manage your apps** page that can be accessed from various Microsoft 365 applications.
- The app bars of Teams, Outlook, and the Microsoft 365 Copilot application.

Both icons must meet specific size requirements. This article outlines the requirements and best practices for designing these icons, with guidelines intended to help you create a balanced, uniform layout across Microsoft 365 experiences.

![Diagram that shows the uniform layout for app icons.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-balanced-layout.png)

### Creating your assets

Microsoft 365 needs two mandatory and one optional asset during app submission to generate the icons. The following are the requirements for these assets.

[![Diagram that shows the three assets used to generate app icons.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/creating-your-assets-new.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/creating-your-assets-new.png#lightbox)

| Asset | Size | Purpose |
| --- | --- | --- |
| Full‑bleed color icon | 192 × 192 px | Used in app stores and flyouts. |
| Default \(rest\) icon | 32 × 32 px | Used in app bar; default state. |
| Focused \(pressed\) icon *\(Optional\)* | 32 × 32 px | Used in app bar; focused/active state. |

### Color icon specification

- The color app icon dimensions must be 192 x 192 pixels.
- If your icon includes a logo or brand mark, keep it within the 120 x 120 safe area in the center.
- The submitted icon must be a perfect square.
- Do not round the corners. Microsoft 365 applies masking automatically at runtime for consistent UI rendering.

[![Diagram that shows the color app icon dimensions of your logo icon.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/color-icon-architecture-new.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/color-icon-architecture-new.png#lightbox)

### Icon attributes

#### Colored

[![Diagram that shows the color attributes for an icon with colored background.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/icon-attributes-coloured.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/icon-attributes-coloured.png#lightbox)

#### White background

[![Diagram that shows the color attributes for an icon with white background.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/icon-attributes-white-background.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/icon-attributes-white-background.png#lightbox)

### App icon utilization

Your icons may appear in other places in Microsoft 365 applications, depending on what types of extensions or capabilities are included in your App for Microsoft 365. The following are some examples.

#### Personal app

![Diagram that shows the app icon in personal app.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-personal-app.png)

#### App flyout

![Diagram that shows app icon in app flyout.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-app-flyout.png)

#### Bot \(channel view\)

![Diagram that shows an app icon in channel view of bot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/bot-channel-view.png)

#### Message extension flyout

![Diagram that shows an app icon in message extension flyout.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-message-extension.png)

#### Meeting apps flyout

![Diagram that shows an app icon in meeting app flyout.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-meeting-apps.png)

#### Meeting U-bar

![Diagram that shows an app icon in meeting U-bar.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/app-icon-meeting-u-bar.png)

## Best practices

Use the following best practices when designing your app icons. The images represent how the icons are displayed in Teams.

![Diagram that shows a logo within the safe area.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-safe-area.png)

### Do: Follow the recommendation for safe area \(120 x 120\)

Keep all critical branding inside the 120 × 120 px safe area. This ensures that important elements of your icon are not masked or cropped when displayed in different contexts.

![Diagram that shows a logo that is not within the safe area.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-cross-safe-area.png)

### Don’t: Extend your logo beyond the safe area

Extending your logo beyond the safe area results in uneven padding after masking.

![Diagram that shows an icon with full bleed.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/round-corners-do.png)

### Do: Provide full bleed for rounded corners

Upload a full‑bleed square PNG \(192 × 192 px\). The corners are rounded dynamically.

![Diagram that shows an icon with rounder corners.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/round-corners-dont.png)

#### Don’t: Round the corners of your icon

Don’t round the corners. Submit a perfect square at 192 × 192 px, the corners are rounded dynamically.

![Diagram that shows an upload of icon without border.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-icon-without-border.png)

#### Do: Upload an icon without a border

Border is added automatically. In this case just upload your PNG format without a border, even if it’s on a white background.

![Diagram that shows an upload of icon with a border.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-add-border.png)

#### Don’t: Add a border

Borders are added dynamically. If you include a border in your PNG format, it results in unwanted duplication on white backgrounds.

![Diagram that shows an app icon with enough contrast.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-provide-enough-contrast.png)

#### Do: Provide enough contrast

Maintain sufficient foreground/background contrast. A ratio of 4.5:1 is recommended for best accessibility.

![Diagram that shows an app icon which is faded.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-fade-icon.png)

#### Don’t: Fade the icon

Don’t use faded or low‑contrast visuals.

![Diagram that shows an app icon with your brand elevated.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-focus-on-brand.png)

#### Do: Elevate your brand

Focus on your brand by using a full flat color as background.

![Diagram that shows an app icon with your brand in a circle.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-place-icon-in-circle.png)

#### Don’t: Avoid placing your brand icon in a circle

Elevate your brand by keeping the brand icon within the 96 x 96 safe area.

![Diagram that shows an app icon with an abbreviation.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-abbreviate-long-word.png)

#### Do: Abbreviate long words in the app icon

Abbreviate long app names so that it’s easier to read when your icon is resized to 32 x 32 size.

![Diagram that shows an app icon with multiple words.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-include-multiple-words.png)

#### Don’t: Include multiple words in app icon

Avoid using multiple words on the icon. It's impossible to read the text when the icon is at smaller sizes, for example, 32 x 32 or 36 x 36.

![Diagram that shows a balanced app icon.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/do-create-balance.png)

#### Do: Create balance \(96 x 96\)

Ensure visual balance within a 96 × 96 px center area for optimal scaling.

![Diagram that shows a skewed or stretched app icon.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/reusable-content/microsoft-365-development/media/dont-skew-or-stretch.png)

#### Don’t: Skew or stretch your icon

Keep your icon within the safe area. Don’t stretch your icon in any direction.
