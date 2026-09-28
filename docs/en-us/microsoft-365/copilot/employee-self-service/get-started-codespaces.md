<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-codespaces -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Install the Agent Developer Kit with GitHub Codespaces

GitHub Codespaces gives you a cloud-hosted Visual Studio Code in the browser, with the kit preinstalled. You don't install anything on your own machine. The whole step takes about 5 minutes.

Use Codespaces when:

- You can't install software locally \(corporate-managed device, locked-down environment\).
- You're on macOS, Linux, or any non-Windows machine.
- You want to try the kit before deciding whether to install it locally.

## Before you start

You need:

- A GitHub account with an active GitHub Copilot subscription.
- A modern browser.

Codespaces includes a [free tier](https://docs.github.com/en/billing/managing-billing-for-your-products/managing-billing-for-github-codespaces/about-billing-for-github-codespaces#monthly-included-storage-and-core-hours-for-personal-accounts) of 120 core-hours per month \(60 hours on the 2-core machine the kit uses\). The Codespace pauses automatically after 30 minutes of inactivity, so you're only billed for time you're actively working.

If your GitHub account is part of an organization and Codespaces isn't available, your administrator may need to enable it. See [Managing Codespaces for your organization](https://docs.github.com/en/codespaces/managing-codespaces-for-your-organization).

## Create the Codespace

1. Open this link in your browser:

   [https://github.com/codespaces/new?repo=microsoft/Employee-Self-Service-Agent-Developer-Kit&ref=main&devcontainer\_path=.devcontainer%2Fdevcontainer.json](https://github.com/codespaces/new?repo=microsoft/Employee-Self-Service-Agent-Developer-Kit&ref=main&devcontainer_path=.devcontainer%2Fdevcontainer.json)
2. Sign in to GitHub if prompted.
3. On the **Create codespace** page, leave the defaults and select the **2-core** machine type.
4. Select **Create codespace**.

GitHub builds the Codespace. The first build takes a couple of minutes because it installs Python, the kit's dependencies, and the GitHub Copilot extensions. Subsequent starts of the same Codespace are faster.

## Open the right folder

When the Codespace finishes building, you land in VS Code in the browser at the repo root. The kit's commands only work when `ess-maker-skills` is the workspace root.

1. From the menu, select **File** > **Open Folder**.
2. Enter `/workspaces/Employee-Self-Service-Agent-Developer-Kit/solutions/ess-maker-skills`.
3. Select **OK**.

VS Code reloads with the right folder open.

## You should see

The Explorer pane shows `ESS-MAKER-SKILLS` at the top, with these folders directly underneath:

```text
ESS-MAKER-SKILLS
  .github
  .vscode
  scripts
  src
```

If the Explorer shows the full repo name at the top with extra folders like `samples`, `solutions`, and `tests`, you opened the wrong folder. Select **File** > **Open Folder** again and use the path in the previous section.

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

## Manage your Codespace

You can stop, restart, and delete your Codespace from [github.com/codespaces](https://github.com/codespaces). Your work is saved between sessions. When you're done with the kit, delete the Codespace to free up your storage quota.

## Next step

Continue with [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup).

If the Codespace didn't build or doesn't open the right folder, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).
