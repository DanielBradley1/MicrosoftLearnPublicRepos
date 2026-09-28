<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-1-clone-the-kit -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Step 1: Clone the Agent Developer Kit

This article covers the **manual install** path. Most users should start with [the one-shot installer](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-installer) on Windows or [GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) in the browser. Both options do the cloning, dependency install, and VS Code setup for you. Use the manual install when you want full control over what gets installed where, or when you're on macOS or Linux and prefer a local setup over Codespaces.

In this step, you get the kit on your computer and open it in Visual Studio Code. The whole step takes about 5 minutes.

Important

Open the **`solutions/ess-maker-skills`** subfolder as your workspace, NOT the top level of the repo. The kit's commands only work when `ess-maker-skills` is the workspace root.

## Before you start

You need:

- **Git** - if you don't have it, download from [git-scm.com](https://git-scm.com/downloads).
- **Visual Studio Code** - if you don't have it, download from [code.visualstudio.com](https://code.visualstudio.com/).

To confirm both are installed, open a terminal and run:

```powershell
git --version
code --version
```

Both commands should print a version number.

## Clone the repo

Open a terminal in the folder where you want to keep the kit \(for example, your `Documents` or a `GitHub` folder under your home directory\). Run:

```powershell
git clone https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit.git
```

Git downloads the repo into a new folder named `Employee-Self-Service-Agent-Developer-Kit`.

## Open the right folder in VS Code

In the same terminal, change into the repo and open VS Code on the `ess-maker-skills` subfolder:

```powershell
cd Employee-Self-Service-Agent-Developer-Kit
code solutions/ess-maker-skills
```

The `code` command opens VS Code with that folder as the workspace.

If you prefer to use VS Code's UI:

1. Open VS Code.
2. Select **File** > **Open Folder**.
3. Navigate to where you cloned the repo.
4. Open `Employee-Self-Service-Agent-Developer-Kit` -> `solutions` -> `ess-maker-skills`.
5. Select **Select Folder**.

## You should see

When VS Code opens, the Explorer pane on the left should show `ESS-MAKER-SKILLS` at the top, with these folders directly underneath:

```text
ESS-MAKER-SKILLS
  .github
  .vscode
  scripts
  src
```

If the Explorer shows `EMPLOYEE-SELF-SERVICE-AGENT-DEVELOPER-KIT` at the top instead \(with extra folders like `.github`, `samples`, `solutions`, `tests`\), you opened the wrong folder. Close the workspace and reopen `solutions/ess-maker-skills`.

## Accept the recommended extensions

VS Code may show a notification in the lower-right asking if you want to install the workspace's recommended extensions. Select **Install**. The kit needs the GitHub Copilot Chat extension, which you set up in the next step.

## Next step

Continue with [Step 2: Install GitHub Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot).
