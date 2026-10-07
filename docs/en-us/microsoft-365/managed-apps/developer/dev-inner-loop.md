<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/dev-inner-loop?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Build, preview, and deploy Microsoft Copilot Managed Runtime apps \(preview\)

\[This article is prerelease documentation and is subject to change.\]

The Copilot Managed Runtime apps *inner loop* is a fast, Git-native workflow for building, previewing, and deploying apps. Edit code in your IDE, commit and push it, and let the platform build the pushed commit for the preview endpoint. When you're ready to go live, deploy explicitly by using [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).

This article describes how each phase of the inner loop works, what the platform does behind the scenes, and where your work lives at each step. It complements [Quickstart: Build a Microsoft Copilot Managed Runtime app with GitHub Copilot \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-github-copilot?view=o365-worldwide) and [Quickstart: Create an app with the Copilot Managed Runtime SDK \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/quickstart-managed-apps-cli?view=o365-worldwide), which walk through the same flow end-to-end with commands.

## What to expect

A few behaviors shape the whole experience. Knowing them up front makes the rest of the inner loop predictable.

- **It's Git-native.** The `ms` CLI works with real Git rather than replacing it. You use [`git add`](https://git-scm.com/docs/git-add), [`git commit`](https://git-scm.com/docs/git-commit), and [`git push`](https://git-scm.com/docs/git-push) the same way you would on any project, so your coding agents, branch policies, and existing workflows all carry over.
- **Builds happen when you need them.** A `git push` updates your source of truth but doesn't build anything on its own. The platform builds on demand: when you open the preview, when you deploy, or when you run a build yourself.
- **Preview is automatic; going live is deliberate.** Every successful build is available to preview. Promoting one to your live app is always an explicit step you take.
- **Every build is addressable.** Each build has a stable ID, a status, and the commit it came from, so you can target any build by using `--commit <sha>` when you check its status or deploy it.

## Repository modes

Every app is bound to one of two repository modes. You choose the mode at [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) or [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-init). The mode is fixed for the life of the app, and switching modes requires creating a new app.

| Mode | Trigger | Source of truth | When to use |
| --- | --- | --- | --- |
| **Platform-managed Git \(default\)** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) with no `--repo` flag | A repository the platform provisions and manages on your behalf | Teams that don't have an existing source-control setup, or that want zero-configuration Git out of the box. |
| **Bring your own GitHub** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo <url>` | An external repository owned by a GitHub Enterprise Cloud organization | Teams that already standardize on GitHub Enterprise Cloud and want their existing branch policies, pull request reviews, and CI to apply to the managed app. |
| **Bring your own build** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo none` | There is no repository that the platform is aware of. In this case, you must build the code yourself to deploy to the platform. | Use this mode if you do not want to manage source via GitHub or platform-managed git. |

## Environments

Every developer, and every coding agent that creates apps on their behalf, lands in an **environment**: a secure sandbox the platform provisions on first [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-create) or [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-init).

An environment is identity-scoped, automatically provisioned, and inherits your organization's policies from the moment it exists. You don't request it; you just start working, and it's there. These environments are preconfigured with a Microsoft-managed baseline of admin policies, so governance applies from the moment you start creating. Administrators can then validate and customize the baseline as needed.

## The inner loop cycle

A typical iteration on an app moves through four phases. At each phase, it's clear where your work lives.

### Edit and run locally

You edit code in your IDE of choice and run the app locally with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-dev). The CLI orchestrates the full local loop: it starts your project's dev process and prints the play URL. The local app is exactly what you see in the browser: no platform calls, no build, no deploy.

At this point your work lives only in your working tree. You didn't commit or push yet.

### Commit and push

When the app behaves the way you want locally, commit with `git commit` and push with `git push`. The push updates the remote repository, either the platform-managed Git repo or your bound external GitHub repo. The push **doesn't** trigger a build by itself. The remote now has a new commit that the platform considers a buildable candidate.

Your work now lives in the remote repository.

### Platform build

A **platform build** is the compiled artifact the platform creates from your source code when you:

- [Preview your app](#preview)
- [Deploy your app](#deploy)
- Build your app using [`ms app build`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-build)

Each build is identified by the commit SHA it came from and has its own status \(building, successful, or failed\). Every successful platform build is automatically available at your preview endpoint and can be deployed to your live app using [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).

### Preview

The first time the preview endpoint is hit for a commit that doesn't yet have a build, the platform queues a build for that commit. The preview URL renders the result.

### Deploy

When the preview looks right, [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) promotes a successful build to the live app. The live URL serves the deployed build until the next [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).

Your live app stays on this deployed build, independent of the preview, which always follows your latest successful build.

### Failure handling

If a build fails, the preview endpoint continues serving the last successful build for the app. To find out why it failed, run [`ms app build-status`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-build-status):

```bash
ms app build-status --app <name> --commit <sha>
```

The output reports the failed build and the reason it failed, so you can fix the code and push again. The next push triggers a new build attempt when it's accessed; there's no manual retry command in the initial release.

## Preview endpoint behavior

The preview URL is a stable, per-app URL, separate from the live URL. Think of it as "the latest successful build on `main`." The platform resolves it by checking recent builds:

| Build state | Preview behavior |
| --- | --- |
| Latest commit has a successful build | Renders the build. |
| Latest commit is still building | Renders the previous successful build with an in-progress banner: *"Latest build is in progress."* |
| Latest commit failed to build | Renders the previous successful build with a failure banner: *"Latest build failed. Showing the last successful build."* |
| App has no successful build yet | Renders a dedicated "never deployed" experience. |

Opening the preview for a commit that has no build starts one.

Preview access is scoped to developers with write access to the bound repository. The preview URL isn't shareable with arbitrary users; that's what the live URL plus [`ms app share`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share) is for.

## Deploy your app to go live

Use [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) to promote a successful build to the live app. The behavior depends on what's available:

- **With no flag**, the command deploys the latest successful build on `main`. If the latest commit is itself successful, the command deploys that build.
- **If the latest build failed**, the command falls back to the most recent successful build on `main` and surfaces a warning. You see exactly what you're deploying and what was skipped.
- **If a build is still in progress**, [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) points you to [`ms app build-status`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-build-status) rather than waiting for the build to finish.
- **With `--commit <sha>`**, the command pins a specific earlier commit. Use this option to roll back to a known-good build without reverting your repository history.

The live URL is what you share with end users via [`ms app share`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-share) and share links. It only updates when you run [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy); the live build is a fixed snapshot until you deploy again.
