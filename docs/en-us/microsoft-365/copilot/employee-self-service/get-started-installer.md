<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-installer -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Install the Agent Developer Kit with the one-shot installer

The one-shot installer is the fastest way to get the kit running on a Windows machine. One command installs Visual Studio Code, Python, Git, PowerShell 7, and the GitHub CLI, clones the kit, installs the GitHub Copilot Chat extension, and opens the right folder in VS Code. The whole step takes about 10 minutes, most of it spent on downloads.

Note

The one-shot installer is Windows only. If you're on macOS or Linux, or you can't install software locally, use [GitHub Codespaces](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces) instead.

## Before you start

You need:

- A Windows 10 or Windows 11 machine where you can install software.
- A GitHub account with an active GitHub Copilot subscription. If you aren't sure, your administrator can confirm in the GitHub organization settings.
- Permission to run PowerShell with internet access.

## Run the installer

1. Open **PowerShell** \(Windows key, type `powershell`, select **Windows PowerShell**\).
2. Paste this command and select **Enter**:

   ```powershell
   iex (irm https://raw.githubusercontent.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/main/setup/bootstrap.ps1)
   ```

The installer prints what it's about to do, then runs through the steps. You may see Windows prompts asking you to confirm software installs. Approve each one.

## What the installer does

While it runs, the installer:

- Installs Visual Studio Code, Python 3.12, Git, GitHub CLI, and PowerShell 7 using `winget`. Tools already installed are skipped.
- Installs the Python packages the kit needs.
- Clones the Employee Self-Service Agent Developer Kit repo into your user folder.
- Installs the GitHub Copilot, GitHub Copilot Chat, and Python extensions in VS Code.
- Opens VS Code on the `solutions/ess-maker-skills` folder.

The installer is idempotent. If something interrupts it, run the same command again. It picks up where it left off and skips work already done.

## Sign in to GitHub Copilot

When VS Code opens, the bottom-right corner shows a sign-in prompt for GitHub Copilot.

1. Select **Sign in to GitHub**.
2. Your browser opens to GitHub.
3. Authorize VS Code to use your GitHub account.
4. The browser returns you to VS Code. The account icon in the lower left now shows your GitHub username.

If VS Code reports that your account doesn't have Copilot access, confirm your subscription at [github.com/settings/copilot](https://github.com/settings/copilot).

## You should see

When the installer finishes:

- VS Code is open with `ESS-MAKER-SKILLS` at the top of the Explorer pane.
- The Explorer shows `.github`, `.vscode`, `scripts`, and `src` as the top folders.
- The Copilot Chat pane is available from the activity bar on the left.

If the Explorer shows `EMPLOYEE-SELF-SERVICE-AGENT-DEVELOPER-KIT` at the top with extra folders \(`samples`, `solutions`, `tests`\), the installer opened the wrong folder. Close the workspace and reopen `solutions/ess-maker-skills`.

## Pick a recommended model

The kit asks the model to detect tools, follow multi-step instructions, and write valid YAML. Not all models do these actions equally well.

Open the Copilot Chat pane \(the Chat icon on the activity bar\). On the top of the chat pane, there's a model picker. Pick a current frontier model from one of these families:

| Model family | Why |
| --- | --- |
| Claude Sonnet \(latest available\) | Recommended. Reliable tool detection and multi-step instruction-following. |
| Claude Opus \(latest available\) | Recommended. Same strengths as Sonnet; higher quality, slightly slower. |
| OpenAI Codex or GPT-5 class \(latest available\) | Recommended. Works well for the kit's setup flows. |

Note

The models in the picker change over time as new versions ship. Pick the most recent version available in one of the previously listed families rather than an exact version number.

If you don't see any of these families in the picker, they may not be enabled by your organization. Choose the closest equivalent. If the kit later reports that it can't find its tools, the most common fix is to switch to a recommended model.

## Next step

Continue with [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup).

If the installer didn't finish, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).
