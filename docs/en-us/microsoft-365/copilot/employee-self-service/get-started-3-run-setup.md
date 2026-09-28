<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-3-run-setup -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Run your first command

In this step, you run the `/setup` command. The kit connects to your Power Platform environment, finds your Employee Self-Service agent, and saves a local copy you can edit. The whole step takes about 10 minutes, most of it spent waiting for sign-in and extraction.

## Before you start

You need:

- The kit installed and open in VS Code \(or in a GitHub Codespace\). If the kit's not installed yet, pick an install path from the [Agent Developer Kit overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/developer-kit-overview#pick-your-install-path).
- GitHub Copilot Chat signed in. The one-shot installer and the Codespaces path sign in for you; if you installed manually, see [Step 2: Install GitHub Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/get-started-2-install-github-copilot).
- The **Environment Maker** role in a Power Platform environment that has an Employee Self-Service agent installed.
- An admin to enable the Microsoft GitHub Copilot client in your environment. If you aren't sure this prerequisite is done, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started#setup-says-no-tools-available).

## Run setup

In the Copilot Chat pane, type:

```text
/setup
```

Select **Enter**.

The kit responds and starts walking through setup. The first thing it does is ask you to sign in.

## Sign in

The kit shows a sign-in code and a link, similar to this example:

```text
To sign in, use a web browser to open the page
https://microsoft.com/devicelogin and enter the code ABCD-EFGH
to authenticate.
```

1. Copy the code.
2. Open the link in your browser.
3. Paste the code and select **Next**.
4. Sign in with the work account that has access to your Power Platform environment.
5. Approve the sign-in prompt.

The browser confirms when sign-in is complete. Return to VS Code.

## Pick which agent to extract

After you sign in, the kit looks for Employee Self-Service agents in your environment and lists what it finds:

```text
Found 2 Employee Self-Service agents in your environment:
  1. Employee Self-Service HR
  2. Employee Self-Service IT
Which one would you like to work on?
```

Reply with the number, or the name. You can come back and add the other one later by running `/setup` again.

If the kit lists only one agent, it asks you to confirm that's the one you want.

If the kit lists zero agents, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started#setup-cant-find-any-employee-self-service-agents).

## Wait for extraction

The kit downloads your agent's topics, workflows, variables, and settings into a local folder. This download takes a couple of minutes for a typical agent. You see progress messages in chat:

```text
Extracting Employee Self-Service HR...
  topics:    42 of 42
  workflows: 3 of 3
  variables: 18 of 18
  settings:  ok
Setup complete.
```

## You should see

In the Explorer pane on the left, a `workspace` folder now appears with your agent inside:

```text
ESS-MAKER-SKILLS
  .github
  .vscode
  scripts
  src
  workspace
    agents
      employee-self-service-hr
        agent.mcs.yml
        settings.mcs.yml
        connectionreferences.mcs.yml
        topics
        variables
        workflows
```

The chat pane also shows a summary message confirming setup is done and pointing you at next things to try.

## What happened

The kit:

- Saved a copy of your sign-in so you don't have to sign in again every time.
- Made a snapshot of your agent \(used later to figure out what you changed when you push back to Copilot Studio\).
- Built an index of every part of your agent so commands like `/scan` and `/create` can find their way around.

You didn't change anything in Copilot Studio. The agent in your environment is exactly as it was before. Everything you do now happens to your local copy until you explicitly push.

## Next step

You're set up. Continue with [What you can do now](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/what-you-can-do-now) for a menu of what to try next.

If something didn't go as expected, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).
