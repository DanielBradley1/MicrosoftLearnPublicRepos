<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/configure-app-settings?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-06 -->

# Configure app settings

Use the Copilot Managed Runtime CLI to view and configure settings for an app. The CLI stores configured settings in the app's `ms.config.json` file. You can also [add a custom app icon](#add-an-app-icon) by updating this file.

## Available app settings

The following app setting is available through `ms app get-settings` and `ms app set-setting`. To configure an app icon, see [Add an app icon](#add-an-app-icon).

| Setting | Type | Default | Description |
| --- | --- | --- | --- |
| `show-header` | Boolean | `true` | Shows or hides the app header bar. |

## View app settings

To view all app settings and their effective values, use [`ms app get-settings`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-get-settings):

```console
ms app get-settings
```

The command displays each setting and its current value:

```output
show-header = true
```

An effective value includes the default when a setting isn't explicitly configured in `ms.config.json`.

To return the settings as JSON for use in scripts or automation, add the `--json` flag:

```console
ms app get-settings --json
```

The command returns:

```json
{
  "success": true,
  "settings": {
    "showHeader": true
  }
}
```

## Configure an app setting

Use [`ms app set-setting`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-set-setting) with the setting flag and a value. Boolean values must be `true` or `false`.

For example, to hide the app header bar, run:

```console
ms app set-setting --show-header false
```

The command updates `ms.config.json` and confirms the configured value:

```output
show-header = false
```

The resulting configuration includes the following setting:

```json
{
  "appSettings": {
    "showHeader": false
  }
}
```

Configured settings take effect the next time you run [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) or [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).

## Add an app icon

Add a custom icon to help users identify your app in the [Copilot Managed Runtime portal](https://managedapps.cloud.microsoft/). Configure the icon by adding `iconPath` to `ms.config.json`. There's no separate CLI command or flag for this setting.

1. Add a PNG or JPG image to your project. For example, place an image named `custom-icon.png` in the `public` folder at the project root. Its path relative to the project root is `public/custom-icon.png`. You can use a different folder or file name; update `iconPath` in the next step to match.
2. In `ms.config.json`, add `iconPath` as a top-level property, alongside the existing configuration:

   ```json
   {
     "iconPath": "public/custom-icon.png"
   }
   ```


   The example shows only the property to add. Keep the other properties in your file.


   Specify the path relative to the project root, which is the directory that contains `ms.config.json`. Use forward slashes \(`/`\) for compatibility with local and cloud builds.

3. Commit and push the image and updated `ms.config.json`, then deploy the app by using your existing release workflow. For more information, see [Build, preview, and deploy apps](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide).

After you deploy the update, the icon appears with your app in the [Copilot Managed Runtime portal](https://managedapps.cloud.microsoft/). If you don't specify `iconPath`, the app uses the platform's default icon.
