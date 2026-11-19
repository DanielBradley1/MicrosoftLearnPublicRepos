<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Quickstart: Create an app with the Copilot Managed Runtime SDK

This quickstart shows you how to scaffold, run, and ship a *Hello World* app from your terminal by using the Copilot Managed Runtime CLI \([`@microsoft/cmr-cli`](https://www.npmjs.com/package/@microsoft/cmr-cli)\) and the Copilot Managed Runtime SDK \([`@microsoft/cmr-apps`](https://www.npmjs.com/package/@microsoft/cmr-apps)\). By the end, your *Hello World* app is running locally, previewed at a hosted URL, and deployed live to users - all from the terminal, with source control handled by a platform-managed repository.

The main steps cover the default end-to-end path. The [Variations](#variations) section covers binding to an existing GitHub repository, converting an existing web project, and pulling an app onto a new machine.

## Prerequisites

Before you begin, make sure the following tools are installed and configured on your machine:

- [Node.js](https://nodejs.org/) \(LTS version\).
- [Git](https://git-scm.com/downloads), with a credential manager configured.
- A terminal of your choice \(Visual Studio Code integrated terminal, Windows Terminal, iTerm, and so on\).

## Process

The following table describes the process to follow.

| Order | Step | Description |
| --- | --- | --- |
| 1 | [Install the Copilot Managed Runtime CLI](#install-the-copilot-managed-runtime-cli) | Installs the CLI globally and confirms the `ms` command is available. |
| 2 | [Sign in](#sign-in) | Authenticates the CLI with your tenant by using your Microsoft Entra identity. |
| 3 | [Create the app](#create-the-app) | Creates a new app and scaffolds the project files in a new folder. |
| 4 | [Build and run the app locally](#build-and-run-the-app-locally) | Installs dependencies and starts the local development loop to test changes quickly. |
| 5 | [Add a connector \(Optional\)](#add-a-connector-optional) | Discovers and adds a governed data connector to your app if you need external data. |
| 6 | [Commit, build, and push to preview](#commit-build-and-push-to-preview) | Commits local changes and pushes them so preview can build the latest commit. |
| 7 | [Play the app in preview mode](#play-the-app-in-preview-mode) | Opens the hosted preview experience and validates build status for the pushed commit. |
| 8 | [Deploy to live](#deploy-to-live) | Promotes the validated app version from preview to live for end users. |

## Install the Copilot Managed Runtime CLI

Install the CLI globally so the `ms` command is available in any project:

```bash
npm install -g @microsoft/cmr-cli
```

Tip

You can also use this command to update the CLI to the latest version.

Verify the install:

```bash
ms --version
```

## Sign in

Authenticate the CLI with your tenant by using [`ms auth login`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-auth-login). This one-time setup per machine uses your Microsoft Entra identity for everything that follows.

```bash
ms auth login
```

A browser window opens for sign-in. After you sign in, the terminal confirms the authenticated identity.

## Create the app

Create a new app and scaffold the project with [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create). This command creates the app on the platform, sets up a platform-managed Git repository for you, and scaffolds your project files.

```bash
ms app create hello-world --display-name "Hello World"
cd hello-world
```

Because the platform manages the repo, you don't need to set up your own source control to get started. The platform automatically provisions, secures, and connects the repo to the build and deploy pipeline.

## Build and run the app locally

Build and run the app locally for your inner dev loop. This approach lets you see changes instantly as you edit code. Stay in local mode for all iteration: writing features, tweaking UI, debugging logic, trying connector calls. Move to a [platform build](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide#platform-build-and-preview) when the app behaves the way you want locally and you're ready to validate it in a hosted environment.

Install dependencies once, then start the local dev loop with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev):

```bash
npm install
ms app dev
```

[`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) starts your project's dev process. App and runtime settings come from `ms.config.json`, while the local development command comes from `package.json`, which must define `scripts.dev`. The CLI detects npm, pnpm, yarn, or bun from package metadata or lockfiles and runs that package manager's `run dev` command. You only need to re-run `npm install` after dependencies change. Open the **Local Play** URL printed in the terminal to see the Hello World template served from your machine through the hosted player.

Important

Open the URL in the same browser profile as your tenant.

Note

**Local Network Access Restrictions**

Since December 2025, Chrome and Microsoft Edge browsers block requests from public origins to local endpoints by default. Because your app connects to localhost during development, you might need to grant browser permission or configure enterprise policies. For embedded scenarios, include `allow="local-network-access"` in iframe tags.

Learn more about the local network access restrictions:

- [Permissions-Policy: local-network-access directive](https://developer.mozilla.org/docs/Web/HTTP/Reference/Headers/Permissions-Policy/local-network-access)
- [Adapting your website for new Local Network Access restrictions in Microsoft Edge](https://learn.microsoft.com/en-us/deployedge/ms-edge-local-network-access)

## Add a connector \(optional\)

If your app needs data, add a connector. Start by discovering what's available in your environment with [`ms connector list`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-connector-list):

```bash
ms connector list [--search <query>]
```

The CLI prints matching connectors with their ID, tabular flag, and unified policy status. Discovery includes blocked connectors by default; pass `--only-allowed` to filter them out. [Data Loss Prevention \(DLP\)](https://learn.microsoft.com/en-us/power-platform/admin/prevent-data-loss) and [Advanced Connector Policies \(ACP\)](https://learn.microsoft.com/en-us/power-platform/admin/advanced-connector-policies) are admin-defined rules that govern which connectors your app is allowed to use. Review the status before selecting a connector so you avoid building against a data source that policy blocks at deploy or run time.

Pick one of the listed connectors and add it to your app with [`ms app add data-source`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-add-data-source):

```bash
ms app add data-source --connector <connector>
```

In interactive mode, the CLI walks you through the full setup: choose an existing connection or create a new one, pick a dataset \(for example, a SharePoint site\), and then pick a table. The CLI automatically generates strongly typed models and services into `generated/` - no extra commands needed.

## Commit, build, and push to preview

Now that the app runs locally, commit your work and push it. This push uploads your latest commit to the platform-managed repo. It doesn't trigger a build on its own. The platform builds your app on demand when you open the preview URL.

```bash
git add .
git commit -m "first pass"
git push
```

### Play the app in preview mode

When your app works the way you want locally and you're ready to test it in a hosted environment, open it in preview mode with [`ms app play`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-play):

```bash
ms app play --mode preview
```

If you don't provide an app ID, the command defaults to your current directory's app project.

When you play the app in preview mode, the platform starts a build for your latest pushed commit. You see one of these states in preview if this is your first time hitting the preview after a push:

1. **Build in progress** banner — the platform is building your latest commit.
2. **Build complete. New version of your app is ready.** — select **Refresh** to load the latest build.
3. **Build failed** banner — something went wrong during the build. Run [`ms app build-status`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-build-status) `[--commit <sha>]` to get the full error details, so you can fix the code and push again. If you omit the commit SHA, the command defaults to the current local Git `HEAD`, not the latest built commit. Pass the pushed commit's SHA explicitly if your checkout has moved.

Tip

You can run [`ms app build`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-build) `[--commit <sha>]` at any time to trigger a [platform build](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide#platform-build-and-preview). If you don't provide a commit SHA, it defaults to the current local Git `HEAD`. Push that commit before building, or use `--commit <sha>` for a particular pushed revision. Most of the time, pushing and hitting the preview URL is all you need. Use this command only if you want to kick off a platform build before opening the preview - for example, to warm up the build so the preview loads instantly when you share it, or to confirm a platform build succeeds without leaving the terminal.

## Deploy to live

When the preview looks right, promote to a live app with [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy):

```bash
ms app deploy
```

To deploy a specific earlier commit, pass `--commit <id>`:

```bash
ms app deploy --commit <commit-id>
```

On success, the CLI returns the live app URL. Open it to confirm your app is running for users as a Copilot Managed Runtime app - governed by Microsoft Entra ID, Conditional Access, and ACP policies, with telemetry and operational health flowing through admin center tools.

Congratulations! You deployed your first Copilot Managed Runtime app.

## Variations

Use these optional paths if you want to connect a different source repository, onboard an existing project, or continue development from another machine.

### Automate deployment with GitHub Actions

To build and deploy your app automatically from a GitHub Actions workflow instead of the terminal, create the app for external artifact deployment with [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo none`, then follow [Deploy Microsoft Copilot Managed Runtime apps with GitHub Actions](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/deploy-managed-apps-github-actions?view=o365-worldwide). External artifact deployment is disallowed by default. See [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

### Bring your own GitHub repository

If your team uses GitHub, create an empty external repository, then bind your app to it at create time by passing `--repo`. The repository must contain no tracked files, including a README or license. The local target directory must also be empty, with no hidden files:

```bash
ms app create hello-world --display-name "Hello World" --repo https://contoso.ghe.com/team/hello-world
```

The platform builds, scans, and deploys from the GitHub repository as the single source of truth. Your existing branch policies and pull request reviews continue to apply.

For a repository that already contains source, clone it with `git clone <repository-url>` and run [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init) in the checkout instead of `ms app create`.

Note

The repository must be owned by an organization on GitHub Enterprise Cloud. Repositories can use a `github.com` host or a `*.ghe.com` data-residency host. GitHub Enterprise Server and repositories owned by personal accounts or organizations that aren't on GitHub Enterprise Cloud aren't supported.

Pass a full `https://` repository URL. Bare-host forms such as `contoso.ghe.com/team/hello-world` are rejected. Configure repository visibility and other repository management policies in GitHub Enterprise Cloud. For more information, see [Enforcing repository management policies in your enterprise](https://docs.github.com/enterprise-cloud@latest/admin/enforcing-policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise#about-policies-for-repository-management-in-your-enterprise).

### Convert an existing web project

To turn a project you already have into an app, run [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init) from inside the project directory instead of [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create):

```bash
cd my-existing-web-app
ms app init --display-name "My App"
```

[`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init) provisions an app record, writes `ms.config.json`, and either creates a platform-managed Git repository or keeps your existing Git remote, depending on what it detects in the working directory.

### Clone an app on a new machine

To work on an existing app with platform-managed Git from a new machine, install the prerequisite tools, sign in, and use [`ms app clone`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-clone). This command configures platform-managed Git authentication for the initial clone and subsequent fetch and push operations:

```bash
ms auth login
ms app clone --app <app-id>
cd <app-directory>
npm install
ms app dev
```

Use `ms app list --permission edit` to find an editable app's ID. For external GitHub repositories, obtain repository access separately in GitHub and use `git clone <repository-url>` instead. See [Collaborate on an app](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/collaborate-on-app?view=o365-worldwide).
