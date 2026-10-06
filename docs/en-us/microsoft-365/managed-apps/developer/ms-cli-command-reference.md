<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Copilot Managed Runtime CLI command reference \(preview\)

\[This article is prerelease documentation and is subject to change.\]

The Copilot Managed Runtime CLI is published as [`@microsoft/managed-apps-cli`](https://www.npmjs.com/package/@microsoft/managed-apps-cli) and invoked as `ms`.

Most commands operate on the app in the current directory and read defaults from its local configuration \(app name, environment, repository binding\). Run commands from the directory that contains your app unless a flag explicitly lets you target another app.

This reference groups every command by typical developer workflow tasks:

| Group | Command | Description |
| --- | --- | --- |
| [Authentication](#authentication) | [`ms auth login`](#ms-auth-login) | Sign in to Microsoft Entra ID via the browser. |
| [Authentication](#authentication) | [`ms auth logout`](#ms-auth-logout) | Clear cached credentials and remove the active account pointer. |
| [Authentication](#authentication) | [`ms auth status`](#ms-auth-status) | List cached accounts and indicate the active one. |
| [Authentication](#authentication) | [`ms auth switch`](#ms-auth-switch) | Make a different cached account active. |
| [Authentication](#authentication) | [`ms git auth refresh`](#ms-git-auth-refresh) | Refresh or establish the Entra-to-GitHub identity mapping. |
| [Create an app](#create-an-app) | [`ms app create`](#ms-app-create) | Create a new app and scaffold a project template. |
| [Create an app](#create-an-app) | [`ms app clone`](#ms-app-clone) | Clone an existing app's platform-managed Git repository. |
| [Create an app](#create-an-app) | [`ms app init`](#ms-app-init) | Register an existing web project as an app. |
| [Discover connectors](#discover-connectors) | [`ms connector list`](#ms-connector-list) | List connectors available in an environment. |
| [Discover connectors](#discover-connectors) | [`ms connector list-actions`](#ms-connector-list-actions) | List operations exposed by a connector. |
| [Manage app resources](#manage-app-resources) | [`ms app add data-source`](#ms-app-add-data-source) | Add a connector to the app as a table or action data source. |
| [Manage app resources](#manage-app-resources) | [`ms app remove data-source`](#ms-app-remove-data-source) | Remove a previously added data source \(table or action\) from the app. |
| [Manage app resources](#manage-app-resources) | [`ms app refresh data-source`](#ms-app-refresh-data-source) | Re-fetch schema and regenerate TypeScript for bound data sources. |
| [Develop locally](#develop-locally) | [`ms app dev`](#ms-app-dev) | Start the full local development loop. |
| [Build and deploy](#build-and-deploy) | [`ms app pack`](#ms-app-pack) | Build the app locally and stage output for inspection. |
| [Build and deploy](#build-and-deploy) | [`ms app build`](#ms-app-build) | Trigger a platform build for a specific commit. |
| [Build and deploy](#build-and-deploy) | [`ms app build-status`](#ms-app-build-status) | Check the status of a build. |
| [Build and deploy](#build-and-deploy) | [`ms app deploy`](#ms-app-deploy) | Promote a green build to the live app. |
| [Play](#play) | [`ms app play`](#ms-app-play) | Open an app and print its launch URL. |
| [Share](#share) | [`ms app share`](#ms-app-share) | Grant access to users or groups. |
| [Share](#share) | [`ms app share list`](#ms-app-share-list) | List the users and groups an app is shared with. |
| [Share](#share) | [`ms app unshare`](#ms-app-unshare) | Revoke previously granted access. |
| [Share](#share) | [`ms app share link create`](#ms-app-share-link-create) | Create a tenant-wide share link for the app. |
| [Share](#share) | [`ms app share link list`](#ms-app-share-link-list) | List share links issued for the app. |
| [Share](#share) | [`ms app share link revoke`](#ms-app-share-link-revoke) | Revoke a share link by ID. |
| [Inspect and manage](#inspect-and-manage) | [`ms app list`](#ms-app-list) | List apps in the environment that you can access. |
| [Inspect and manage](#inspect-and-manage) | [`ms app show`](#ms-app-show) | Show local app configuration and bound resources. |
| [Inspect and manage](#inspect-and-manage) | [`ms app info`](#ms-app-info) | Show the server-side state of the app. |
| [Inspect and manage](#inspect-and-manage) | [`ms app get-settings`](#ms-app-get-settings) | Show all app settings and their current values. |
| [Inspect and manage](#inspect-and-manage) | [`ms app set-setting`](#ms-app-set-setting) | Update one or more app settings. |
| [Inspect and manage](#inspect-and-manage) | [`ms app delete`](#ms-app-delete) | Delete the app from the environment. |
| [Telemetry](#telemetry) | [`ms telemetry enable`](#ms-telemetry-enable) | Turn on telemetry collection. |
| [Telemetry](#telemetry) | [`ms telemetry disable`](#ms-telemetry-disable) | Turn off telemetry collection. |
| [Telemetry](#telemetry) | [`ms telemetry status`](#ms-telemetry-status) | Show current telemetry settings. |

## Command index

The following table lists the commands alphabetically:

| Command | Group | Description |
| --- | --- | --- |
| [`ms app add data-source`](#ms-app-add-data-source) | [Manage app resources](#manage-app-resources) | Add a connector to the app as a table or action data source. |
| [`ms app build`](#ms-app-build) | [Build and deploy](#build-and-deploy) | Trigger a platform build for a specific commit. |
| [`ms app build-status`](#ms-app-build-status) | [Build and deploy](#build-and-deploy) | Check the status of a build. |
| [`ms app clone`](#ms-app-clone) | [Create an app](#create-an-app) | Clone an existing app's platform-managed Git repository. |
| [`ms app create`](#ms-app-create) | [Create an app](#create-an-app) | Create a new app and scaffold a project template. |
| [`ms app delete`](#ms-app-delete) | [Inspect and manage](#inspect-and-manage) | Delete the app from the environment. |
| [`ms app deploy`](#ms-app-deploy) | [Build and deploy](#build-and-deploy) | Promote a green build to the live app. |
| [`ms app dev`](#ms-app-dev) | [Develop locally](#develop-locally) | Start the full local development loop. |
| [`ms app get-settings`](#ms-app-get-settings) | [Inspect and manage](#inspect-and-manage) | Show all app settings and their current values. |
| [`ms app info`](#ms-app-info) | [Inspect and manage](#inspect-and-manage) | Show the server-side state of the app. |
| [`ms app init`](#ms-app-init) | [Create an app](#create-an-app) | Register an existing web project as an app. |
| [`ms app list`](#ms-app-list) | [Inspect and manage](#inspect-and-manage) | List apps in the environment that you can access. |
| [`ms app pack`](#ms-app-pack) | [Build and deploy](#build-and-deploy) | Build the app locally and stage output for inspection. |
| [`ms app play`](#ms-app-play) | [Play](#play) | Open an app and print its launch URL. |
| [`ms app refresh data-source`](#ms-app-refresh-data-source) | [Manage app resources](#manage-app-resources) | Re-fetch schema and regenerate TypeScript for bound data sources. |
| [`ms app remove data-source`](#ms-app-remove-data-source) | [Manage app resources](#manage-app-resources) | Remove a previously added data source \(table or action\) from the app. |
| [`ms app set-setting`](#ms-app-set-setting) | [Inspect and manage](#inspect-and-manage) | Update one or more app settings. |
| [`ms app share`](#ms-app-share) | [Share](#share) | Grant access to users or groups. |
| [`ms app share list`](#ms-app-share-list) | [Share](#share) | List the users and groups an app is shared with. |
| [`ms app share link create`](#ms-app-share-link-create) | [Share](#share) | Create a tenant-wide share link for the app. |
| [`ms app share link list`](#ms-app-share-link-list) | [Share](#share) | List share links issued for the app. |
| [`ms app share link revoke`](#ms-app-share-link-revoke) | [Share](#share) | Revoke a share link by ID. |
| [`ms app show`](#ms-app-show) | [Inspect and manage](#inspect-and-manage) | Show local app configuration and bound resources. |
| [`ms app unshare`](#ms-app-unshare) | [Share](#share) | Revoke previously granted access. |
| [`ms auth login`](#ms-auth-login) | [Authentication](#authentication) | Sign in to Microsoft Entra ID via the browser. |
| [`ms auth logout`](#ms-auth-logout) | [Authentication](#authentication) | Clear cached credentials and remove the active account pointer. |
| [`ms auth status`](#ms-auth-status) | [Authentication](#authentication) | List cached accounts and indicate the active one. |
| [`ms auth switch`](#ms-auth-switch) | [Authentication](#authentication) | Make a different cached account active. |
| [`ms connector list`](#ms-connector-list) | [Discover connectors](#discover-connectors) | List connectors available in an environment. |
| [`ms connector list-actions`](#ms-connector-list-actions) | [Discover connectors](#discover-connectors) | List operations exposed by a connector. |
| [`ms git auth refresh`](#ms-git-auth-refresh) | [Authentication](#authentication) | Refresh or establish the Entra-to-GitHub identity mapping. |
| [`ms telemetry disable`](#ms-telemetry-disable) | [Telemetry](#telemetry) | Turn off telemetry collection. |
| [`ms telemetry enable`](#ms-telemetry-enable) | [Telemetry](#telemetry) | Turn on telemetry collection. |
| [`ms telemetry status`](#ms-telemetry-status) | [Telemetry](#telemetry) | Show current telemetry settings. |

## Global flags

Every command accepts the following flags.

| Flag | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--json` |  | No | Output the result as a single JSON object \(or NDJSON for streaming commands\). Use this in scripts and CI. |
| `--non-interactive` |  | No | Run without prompts. All required values must be supplied through flags or environment variables. Use this in scripts and CI. |
| `--no-color` |  | No | Disable colored output. |
| `--cloud <cloud>` |  | No | Cloud environment to target. Valid values are `public` \(default\), `usgov`, `usgovhigh`, `usgovdod`, and `china`. |
| `--version` | `-v` | No | Print the CLI version. |
| `--help` | `-h` | No | Show help for the command, including all available flags. |

Tip

Run `ms` with no arguments for grouped top-level help, `ms app` for app subcommands, and `ms app <verb> --help` for a verb's flags. Capabilities surface progressively as you drill in.

## Authentication

Sign in once per machine. All other commands assume an authenticated session against a Copilot Managed Runtime-enabled tenant.

### `ms auth login`

Sign in to Microsoft Entra ID via the browser. Adds the new account to the cache and makes it active.

```bash
ms auth login [--account <email>]
```

#### `ms auth login` `account` parameter

Attempts to log you in as the selected account, useful for multi-account scenarios. To pick among already-cached accounts, use [`ms auth switch`](#ms-auth-switch) instead.

---

### `ms auth logout`

Clear all cached credentials and remove the active-account pointer.

```bash
ms auth logout
```

To change which account is active without signing out, use [`ms auth switch`](#ms-auth-switch).

---

### `ms auth status`

List cached accounts. When more than one account is cached, the active account \(the one used by other commands\) is marked with `*`.

```bash
ms auth status
```

---

### `ms auth switch`

Make a different cached account active for subsequent commands.

```bash
ms auth switch [--account <email>]
```

#### `ms auth switch` `account` parameter

The account to make active. In interactive mode with multiple cached accounts, the CLI prompts for selection if this flag is omitted. Required in non-interactive mode and when using `--json`.

### Git authentication

Some commands need to verify that your Microsoft Entra identity is mapped to a GitHub user with access to the bound repository. The first time a mapping is needed, [`ms app create`](#ms-app-create), [`ms app build`](#ms-app-build), and [`ms app deploy`](#ms-app-deploy) run the GitHub Device Code Flow inline - you don't need to refresh proactively for first-time setup. Use [`ms git auth refresh`](#ms-git-auth-refresh) to re-authenticate explicitly \(for example, when switching GitHub accounts\).

### `ms git auth refresh`

Refresh or establish the Microsoft Entra ↔ GitHub identity mapping for a repository owned by a GitHub Enterprise Cloud organization.

```bash
ms git auth refresh --repo <url> [--open-browser]
```

The command prints the verification URL and a user code for you to paste into a browser. On success, it prints the authenticated GitHub login and the mapping's expiration timestamp. Press `Ctrl+C` to cancel the polling loop cleanly.

#### `ms git auth refresh` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--repo` | `-r` | Yes | A full URL for a repository owned by a GitHub Enterprise Cloud organization. For example, `https://contoso.ghe.com/contoso/my-app` or `https://github.com/contoso/my-app`. The CLI performs only a minimal check that the URL has a host \(used to derive the sign-in endpoint\) and doesn't enforce host or scheme rules itself. The platform is the authority on which hosts and providers are supported. The CLI prompts in interactive mode if you don't set this value. |
| `--open-browser` |  | No | Best-effort launch the system browser in addition to printing the verification URL. Default is print-only. |

## Create an app

Use these commands to create a new Copilot Runtime app or register an existing project.

Configure repository visibility and other repository management policies in GitHub Enterprise Cloud. For more information, see [Enforcing repository management policies in your enterprise](https://docs.github.com/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#about-policies-for-repository-management-in-your-enterprise).

### `ms app create`

Create a new app, scaffold a project template into the directory, and set up source control.

```bash
ms app create --display-name <name> [directory] [options]
```

#### `ms app create` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--display-name <name>` | -n | Yes | Display name for the app. |
| `[directory]` |  | No | Target directory. Defaults to the current directory. Must be empty. |
| `--environment-id <id>` | -e | No | Target environment. When omitted, the CLI uses your developer environment, provisioning one on first run. |
| `--description <text>` | -d | No | Free-text description stored on the app record. |
| `--template <name>` | -t | No | GitHub repository or subpath to scaffold the app from \(for example, `github:owner/repo/subdir`\). Defaults to the built-in Vite template. Applies to every `--repo` mode. |
| `--repo <url>` |  | No | Source-control binding. Omit for platform-managed \(GRS\) Git \(default\). Pass a full `https://` URL for a repository owned by a GitHub Enterprise Cloud organization - for example, `https://contoso.ghe.com/contoso/my-app` or `https://github.com/contoso/my-app` - to clone and bind an existing empty external GitHub repo. Pass `none` to skip all Git binding \(scaffold the template and write `ms.config.json` only, with no local repo or remote\). Can't be combined with `--repository-id`. |
| `--repository-id <id>` | -r | No | Repository ID to associate with the app for source control. Can't be combined with `--repo`. |
| `--build-path <path>` | -b | No | Build output directory. Defaults to `./dist`. |
| `--build-command <cmd>` | -S | No | Full shell command used to build the app. Defaults to `npm run build`. |
| `--build-entry-point <file>` |  | No | Entry point HTML file. Defaults to `index.html`. |
| `--open-browser` |  | No | Best-effort launch the system browser if Device Code Flow re-authentication is needed. Has no effect with `--json`. |
| `--force-reauth` |  | No | Bypass the stored GitHub mapping and force Device Code Flow, as if the mapping had expired. Only affects apps bound to an external GitHub repository. |

Note

- For `--repo <url>`, the CLI clones the external GitHub repository into the directory and overlays the template. The repo must exist and be empty.
- For `--repo none`, the CLI scaffolds the template and writes `ms.config.json` but doesn't initialize a local Git repo or bind a remote. This creates an app for external artifact deployment that you build and deploy yourself. For an example, see [Deploy Microsoft Copilot Managed Runtime apps with GitHub Actions](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/deploy-managed-apps-github-actions?view=o365-worldwide).
- If the GitHub mapping is missing or expired, `ms app create` runs the Device Code Flow in-band and retries once.

---

### `ms app init`

Register an existing web project as an app, without scaffolding files.

```bash
ms app init --display-name <name> [options]
```

#### `ms app init` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--display-name <name>` | -n | Yes | Display name for the app. |
| `--environment-id <id>` | -e | No | Target environment. Defaults to the user's developer environment. |
| `--description <text>` | -d | No | Free-text description. |
| `--build-path <path>` | -b | No | Build output directory. Defaults to `./dist`. |
| `--build-command <cmd>` | -S | No | Full shell command used to build the app. Defaults to `npm run build`. |
| `--build-entry-point <file>` |  | No | Entry point HTML file. Defaults to `index.html`. |
| `--repo <value>` |  | No | Repository behavior. Omit to auto-detect the current Git setup \(and prompt in interactive mode\). Pass `native` to force a platform-managed \(GRS\) repo, `none` for external artifact deployment \(no platform-managed repo\), or a repository URL to bind to an existing GitHub repo already cloned into the current directory. |
| `--icon-path <path>` |  | No | Optional path to a `.png` or `.jpg` app icon, written to `ms.config.json` as `iconPath`. |
| `--local-app-url <url>` |  | No | Optional local development URL, written to `ms.config.json` as `localAppUrl`. |
| `--open-browser` |  | No | Best-effort launch the system browser during Device Code Flow. Has no effect with `--json`. |
| `--force-reauth` |  | No | Bypass the stored GitHub mapping and force Device Code Flow on the first attempt. Useful for recovering a corrupted mapping. |

Note

- Fails if the current directory is already an app.
- Doesn't scaffold template files. Source-control behavior depends on `--repo` \(auto-detected from the current directory when omitted\).
- For the external GitHub branch, the same inline Device Code Flow re-auth applies as with `ms app create`.

---

### `ms app clone`

Clone an existing app's platform-managed Git repository and configure Git authentication for future fetch and push operations.

```bash
ms app clone --app <app-id> [directory]
```

#### `ms app clone` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <app-id>` |  | Yes | App ID of an app that you have edit access to. Use `ms app list --permission edit` to find the app ID. |
| `[directory]` |  | No | Target directory for the cloned repository. If omitted, the CLI uses the current directory, which must be empty. |

Note

`ms app clone` supports platform-managed Git repositories. For an app that uses an external GitHub or GitHub Enterprise Cloud repository, use `git clone <repository-url>` instead. You can't clone an app that doesn't have a source-control binding.

## Discover connectors

Use these commands to find available connectors and inspect their operations before adding them to your app.

### `ms connector list`

List connectors available in an environment.

```bash
ms connector list [--environment-id <id>] [--search <term>] [--include-blocked]
```

Output includes the connector ID, authentication type, tabular support flag, and Data Loss Prevention \(DLP\) and Advanced Connector Policy \(ACP\) status. Seeing governance status at design time lets you avoid building against a connector that policy blocks at deploy or runtime.

#### `ms connector list` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--environment-id <id>` | -e | No | Environment to query. Defaults from `ms.config.json` when present. |
| `--search <term>` | -s | No | Filter by substring match on connector display name or ID \(case-insensitive\). |
| `--include-blocked` |  | No | Also list connectors blocked by tenant policy. By default only allowed connectors are shown. |

---

### `ms connector list-actions`

List the operations exposed by a connector, including per-operation DLP status.

```bash
ms connector list-actions [--environment-id <id>] --connector <connector> [--search <term>]
```

#### `ms connector list-actions` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--connector <connector>` |  | Yes | Connector to inspect, by ID. |
| `--environment-id <id>` | -e | No | Environment to query. Defaults from `ms.config.json` when present. |
| `--search <term>` | -s | No | Filter by substring match on operation summary or action ID \(case-insensitive\). |

## Manage app resources

Use these commands to add, remove, and refresh the data sources your app depends on.

- [Add app resources](#add-app-resources)
- [Remove app resources](#remove-app-resources)
- [Refresh app resources](#refresh-app-resources)

### Add app resources

Run all `add` commands from the directory that contains your app. By default, they generate TypeScript models and services under `generated/`.

---

### `ms app add data-source`

Add a connector to the app, automatically choosing between table and action data sources.

```bash
ms app add data-source --connector <connector> [options]
```

Note

- The CLI adds non-tabular connectors as actions automatically.
- The CLI prompts for table versus action in interactive mode for tabular connectors. You must specify `--as` in non-interactive mode.
- DLP and ACP preflight run before any action or table is added. The CLI filters out blocked operations and reports the count skipped.

#### `ms app add data-source` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--connector <connector>` |  | Yes | Connector to add, by ID \(for example, `shared_office365`\) or display name, from `ms connector list`. |
| `--as <mode>` |  | Conditional | Force `table` or `action` dispatch. Required in non-interactive mode when the connector supports tables. |
| `--connection-id <id>` | -c | No | Existing connection to use. The CLI prompts when omitted. |
| `--dataset <name>` | -d | No | Dataset \(used with `--as table`\). |
| `--table <name>` | -t | No | Table to add \(used with `--as table`\). For Dataverse \(`shared_commondataserviceforapps`\), the table logical name. |
| `--dataverse-environment-id <guid>` |  | No | Dataverse environment ID. Only used with `--connector shared_commondataserviceforapps` to bind to a specific table. |
| `--use-sso` |  | No | Prefer a single sign-on \(Entra ID\) connection: reuse the first existing SSO connection, or silently create one. Errors if the connector isn't SSO-capable. Ignored when `--connection-id` is supplied. |

### Remove app resources

Removal commands prompt for confirmation unless you pass `--force`.

### `ms app remove data-source`

Remove a previously added data source \(table or action\) from the app.

```bash
ms app remove data-source [--name <name>] [--force]
```

#### `ms app remove data-source` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--name <name>` | -n | No | Name of the data source to remove. The CLI prompts you to choose from the app's data sources when omitted. |
| `--force` | -f | No | Skips the confirmation prompt. |

### Refresh app resources

Use this command to sync generated app types with the latest source schema changes.

### `ms app refresh data-source`

Re-fetch the schema and regenerate TypeScript for bound data sources.

```bash
ms app refresh data-source [--name <name>]
```

Run this command after the underlying schema changes \(for example, a new column in a SharePoint list\) to keep the generated TypeScript in sync.

#### `ms app refresh data-source` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--name <name>` | -n | No | Refresh a specific data source. Omit to refresh all bound sources. |

## Develop locally

Use these commands to run your app locally with the config server for iterative development.

### `ms app dev`

Start the full local development loop.

```bash
ms app dev [--port <n>] [--local-app-url <url>] [--config-only]
```

The CLI starts the project's dev process alongside a local config server. The play URL prints once both are reachable. Press `Ctrl+C` to stop them cleanly.

#### `ms app dev` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--port <n>` | -p | No | Port for the config server. Defaults to `8080`. |
| `--local-app-url <url>` | -l | No | URL where the dev server is reachable. Defaults to `http://localhost:3000`. |
| `--config-only` | -C | No | Start only the config server, for when you run the dev server separately \(for example, under a process manager\). |

## Build and deploy

Use these commands to package locally, run remote builds, and deploy a validated commit.

### `ms app pack`

Build the app locally and stage the output for inspection without uploading it anywhere.

```bash
ms app pack
```

Use this command to verify that a clean local build succeeds before triggering a remote build.

---

### `ms app build`

Trigger a platform build for a specific commit on a Git-backed app.

```bash
ms app build --app <name> --commit <sha> [--no-wait] [--open-browser] [--force-reauth]
```

#### `ms app build` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App name. Defaults from `ms.config.json` when present. |
| `--commit <sha>` | -c | No | Commit to build. Defaults to the current `HEAD`. |
| `--no-wait` |  | No | Return immediately after submission and print a hint to follow up with `ms app build-status`. By default, the command waits for the build to reach a terminal state. |
| `--open-browser` |  | No | Best-effort launch the system browser if Device Code Flow re-authentication is needed for external GitHub repos. Has no effect with `--json`. |
| `--force-reauth` |  | No | Bypass the stored GitHub mapping and force Device Code Flow. Only affects apps bound to an external GitHub repository. |

---

### `ms app build-status`

Check the status of a build.

```bash
ms app build-status --app <name> --commit <sha> [--show-log]
```

If the build failed, the output includes the reason so you can fix the code and push again.

#### `ms app build-status` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to inspect. Defaults from `ms.config.json` when present. |
| `--commit <sha>` | -c | No | Commit to check for build status. Defaults to the current `HEAD`. |
| `--show-log` |  | No | Fetch and print the build log when available. |

---

### `ms app deploy`

Promote a green build to the live app.

```bash
ms app deploy [--app <name>] [--commit <sha>] [--artifact <path>] [--open-browser] [--force-reauth]
```

Note

- The command deploys to the environment associated with the app. It doesn't select a deployment environment.
- For Git-backed apps, the CLI resolves the commit \(default `HEAD`\), warns about uncommitted local changes, queues a remote build, polls to completion, and deploys the resulting build.
- For apps with no source control \(`repoType: none`\), the CLI packs and uploads the local build, or uploads a pre-built `.zip` when `--artifact` is supplied.

#### `ms app deploy` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to deploy. Defaults from `ms.config.json`. |
| `--commit <sha>` | -c | No | Commit to deploy \(Git-backed apps only\). Defaults to the current `HEAD`. Mutually exclusive with `--artifact`. |
| `--artifact <path>` |  | No | Path to a local `.zip` build artifact to upload and deploy. Only valid for apps created with no source control \(`repoType: none`\); rejected on Git-backed apps. Mutually exclusive with `--commit`. |
| `--open-browser` |  | No | Best-effort launch the system browser if Device Code Flow re-authentication is needed. Has no effect with `--json`. |
| `--force-reauth` |  | No | Bypass the stored GitHub mapping and force Device Code Flow. Only affects apps bound to an external GitHub repository. |

`ms app deploy --artifact <path>` uploads and deploys the artifact without a platform-managed build. External artifact deployment is disallowed by default. See [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

Your organization is responsible for validating externally built artifacts and securing the build pipeline before deployment.

## Play

Use this command to open your app in live or preview mode.

### `ms app play`

Open an app in the browser and print its launch URL.

```bash
ms app play [--app <name>] [--mode live | preview] [--commit <sha>] [--no-browser]
```

#### `ms app play` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to open. Defaults from `ms.config.json`. |
| `--mode <mode>` | -m | No | `live` opens the deployed app. `preview` opens the latest build on `main`, or a specific commit when combined with `--commit`. Defaults to `live`. |
| `--commit <sha>` | -c | No | Open the preview at a specific commit. Valid only with `--mode preview`. |
| `--no-browser` |  | No | Print the launch URL without opening the default browser. Useful for SSH sessions, CI, and scripts. |

Note

`--mode live` warns that the live build is a snapshot and won't auto-update. Re-run `ms app deploy` to refresh it. If the app is never deployed, `--mode live` fails with a usage error that points you to `ms app deploy`.

## Share

Use these commands to grant, revoke, and manage app access and share links.

### `ms app share`

Grant access to users or groups.

```bash
ms app share <principals> [--app <name>] [--access play | edit]
```

The command automatically looks up email addresses. It reports warnings for entries that don't resolve but proceeds with the ones that do. If no entries resolve, the command fails.

#### `ms app share` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `<principals>` |  | Yes | Comma-separated list of email addresses or Microsoft Entra object IDs. |
| `--app <name>` |  | No | App to share. Defaults from `ms.config.json`. |
| `--access <level>` |  | No | Grant runtime access \(`play`, default\) or repository-edit access \(`edit`\). |

---

### `ms app unshare`

Revoke previously granted access.

```bash
ms app unshare <principals> [--app <name>] [--access play | edit]
```

The `unshare` command only affects the requested access level. For example, `unshare --access edit` leaves `play` access intact. Principals without an existing role assignment at the requested level are no-ops.

#### `ms app unshare` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `<principals>` |  | Yes | Comma-separated list of email addresses or Microsoft Entra object IDs. |
| `--app <name>` |  | No | App to unshare. Defaults from `ms.config.json`. |
| `--access <level>` |  | No | Revoke runtime access \(`play`, default\) or repository-edit access \(`edit`\). |

---

### `ms app share list`

List the users and groups an app is shared with at a given access level.

```bash
ms app share list --access <level> [--app <name>] [--environment-id <id>]
```

#### `ms app share list` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--access <level>` |  | Yes | Access level to list. Either `play` \(run the app\) or `edit` \(modify the underlying repository\). |
| `--app <name>` |  | No | App to inspect. Defaults from `ms.config.json`. |
| `--environment-id <id>` | -e | No | Override the environment ID. Defaults from `ms.config.json` when present. |

---

### `ms app share link create`

Create a tenant-wide share link for the app.

```bash
ms app share link create [--app <name>] [--environment-id <id>]
```

#### `ms app share link create` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to share. Defaults from `ms.config.json`. |
| `--environment-id <id>` | -e | No | Override the environment ID. Defaults from `ms.config.json` when present. |

---

### `ms app share link list`

List share links issued for the app.

```bash
ms app share link list [--app <name>] [--environment-id <id>]
```

#### `ms app share link list` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to inspect. Defaults from `ms.config.json`. |
| `--environment-id <id>` | -e | No | Override the environment ID. Defaults from `ms.config.json` when present. |

---

### `ms app share link revoke`

Revoke a share link by ID. This command removes every prior redeemer's role before it tears down the link record.

```bash
ms app share link revoke --link-id <id> [--app <name>] [--environment-id <id>] [--force]
```

#### `ms app share link revoke` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--link-id <id>` | -l | Yes | The link ID returned from `ms app share link create`. |
| `--app <name>` |  | No | App that owns the link. Defaults from `ms.config.json`. |
| `--environment-id <id>` | -e | No | Override the environment ID. Defaults from `ms.config.json` when present. |
| `--force` | -f | No | Skips the confirmation prompt. |

## Inspect and manage

Use these commands to view app state, update settings, and remove apps when needed.

### `ms app list`

List all apps you can access. By default lists all apps in the tenant; pass `--environment-id` to scope to a single environment.

```bash
ms app list [--environment-id <id>] [--permission <level>]
```

Returns display name, app ID, repository URL, and owners for each app.

#### `ms app list` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--environment-id <id>` | -e | No | Scope the listing to a single environment. When omitted, all apps you can access across the tenant are returned. |
| `--permission <level>` | -p | No | Permission filter. Either `edit` \(apps you can contribute to; default\) or `play` \(apps you can play/view\). Case-insensitive. |

---

### `ms app show`

Show the local app configuration and all bound resources.

```bash
ms app show
```

Reads the local configuration of the app in the current directory.

---

### `ms app info`

Shows the server-side state of the app.

```bash
ms app info [--app <name>] [--environment-id <id>]
```

Returns display name, app ID, repository URL, owners, environment ID, last deployed commit, and the live and preview URLs.

#### `ms app info` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | Name of the app to inspect. Defaults from `ms.config.json`. Pass an explicit name to inspect an app outside the current working directory. |
| `--environment-id <id>` | -e | No | Override the environment ID. Defaults from `ms.config.json`; when neither is set, the environment is resolved automatically from the app name. |

---

### `ms app get-settings`

Shows all app settings and their current values.

```bash
ms app get-settings
```

[Learn how to view app settings](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/configure-app-settings?view=o365-worldwide#view-app-settings)

---

### `ms app set-setting`

Updates one or more app settings.

```bash
ms app set-setting [--show-header <bool>] [other-settings...]
```

Pass settings as named flags. Only the keys you specify are updated.

#### `ms app set-setting` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--show-header <bool>` |  | No | Show or hide the app header bar. |
| `[other-settings...]` |  | No | One or more named setting flags to update. Only provided keys are changed. |

[Learn how to configure an app setting](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/configure-app-settings?view=o365-worldwide#configure-an-app-setting)

---

### `ms app delete`

Deletes the app from the environment. Doesn't delete local source code or the Git repository.

```bash
ms app delete [--app <name>] [--environment-id <id>] [--force]
```

If the app doesn't exist, the command exits cleanly without an error.

#### `ms app delete` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--app <name>` |  | No | App to delete. Defaults from `ms.config.json`. |
| `--environment-id <id>` | -e | No | Override the environment ID. When omitted, the environment is resolved automatically from the app. Useful for deleting an app from outside its scaffolded directory. |
| `--force` | -f | No | Skips the confirmation prompt. |

## Telemetry

The CLI sends anonymized telemetry by default. Use these commands to control collection.

---

### `ms telemetry enable`

Turn on telemetry collection.

```bash
ms telemetry enable [--remote] [--console]
```

#### `ms telemetry enable` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--remote` |  | No | Control sending telemetry to the remote service. This option is the default when no flag is given. |
| `--console` |  | No | Print telemetry events to the local console. |

Pass both flags to toggle both targets at once.

---

### `ms telemetry disable`

Turn off telemetry collection.

```bash
ms telemetry disable [--remote] [--console]
```

#### `ms telemetry disable` parameters

| Parameter | Alias | Required? | Description |
| --- | --- | --- | --- |
| `--remote` |  | No | Stop sending telemetry to the remote service. This option is the default when no flag is given. |
| `--console` |  | No | Stop printing telemetry events to the local console. |

Pass both flags to disable both targets at once.

---

### `ms telemetry status`

Show the current telemetry settings.

```bash
ms telemetry status
```
