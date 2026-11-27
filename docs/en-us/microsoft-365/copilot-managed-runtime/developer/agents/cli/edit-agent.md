<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/edit-agent?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Edit your Copilot Studio agent \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Edit your Copilot Studio agent definition files after you [create](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide) or [open](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide) an agent. Use the tools and workflow you prefer to make changes, then deploy and evaluate them with the CLI. You can edit files manually or use an AI-assisted workflow with GitHub Copilot, Claude, or another coding assistant. The CLI synchronizes and deploys your files and starts evaluations that run in Copilot Studio.

Visual Studio Code is an optional IDE for browsing and editing the local workspace's files and folders. The [Copilot Studio Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=ms-CopilotStudio.vscode-copilotstudio) offers additional authoring features. Neither Visual Studio Code nor the extension is required to use the CLI.

Start with a registered project, a safe development target, and a saved source version.

## Understand the agent workspace files

View your agent's local registration details:

```powershell
msagent agent show --project 'C:\AgentProjects\VisitorGuide' --agent-name 'Visitor Guide'
```

List the agent's deployments:

```powershell
msagent deployment list --project 'C:\AgentProjects\VisitorGuide' --agent-name 'Visitor Guide'
```

Check the saved configuration for the `develop` deployment:

```powershell
msagent deployment show --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop
```

| Files or location | Purpose and review rule |
| --- | --- |
| Project `.config\\agent.config.json` | Personal registration, local IDs, and deployment targets. Don't commit it. |
| Workspace `settings.mcs.yml` | Agent settings and schema identity. In the default CLI scaffold, contains instruction segments under `configuration.agentSettings.instructions`. |
| Workspace `agent.sync.yaml` | Sync overlay; in the default CLI scaffold, contains the layout marker, not the instructions or identity. |
| Topics, `capabilities`, and `knowledge`, where present | Conversation behavior, tools, and knowledge declarations. Preserve component identities and cross-file references. |
| `workflows` and `infrastructure\\connections`, where present | Workflow content, metadata, and portable connection-reference declarations. Bind connections per environment. |
| Workspace `.mcs` | Local connection, baseline, and caches. Don't hand-edit, delete to bypass drift, or share it as portable source. |
| Declared component collections beside an agent | Shared content with potentially broader pull/deploy scope. Verify ownership and target connection. |

The display name is a label; the schema name identifies service content.

For schema-aware editing, see the [Copilot Studio Visual Studio Code extension](https://learn.microsoft.com/en-us/microsoft-copilot-studio/visual-studio-code-extension-install-configure).

## Make, deploy, and evaluate a focused change

1. Change only the relevant instruction segment, either manually or with a coding assistant. For the [Visitor Guide tutorial](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide), add a sentence to its static segment's `value`: "If you don't know a policy, ask the visitor to contact their host." Keep YAML indentation and all other settings intact.
2. Optionally, if you're using Git, use `git diff` to review your changes. Check file references, accidental deletion, secrets, intended collections, and generated files.
3. Deploy your changes to the cloud draft:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

4. Run the test set against the updated draft:

   ```powershell
   msagent agent eval run --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<development-environment-id>' `
     --testset VisitorSmokeV1 --watch
   ```

5. Read the returned run with agent eval show, inspect transcripts, and check draft content in Copilot Studio. If you don't have the tutorial's test set, [prepare one using the Visitor Guide CSV example](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide#evaluate-the-draft-and-improve-it) first.

You successfully edited the agent if the draft in Copilot Studio contains your changes and the evaluation results show that it responds as expected.

## Use a coding assistant with review boundaries

Give the assistant the project shape, approved schema guidance, and root help or deployment help. For example:

> Update only the visitor-policy instruction segment. Preserve schema identity and workflow metadata. Show the file diff. Don't sign in, deploy, publish, delete resources, or execute tests without approval.

Review generated content yourself. Keep credentials out of prompts and files. Require explicit approval for publication, destructive operations, and tests with real effects. If visual editing is required, open the deployed content in Copilot Studio and verify the round trip.

After approved publication, optional [live queries](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) and [playground exploration](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide) can uncover cases for regression tests.

## Next steps

[Prepare connections](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide)

[Review and promote the change](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide)
