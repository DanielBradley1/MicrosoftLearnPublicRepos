<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/configure-app-settings?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Configure app settings \(preview\)

Use the Copilot Managed Runtime CLI to view and configure settings for an app. The CLI stores configured settings in the app's `ms.config.json` file.

## Available app settings

The following app setting is currently available:

| Setting | Type | Default | Description |
| --- | --- | --- | --- |
| `show-header` | Boolean | `true` | Shows or hides the app header bar. |

## View app settings

To view all app settings and their effective values, use [`ms app get-settings`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-get-settings):

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

Use [`ms app set-setting`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-set-setting) with the setting flag and a value. Boolean values must be `true` or `false`.

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

Configured settings take effect the next time you run [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) or [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).
