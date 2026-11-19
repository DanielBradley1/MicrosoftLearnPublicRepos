<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/dev-inner-loop?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Build, preview, and deploy Microsoft Copilot Managed Runtime apps

The Copilot Managed Runtime apps *inner loop* is a fast, Git-native workflow for building, previewing, and deploying apps. Edit code in your IDE, commit and push it, and let the platform build the pushed commit for the preview endpoint. When you're ready to go live, deploy explicitly by using [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy).

This article describes how each phase of the inner loop works, what the platform does behind the scenes, and where your work lives at each step. It complements [Quickstart: Build a Microsoft Copilot Managed Runtime app with GitHub Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-github-copilot?view=o365-worldwide) and [Quickstart: Create an app with the Copilot Managed Runtime SDK](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/quickstart-managed-apps-cli?view=o365-worldwide), which walk through the same flow end-to-end with commands.

This article describes Command Line Interface \(CLI\) commands that you can enter in a command line based terminal window. Agents such as GitHub Copilot have similar skills and can also issue these commands as needed. For example, you can ask an agent to simply "deploy" and it runs the equivalent of `ms app deploy`. You don't need to learn all of these commands, but they're always here if you need them.

## What to expect

A few behaviors shape the whole experience. Knowing them up front makes the rest of the inner loop predictable.

- **It's Git-native.** The `ms` CLI works with real Git rather than replacing it. You use [`git add`](https://git-scm.com/docs/git-add), [`git commit`](https://git-scm.com/docs/git-commit), and [`git push`](https://git-scm.com/docs/git-push) the same way you would on any project, so your coding agents, branch policies, and existing workflows all carry over.
- **Builds happen when you need them.** A [`git push`](https://git-scm.com/docs/git-push) updates your source of truth but doesn't build anything on its own. The platform builds on demand: when you open the preview, when you deploy, or when you run a build yourself.
- **Preview is automatic; going live is deliberate.** Every successful build is available to preview, for all commits and branches. Promoting one to your live app is always an explicit step you take.
- **Every build is addressable.** Each build has a stable ID, a status, and the commit it came from, so you can target any build by using `--commit <sha>` when you check its status or deploy it.

## Repository modes

Every app uses one of three repository modes. You choose the mode at [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) or [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init). The mode is fixed for the life of the app, and switching modes requires creating a new app.

| Mode | Trigger | Source of truth | When to use |
| --- | --- | --- | --- |
| **Platform-managed Git \(default\)** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) with no `--repo` flag | A repository the platform provisions and manages on your behalf | Teams that don't have an existing source-control setup, or that want zero-configuration Git out of the box. |
| **Bring your own GitHub** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo <url>` | An external repository owned by a GitHub Enterprise Cloud organization | Teams that already standardize on GitHub Enterprise Cloud and want their existing branch policies, pull request reviews, and CI to apply to the managed app. |
| **Bring your own build** | [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) `--repo none` | There is no repository that the platform is aware of. In this case, you must build the code yourself to deploy to the platform. | Use this mode if you don't want to manage source via GitHub or platform-managed git. |

## Environments

Every developer, and every coding agent that creates apps on their behalf, lands in an **environment**: a secure sandbox the platform provisions on first [`ms app create`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-create) or [`ms app init`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-init).

An environment is identity-scoped, automatically provisioned, and inherits your organization's policies from the moment it exists. You don't request it; you just start working, and it's there. These environments are preconfigured with a Microsoft-managed baseline of admin policies, so governance applies from the moment you start creating. Administrators can then validate and customize the baseline as needed.

## Add dependencies

After you run `ms app create`, the app directory contains the scaffolding for an app. The next step is to add packages that the app depends on by using `npm install`.

You only need to complete this step once, unless you add more packages later.

## The inner loop

From creation to long-term, dependable usage, apps cycle through a loop:

1. **Edit and run locally:** Create the app and iterate in a tight loop through editing and seeing the results of a change quickly. The app only exists for one contributor on a single machine.
2. **Save to source control:** Use Git add, commit, and push commands to preserve your changes and collaborate with other contributors.
3. **Platform build and preview:** Build the app on the platform and preview it from the cloud.
4. **Deploy to production:** Share the app with end users for production use. Your app is live.
5. **Monitor health and usage:** Make sure your app stays available and gauge usage for further investments.

The loop repeats with user feedback, new ideas, changes in requirements, and countless other reasons.

If something goes wrong along the way, source control enables you to deploy a previously known good version and unblock end users. For more information, see the section on [reverting to a previous version](#revert-to-a-previous-version).

### Edit and run locally

Edit code in your preferred IDE and play the app locally with [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev). This command doesn't return; instead, it starts working and can shut down with a Ctrl+C key combination. If you start this command with an agent, such as GitHub Copilot, it shows that a background task is running.

While it's working, this command performs two tasks:

- It acts as a web server on your local machine to play the app. It prints the URL that you can use to preview the app in local mode, and it might also open a browser to this URL.
- It monitors for changes in your app as you continue to make edits. If it detects one, it automatically refreshes the browser with the update.

The URL that [`ms app dev`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-dev) provides starts with `https://play.managedapps.cloud.microsoft/...`, which is different from the URL you might see with other Node-based local development. This remote URL calls back to the local computer for most of the web content, but it also provides a gateway to access remote data services and connectors. This setup enables playing a local app with data in a remote data source such as Dataverse, SharePoint, or from any other connector.

