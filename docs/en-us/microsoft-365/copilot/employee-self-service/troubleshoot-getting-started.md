<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Troubleshoot getting started with the Agent Developer Kit

This article covers the most common stumbles in the first 20 minutes with the kit. If your issue isn't here, run `/troubleshoot` in chat for interactive triage, or file an issue in the [kit repo](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/issues).

## The one-shot installer fails on a winget step

**Symptom**: You run the PowerShell one-liner from [Install with the one-shot installer](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-installer) and it stops with an error about `winget` not being found, or a specific tool \(Python, Git, VS Code\) failing to install.

**Cause**: Either `winget` isn't available on your machine \(it ships with Windows 10 1809+ and Windows 11\), or your account doesn't have permission to install software.

**Fix**:

1. Confirm `winget` works. Open PowerShell and run `winget --version`. If you get an error, install **App Installer** from the [Microsoft Store](https://apps.microsoft.com/detail/9NBLGGH4NNS1).
2. Confirm you can install software on this machine. On a corporate-managed device, your IT admin may block `winget`. If they do, use [GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) instead.
3. Rerun the installer. It's idempotent and picks up from where it stopped.

If the installer still fails on the same step, install that tool manually from the vendor's site \(for example, [python.org](https://www.python.org/downloads/) for Python\), then rerun the installer with `-SkipToolchain` to skip the toolchain step.

## The Codespace builds but the kit's commands don't appear

**Symptom**: Your Codespace finishes building but when you type `/` in Copilot Chat, you only see built-in commands, not `/setup` or `/scan`.

**Cause**: The Codespace opens the repo root by default, not the `ess-maker-skills` subfolder.

**Fix**:

1. From the menu, select **File** > **Open Folder**.
2. Enter `/workspaces/Employee-Self-Service-Agent-Developer-Kit/solutions/ess-maker-skills`.
3. Select **OK**. VS Code reloads with the right folder open.

See [Install with GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces#open-the-right-folder).

## The commands don't appear when I type /

**Symptom**: You type `/` in Copilot Chat but only the built-in commands appear. None of the kit's commands \(`/setup`, `/scan`, `/create`, and so on\) show up.

**Cause**: You opened the wrong folder as your workspace. The kit's commands are loaded from the workspace and only work when `ess-maker-skills` is the workspace root.

**Fix**:

1. In Visual Studio Code, select **File** > **Close Folder**.
2. Select **File** > **Open Folder**.
3. Navigate into the cloned repo and open the `solutions/ess-maker-skills` subfolder.
4. The Explorer pane should now show `ESS-MAKER-SKILLS` at the top with `.github`, `.vscode`, `scripts`, and `src` as the top folders. If it shows `EMPLOYEE-SELF-SERVICE-AGENT-DEVELOPER-KIT` instead, you opened the wrong folder.

See [Step 1: Clone the kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-1-clone-the-kit#open-the-right-folder-in-vs-code).

## Copilot Chat says no model available

**Symptom**: When you open the Copilot Chat pane, the model picker is empty or shows "no model available".

**Cause**: You're signed in to GitHub but your account doesn't have an active Copilot subscription, or your organization doesn't allow your account to use Copilot Chat.

**Fix**:

1. Visit [github.com/settings/copilot](https://github.com/settings/copilot) and confirm Copilot is enabled on your account.
2. If you're part of an organization, your administrator may need to grant Copilot access. Ask your administrator to confirm in the GitHub organization settings.
3. After your access is sorted, sign out of GitHub in VS Code \(account icon in the lower-left\) and sign in again.

## /setup says no tools available

**Symptom**: You run `/setup` and the kit responds with a message like "I can't find the tools I need" or "no MCP tools available".

**Cause**: Either the model you selected doesn't reliably detect the kit's tools, or your Power Platform environment doesn't have the Microsoft GitHub Copilot client enabled.

**Fix - first try the model**:

Switch to a [recommended model](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot#pick-a-recommended-model) in the chat model picker \(a current Claude Sonnet, Claude Opus, or OpenAI Codex model\). Rerun `/setup`.

**Fix - if the model is recommended**:

Your Power Platform admin needs to enable the kit:

1. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), open the environment.
2. Select **Settings** > **Features**.
3. Find **Dataverse Model Context Protocol** and turn on **Allow MCP clients \(GA version\)**.
4. In **Advanced Settings**, enable **Microsoft GitHub Copilot** as a client.

For more, see [Connect Dataverse MCP with VS Code](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-mcp-vscode).

## Device-code sign-in opens the wrong account

**Symptom**: The browser opens for sign-in but you only see your personal Microsoft account, not your work account.

**Cause**: Your browser is already signed in to the wrong account.

**Fix**:

1. In the browser, sign out of the personal account.
2. Sign in with your work account that has access to the Power Platform environment.
3. Return to VS Code, run `/setup` again, and use the new code that the kit shows you. \(Codes expire after a few minutes; don't reuse an old one.\)

If your organization uses multiple tenants, make sure you're signing in to the tenant that owns the Power Platform environment with Employee Self-Service.

## /setup can't find any Employee Self-Service agents

**Symptom**: You sign in successfully but the kit reports zero agents in your environment.

**Cause**: One of the following options:

- Employee Self-Service isn't installed in this environment.
- You're connected to the wrong environment.
- Your account doesn't have the Environment Maker role in this environment.

**Fix**:

1. Sign in to [Copilot Studio](https://copilotstudio.microsoft.com/) in your browser with the same work account.
2. Confirm the environment selector at the top of the page matches the environment you want.
3. Confirm you can see the Employee Self-Service agent in the Agents list. If you can't, Employee Self-Service isn't installed in that environment. See [Install the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install).
4. If Employee Self-Service is there but the kit doesn't see it, your account may not be assigned the Environment Maker role. See [Prerequisites - Required roles](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites#required-roles).

## /setup hangs partway through extraction

**Symptom**: The kit shows progress for a while, then stalls without finishing.

**Cause**: Usually network. Power Platform's APIs occasionally throttle, especially in shared environments.

**Fix**:

1. Wait a minute or two. Most extractions resume on their own.
2. If the message in chat still says "extracting" after five minutes with no progress, ask the kit to retry:

   ```text
   /setup
   ```

3. If it still fails, switch to a different network \(for example, off VPN\), or try again later. Persistent failure on a clean network usually means an environment-side issue worth opening with your admin.

## I opened the workspace but VS Code looks empty

**Symptom**: The Explorer pane shows the workspace name but no files.

**Fix**: The clone was interrupted. Delete the folder and clone again. See [Step 1: Clone the kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-1-clone-the-kit).

## I switched models and the kit behaves differently

**Symptom**: Commands worked yesterday but today the responses are confused or the kit can't find its tools.

**Fix**: Confirm the model picker shows one of the [recommended models](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot#pick-a-recommended-model). Switch back if it doesn't.

## Where to ask for help

- Run `/troubleshoot` in the chat pane for interactive triage.
- File an issue in the [kit repo](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/issues).
- For broader Employee Self-Service product issues \(publishing delays, the agent itself, integrations\), see [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations).
