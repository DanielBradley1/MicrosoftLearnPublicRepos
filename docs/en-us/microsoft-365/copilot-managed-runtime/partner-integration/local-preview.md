<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/local-preview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Preview an app in a Copilot Managed Runtime partner integration

This article shows how to preview a locally running app in a Copilot Managed Runtime partner integration, inside the same app host boundary used after deployment. The local-preview flow wraps the partner dev server in Local Play, confirms nested-iframe readiness, and prepares the required embedding-domain and Content Security Policy \(CSP\) configuration.

## Load a local preview in the Copilot Managed Runtime app host

Partner products must embed the app frame in the Copilot Managed Runtime app host.

Before integration, the partner product loads the local app directly:

[![Screenshot of a partner product loading the local app directly before Copilot Managed Runtime app host integration.](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/local-preview-before.svg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/local-preview-before-large.svg?view=o365-worldwide#lightbox)

After integration, the partner product loads the Copilot Managed Runtime app host, which nests the local app iframe:

[![Screenshot of a partner product loading the Copilot Managed Runtime app host, which nests the local app iframe.](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/local-preview-after.svg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/media/local-preview-after-large.svg?view=o365-worldwide#lightbox)

For the standard edit, run, commit, and preview cycle around this integration, see [Build, preview, and deploy apps](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide#the-inner-loop).

## Start Local Play

Let the CLI start the app dev script and config server:

```bash
ms app dev
```

If the partner already manages the dev server:

```bash
ms app dev \
  --config-only \
  --local-app-url http://localhost:3000
```

Keep the CLI process alive for the duration of the development session.

For complete command and option details, see [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) and [`ms app play`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-play).

## Embed Local Play

Embed the exact URL printed by the CLI:

```html
<iframe
  title="App preview"
  src="{localPlayUrl}"
  allow="clipboard-read; clipboard-write; local-network-access"
></iframe>
```

Local Play loads from a public HTTPS host while reaching the app on localhost, so Chrome and Microsoft Edge require `local-network-access` for embedded scenarios. Partners must delegate this permission on the Local Play iframe they own, as shown above. For browser and enterprise-policy guidance, see [Build and run the app locally](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide#build-and-run-the-app-locally).

An example of the Local Play URL currently emitted by the CLI is:

```text
https://play.managedapps.cloud.microsoft/apps/dev?ms_appUrl={urlEncodedAppDevServerUrl}&ms_appConfigUrl={urlEncodedAppConfigUrl}
```

Note

`/apps/dev` is the dedicated local-preview route; `dev` is not a registered app ID. Use the exact URL emitted by the CLI rather than substituting an app ID or constructing the URL yourself.

The play-host origin and URL shape can vary by cloud and release. Always use the value emitted by the CLI instead of constructing or rewriting it in production.

The app dev server and config server must both be reachable by the creator's browser. In a remote development container, don't assume the container's localhost is the maker's localhost; exposing only the app endpoint isn't sufficient. Wait for the nested app iframe before reporting that preview is ready, and don't fall back to the bare dev-server URL if host startup fails.

## Request domain allowlisting for Local Play

The Local Play host at the origin emitted by the CLI must allow the partner's domain to embed its URLs. Partners should contact [CMRIntegration@microsoft.com](mailto:CMRIntegration@microsoft.com) to allowlist their embedding domain for the applicable play-host origin during integration planning.

This service-side play-host allowlisting is distinct from app CSP `frame-ancestors`, which controls where the app itself may be framed. See [Allow your app to be embedded](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/content-security-policy?view=o365-worldwide#allow-your-app-to-be-embedded) when configuring app CSP.
