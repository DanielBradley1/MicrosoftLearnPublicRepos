<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Explore a published agent in the playground \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use the `msagent test playground` command to explore your published Copilot Studio agent in Microsoft 365 Agents Playground with supervised multi-turn conversations. The command launches the playground in a separate terminal window so you can test agent responses in a browser.

After the playground opens, complete any sign-in prompts and check that you can send a message to your agent.

## Choose the connection mode

The playground supports two APIs for connecting to an agent. **DirectEngine** connects directly to Copilot Studio and supports agents that require Microsoft sign-in. It's the default connection mode. **Direct Line** uses the Bot Framework Direct Line API and a connection credential. In this playground integration, it supports agents configured with no authentication.

| Mode | Use it when | Authentication and targeting |
| --- | --- | --- |
| DirectEngine, the default | The published agent requires Microsoft sign-in. | CLI discovers the endpoint for the selected deployment; the playground owns its own sign-in. |
| Direct Line | A separately approved compatible agent is already configured for no authentication and global public-cloud Direct Line. | Native masked credential entry determines the agent; local project and deployment selectors aren't used. |

This integration doesn't support regional, custom, or sovereign Direct Line endpoints, OAuth-card sign-in, file upload, saved connections, or headless interaction.

Note

Playground conversations use the cloud service and your published agent. They can consume credits, and the agent's tools and workflows can make changes to connected services that can't always be undone. Use appropriate test data and connections.

## Set up your machine

Install [Node.js](https://nodejs.org/en/download) version 22.17.1 or newer. Choose a supported LTS release; the installer also includes npm.

After installation, open a new terminal and check that both are available:

```powershell
node --version
npm --version
```

Install Microsoft 365 Agents Playground:

```powershell
npm install -g @microsoft/m365agentsplayground@latest
```

Run the playground from a terminal on your local machine so you can complete sign-in and use the browser experience.

## Launch the playground

1. Verify the intended registered agent and deployment. The playground uses Direct Engine by default unless you select a different connection mode. Launch it with `msagent test playground`:

   ```powershell
   msagent test playground --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

2. Check the agent, deployment, and playground version shown in your terminal. The CLI uses your signed-in account to find the agent's endpoint, then opens the playground in a new terminal. Complete any browser or device-code sign-in prompts by using an account with access to the agent. The playground signs in separately, so it might prompt even if you used `--non-interactive`.
3. In the playground browser, wait for **Connected**, then send a question such as "Where should a visitor check in?" and a follow-up question.

## Launch the playground with Direct Line

1. In Copilot Studio, check that your agent is published and configured for **No authentication**. This option supports global public-cloud Direct Line connections.
2. Run:

   ```powershell
   msagent test playground --target directline
   ```

3. In the new terminal, enter the HTTPS token endpoint from **Channels** > **Mobile app**, or the Direct Line secret from **Settings** > **Security** > **Web channel security**. Your input is hidden.
4. In the playground browser, wait for **Connected**, check that you're connected to the intended agent, then send a question and a follow-up.

Never put Direct Line credentials in chat, commands, environment variables, configuration, screenshots, or logs. Press Enter, Escape, or Ctrl+C to cancel credential setup. The CLI doesn't retrieve, save, or log the credential.

Direct Line rejects `--non-interactive`, including with `--install-playground`, and rejects all DirectEngine target selectors, including `--project`.
