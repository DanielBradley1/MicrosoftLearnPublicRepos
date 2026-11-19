<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/share-run-apps?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Share and run Copilot Managed Runtime partner apps

This article explains how to run, discover, and share Copilot Managed Runtime partner apps after deployment. The Copilot Managed Runtime portal gives app users a stable way to discover, open, and access apps by default, while partners can optionally surface open and share actions inline when that feature improves the app maker's workflow.

## Run an app

After deployment, an app user can open the app in the Copilot Managed Runtime app host at its runtime URL. This stable URL remains associated with the app across deployments and serves the latest deployed version.

Use the CLI as the source of truth for the live URL:

```bash
ms app play --no-browser --json
```

Runtime URLs use:

```text
https://play.managedapps.cloud.microsoft/apps/<app-id>
```

Use the complete app-specific URL. Opening only the host origin redirects to the Copilot Managed Runtime portal rather than launching an app.

## Discover apps in the app portal

App users can discover and open all apps they created or that have been shared with them in the Copilot Managed Runtime portal:

```text
https://managedapps.cloud.microsoft/
```

The portal lists accessible apps and their current deployment status, so app users don't need a direct runtime link.

## Share an app

App makers can share apps from the Copilot Managed Runtime portal. Partner integration is optional; a partner might provide inline sharing backed by the CLI when it improves the authoring experience.

To grant one or more users or groups permission to run an app:

```bash
ms app share <principals> --access play
```

Principals are a comma-separated list of email addresses or Microsoft Entra object IDs. The supported `edit` access level grants repository-edit access to app-making collaborators rather than runtime access.

See [Share an app](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/share-app?view=o365-worldwide) for complete direct sharing, unsharing, and organization share-link workflows. See the [`ms app share` CLI reference](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-share) for exact command syntax.
