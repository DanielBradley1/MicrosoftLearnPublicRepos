<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/initialize-app?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Initialize an app in a Copilot Managed Runtime partner integration \(preview\)

\[This article is prerelease documentation and is subject to change.\]

A partner integrating an app-creation experience must register each generated or existing project with Copilot Managed Runtime before it can be previewed or deployed. Initialization selects the source or artifact model, saves the app configuration, and connects the runtime SDK and build integration.

## Choose an app setup flow

For generic setup, see the [CLI quickstart](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide) or the [Copilot quickstart](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-github-copilot?view=o365-worldwide). For command syntax and options, see [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) and [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init).

### New app with platform-managed Git

```bash
ms app create my-app \
  --display-name "My App" \
  --non-interactive

cd my-app
npm install
```

The CLI normally routes the creator to an environment. Pass `--environment-id <environmentId>` only when the creator explicitly targets a specific environment.

### Existing project with platform-managed Git

Use platform-managed Git as the preferred integration for an existing partner project:

```bash
cd <appRoot>

ms app init \
  --display-name "My App" \
  --repo native \
  --build-command "npm run build" \
  --build-path ./dist \
  --non-interactive
```

### Existing partner project with partner-owned artifacts

Use this alternative when you retain partner-owned source and builds. [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/deploy-app?view=o365-worldwide#enable-external-artifact-deployment) requires an environment administrator to enable it.

```bash
cd <appRoot>

ms app init \
  --display-name "My App" \
  --repo none \
  --build-command "npm run build" \
  --build-path ./dist \
  --non-interactive
```

### Existing project with external Git

Use a supported repository owned by a GitHub Enterprise Cloud organization. See [Repository options](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/?view=o365-worldwide#repository-options).

```bash
ms git auth refresh \
  --repo https://github.com/contoso/my-app \
  --open-browser

cd <appRoot>

ms app init \
  --display-name "My App" \
  --repo https://github.com/contoso/my-app \
  --build-command "npm run build" \
  --build-path ./dist \
  --non-interactive
```

Use a full commit SHA for build and deploy automation.

## Persist app configuration

`ms app create` and `ms app init` write `ms.config.json` in the app root. Commit or otherwise persist it with the project. It contains identifiers and build settings, not user credentials.

```bash
ms app show --json
```

Don't reuse one app's config file to register another app. Never persist the CLI's user token cache with app source.

## Add the runtime SDK

```bash
npm install @microsoft/managed-apps
```

The package exposes subpath imports rather than a root import:

```ts
import { getContext } from "@microsoft/managed-apps/app";
import { getUser } from "@microsoft/managed-apps/auth";
import { getClient } from "@microsoft/managed-apps/data";
```

## Configure Vite

```bash
npm install --save-dev @microsoft/managed-apps-vite-plugin
```

Add the plugin to `vite.config.ts`:

```ts
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { managedApps } from "@microsoft/managed-apps-vite-plugin";

export default defineConfig({
  plugins: [react(), managedApps()],
});
```