At this point:

- Your work lives only on the local machine, and only you can play it. Add, commit, and push in the next phase to preserve and collaborate with other contributors, including yourself on another machine.
- There's no build or deploy required. The web server runs off the raw source files, which facilitates rapid development.

### Save to source control

When the app behaves the way you want locally, save this version to source control to preserve it and collaborate with other contributors.

In the root directory of the app, follow these steps to bottle this version of the app and to push it to the remote Git repository.

- `git add .` adds all the files that you modified to the next commit. The `.` tells git to include all files in this directory and subdirectories. You can safely ignore any warnings about LF and CRLF line endings.
- `git commit` creates the commit. A commit is a specific version of your app that you can refer to later with a commit ID. Git asks for a message to label this commit, so you and others know what changed with this version.
- `git push` sends the commit to the server for safekeeping and for preview. The push updates the remote repository, either the platform-managed Git repo or your bound external GitHub repo.

At this point:

- Your work now lives both on your local machine and in the remote repository. Your changes are safely stored on the platform and are no longer isolated to one machine. Other contributors can see and preview your changes. You can still use `ms app dev` as you see fit for further changes.
- The push doesn't trigger a build by itself. The remote now has a new commit that the platform considers a buildable version.

If you're using "bring your own build" mode, these commands might be different for you.

### Platform build and preview

When you save a commit to the platform, you and other contributors can play it directly. Enter the command [`ms app play --mode preview`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-play) to display the URL for the preview. Hold down the Ctrl key and select the URL, or copy and paste the URL into a browser.

By default, preview selects the current Git branch. If the CLI can't identify the branch, it warns and falls back to `main`. Use `ms app play --mode preview --branch <name>` for a particular branch or `ms app play --mode preview --commit <sha>` for a particular commit. `--branch` and `--commit` are mutually exclusive.

If you didn't play this version of the app before, the platform builds the app on demand. If a previous build exists, the platform plays that older build while you wait and asks you to refresh when it's done.

All Git commits saved to the platform are runnable by any contributor, at any time. Use this feature to compare changes between versions with two separate browser windows. To access a particular commit, use these URLs:

- `https://play.managedapps.cloud.microsoft/apps/<appId>/commit/<commitSHA>` where you replace `<appId>` with the app ID GUID displayed by [`ms app info`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-info) and `<commitSHA>` with the full SHA code displayed by `git log -1`.
- `https://play.managedapps.cloud.microsoft/apps/<appId>/branch/<branchName>`. The default branch name is `main` but you can play the head of any Git branch in this manner.

In addition to building apps on demand via preview, use the [`ms app build`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-build) command to explicitly start a build.

If a build fails, the preview endpoints continue serving the last successful build for the app. To find out why it failed, run [`ms app build-status`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-build-status). The output reports the failed build and the reason it failed, so you can fix the code and push again.

If you're using "bring your own build" mode, these preview URL endpoints aren't available to you. You're responsible for creating the build and sending it to the platform.

### Deploy to production

When the preview looks good, use [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) to promote it to the production version that you share with end users. Further development, commits, and previews don't affect the deployed version until you do another deployment.

The URL for the live production version of the app doesn't include a commit or branch identifier. For example, a viable production URL might look like `https://play.managedapps.cloud.microsoft/apps/00000000-0000-0000-0000-000000000000`. This URL doesn't change with subsequent deployments. Until you complete the first deployment, the portal shows a non-deployment message to end users.

Initially, only owners of the app can play the deployed app. Use [`ms app share`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-share) to share with others. You can also manage users at [https://managedapps.cloud.microsoft](https://managedapps.cloud.microsoft) and generate shareable URLs.

For Git-backed apps, with no switches, [`ms app deploy`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) selects the current local Git `HEAD`. If there are uncommitted changes or local commits ahead of the remote, the CLI asks for confirmation in interactive mode and stops with a usage error in non-interactive or JSON mode unless you pass `--force`. Go through the [add, commit, and push](#save-to-source-control) flow to include intended changes. `--force` only bypasses preflight; it doesn't upload uncommitted or unpushed source.

Use [`ms app deploy --commit <commitSHA>`](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/ms-cli-command-reference?view=o365-worldwide#ms-app-deploy) to deploy a specific commit. Use this command to revert to a previous version of the app if there are problems with a new deployment.

Deployment reuses a cached build or submits a build for the selected commit and waits for completion. If that build fails or is canceled, deployment stops; it doesn't fall back to an older successful build. The old deployed version remains unchanged.

### Monitor health and usage

After you deploy an app, monitor it to ensure it's operating properly and to measure usage. For more information, see [monitor apps](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/apps/monitor-apps?view=o365-worldwide).

### Revert to a previous version

Sometimes, a change doesn't work out the way you thought and you'd like to return to the previous version.

You can deploy any commit from any branch at any time. Review `git log` to understand who made changes, when, and the message they provided on what the change was. Use this information to identify a commit ID that you want to revert to. Then use `ms app deploy --commit <commitID>` to revert to that version.

The change that wasn't perfect is still there because nothing is lost in source control. By restoring the app for end users, you can take a look at the problematic commit and the known good one and decide how to move forward. You might make small tweaks to the tip or head of the branch, or simply commit the old version ahead of the new one. When you're ready, create a new commit at the top of your `main` or other branch and deploy it.
