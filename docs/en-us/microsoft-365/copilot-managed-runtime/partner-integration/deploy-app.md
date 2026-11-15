<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/partner-integration/deploy-app?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Deploy an app from a Copilot Managed Runtime partner integration \(preview\)

\[This article is prerelease documentation and is subject to change.\]

After you validate an app from a partner integration, deploy it through Copilot Managed Runtime and provide a path for creators and users to open it. The deployment flow supports Git-backed builds and partner-provided artifacts while keeping live promotion explicit.

Deployment changes the live app and should require explicit user confirmation. A successful build is not a successful deployment.

For the standard Git-backed build, deploy, and live-app flow, see the [build, preview, and deploy guide](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide). See the [CLI command reference](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide) for command details.

## Build a Git-backed app

Commit and push the version you want to build. Use its full commit SHA for the following commands. For the standard Git steps, see [Commit, build, and push to preview](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide#commit-build-and-push-to-preview).

For the build commands, `--app` takes the logical app name, not an app ID. Omit it when the CLI can resolve the app from the current project's `ms.config.json`.

```bash
ms app build \
  --app <appName> \
  --commit <fullCommitSha> \
  --no-wait \
  --json
```

Note

`ms app build` waits for a terminal state by default. Submit with `--no-wait`, retain the returned operation and build identifiers, and poll build status to a terminal state while surfacing progress and logs.

Query the submitted build's status:

```bash
ms app build-status \
  --app <appName> \
  --commit <fullCommitSha> \
  --show-log \
  --json
```

## Preview a Git-backed build

Before you promote a build to live, you can open a successful Git-backed build at a hosted preview endpoint in the Copilot Managed Runtime app host. This approach lets you validate the build without changing the currently deployed live version.

Use [`ms app play`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-play):

```bash
ms app play \
  --mode preview \
  --commit <fullCommitSha> \
  --no-browser \
  --json
```

`--commit` targets the specific build you're evaluating. For default preview behavior, see [Preview endpoint behavior](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide#platform-build-and-preview).

## Deploy a Git-backed app

Ensure you push the commit, then:

```bash
ms app deploy \
  --commit <fullCommitSha> \
  --json
```

Keep the selected commit consistent across build, preview, and deployment.

## Deploy a partner-provided artifact

Partner artifact mode applies to an app initialized with `--repo none`. The partner retains ownership of its source and build infrastructure and provides only the deployable output, so it doesn't need to expose or synchronize a source repository. Unlike a Git-backed deployment, the service accepts an artifact produced by the partner's build or pipeline instead of building from a Git commit.

### Enable external artifact deployment

Important

**Allow External Artifact Deployment** is disabled by default. An environment administrator can enable it in the Power Platform Admin Center for the target environment. Most developers don't have permission to turn on this setting, which makes partner artifact deployment more restrictive than the default platform-provided Git flow. Partners should plan for administrator approval and configuration before deployment. When enabled, the setting allows the service to accept deployable artifacts from partner pipelines rather than building from a Git repository.

For the administrator procedure, see [External artifact deployment](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/governance?view=o365-worldwide#external-artifact-deployment).

### Build and deploy

From the app root, verify that the local build succeeds:

```bash
ms app pack
```

To let the CLI pack and upload the local app, run:

```bash
ms app deploy --json
```

To deploy a prebuilt ZIP file from your pipeline instead, pass its path:

```bash
ms app deploy \
  --artifact <artifactPath> \
  --json
```

Don't pass `--artifact` for a Git-backed app.
