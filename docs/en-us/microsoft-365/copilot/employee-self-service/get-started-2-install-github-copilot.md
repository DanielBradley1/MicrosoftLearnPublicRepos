<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Step 2: Install GitHub Copilot Chat

In this step, you install the GitHub Copilot Chat extension, sign in, and pick a model the kit works well with. The whole step takes about 5 minutes.

## Before you start

You need an active GitHub Copilot subscription on your GitHub account. Most enterprise users have one through their organization. If you aren't sure, your administrator can confirm in the GitHub organization settings.

## Install the extension

1. In Visual Studio Code, open the Extensions view: **View** > **Extensions**, or select Ctrl+Shift+X.
2. In the search box, type `GitHub Copilot`.
3. Find **GitHub Copilot Chat** \(publisher: GitHub\) in the results and select **Install**.

The base **GitHub Copilot** extension installs as a dependency. You don't need to install it separately.

## Sign in to GitHub

When the extension finishes installing, VS Code shows a sign-in prompt in the lower-right corner.

1. Select **Sign in to GitHub**.
2. Your browser opens to GitHub.
3. Authorize VS Code to use your GitHub account.
4. The browser returns you to VS Code. The sign-in indicator on the lower left of VS Code \(the account icon\) now shows your GitHub username.

If VS Code reports that your account doesn't have Copilot access, confirm your subscription at [github.com/settings/copilot](https://github.com/settings/copilot).

## Open the chat pane

Open the Copilot Chat pane in one of these ways:

- Select Ctrl+Alt+I \(Windows or Linux\) or Cmd+Alt+I \(macOS\).
- Select the **Chat** icon in the activity bar on the left side of VS Code.
- From the menu, select **View** > **Chat**.

The chat pane opens on the right side of the window with a text input on the bottom.

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

## You should see

The chat pane is open. The model picker on the top shows your chosen recommended model. The chat input on the bottom is ready for you to type into. You can confirm the kit's commands are loaded by typing:

```text
/
```

The chat pane shows a list of available slash commands. You should see kit commands like `/setup`, `/scan`, `/create`, `/flightcheck`, and others. If you don't see these commands, close and reopen the workspace and make sure you opened `solutions/ess-maker-skills`, not the top level of the repo.

## Next step

Continue with [Run your first command](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup).
