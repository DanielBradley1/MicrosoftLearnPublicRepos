<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/collaborate-on-app?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Collaborate on an app \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use the Copilot Managed Runtime CLI to collaborate on an existing app, including an app created in Copilot Cowork or Microsoft Copilot Studio. Apps created in these experiences are backed by Git. After the app owner grants you edit access, you can find the app, clone its repository, and continue development in your preferred code editor.

## Prerequisites

Before you begin, make sure you have:

- The Copilot Managed Runtime CLI and [Node.js](https://nodejs.org/) installed.
- [Git](https://git-scm.com/downloads) installed with Git Credential Manager configured.
- Access to the tenant that contains the app.
- Edit access to the app. The app owner must grant this access before you can find and clone the app. For more information, see [Share a Microsoft Copilot Managed Runtime app with users and groups \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/share-app?view=o365-worldwide).

Sign in to the Copilot Managed Runtime CLI:

```bash
ms auth login
```

## Find the app ID

Sign in with the account that received edit access, and then list the apps that you can edit:

```bash
ms app list --permission edit
```

Find the app you want to edit, and copy its **App ID**. The app ID is the GUID that you use to clone the repository.

Tip

If the app doesn't appear, verify that you're signed in with the account that received edit access and that the owner shared the app by using `--access edit`.

## Clone the app

Use [`ms app clone`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-clone) with the app ID to clone the app's platform-managed Git repository:

```bash
ms app clone --app <app-id> [directory]
```

For example, if the app's display name is `Inventory App`, the CLI creates the `Inventory App` folder:

```bash
ms app clone --app 00000000-0000-0000-0000-000000000000
cd "Inventory App"
```

The `[directory]` argument is optional. If you omit it, the CLI creates a folder named after the app's display name and clones the repository into that folder. To clone into the current directory, which must be empty, specify `.` as the directory. If the app's display name isn't a valid folder name, specify a different directory. The CLI finds the repository from the app record and configures Git authentication for future fetch and push operations.

Note

`ms app clone` supports platform-managed Git repositories. If the app uses an external GitHub or GitHub Enterprise Cloud repository, you must have access to that repository and use `git clone <repository-url>` instead. You can't clone an app that doesn't have a source-control binding.

## Start developing

From the cloned project directory, install the app's dependencies:

```bash
npm install
```

Start the local development loop:

```bash
ms app dev
```

You can now edit and test the app locally. Pull the latest changes before you begin a new development session. When your changes are ready, use standard Git commands to commit and push them:

```bash
git pull
git add .
git commit -m "Describe the change"
git push
```

The pushed commit updates the app's source repository. It doesn't update the live app. To build, preview, and deploy the changes, see [Build, preview, and deploy Microsoft Copilot Managed Runtime apps \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/dev-inner-loop?view=o365-worldwide).

## Related information

- [Build, preview, and deploy Microsoft Copilot Managed Runtime apps \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/dev-inner-loop?view=o365-worldwide)
- [Share a Microsoft Copilot Managed Runtime app with users and groups \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/share-app?view=o365-worldwide)
- [Copilot Managed Runtime architecture \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/architecture?view=o365-worldwide)
- [Copilot Managed Runtime CLI command reference \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide)
