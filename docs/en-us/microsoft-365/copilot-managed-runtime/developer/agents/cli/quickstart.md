<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/quickstart?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Quickstart: Create and deploy a Copilot Studio agent \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Create a Copilot Studio agent from local files and deploy it to a development environment with the Copilot Studio CLI \(`msagent`\). In this quickstart, you sign in, scaffold an incident management agent, edit its instructions, and deploy it. You can then publish and test the agent and use evaluations to assess its responses.

## Prerequisites

- [Install the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli).
- Use a work or school account with Copilot Studio access and permission to create, publish, and use agents in a nonproduction Power Platform environment.
- Confirm licensing, available Copilot Credits, and cost controls before running an agent. If you add connector tools, obtain approved connections and permission to use them.

The examples use PowerShell and `C:\AgentProjects\IncidentManagement` as the project directory. Replace `<development-environment-id>` with the environment ID you select in the next section.

## Sign in and select an environment

1. Sign in by using `msagent auth login` and complete the sign-in prompt:

   ```powershell
   msagent auth login
   ```

2. Find your development environment by using `msagent env list`:

   ```powershell
   msagent env list
   ```

3. Copy the environment ID and select it by using `msagent env select`:

   ```powershell
   msagent env select '<development-environment-id>'
   ```

For more information, see [Sign in and choose your Copilot Studio environment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide). Selecting an environment doesn't retarget existing projects or deployments.

## Create a local agent

Use `msagent agent create` to scaffold an agent in a new project directory:

```powershell
msagent agent create --agent-type MCSAgent `
  --agent-name 'Incident Management Agent' `
  --description 'Helps customers describe and triage issues.' `
  --initial-prompt 'Help customers describe an issue and prepare an initial support ticket. Do not claim to submit tickets or access customer systems.' `
  --environment-id '<development-environment-id>' `
  --project 'C:\AgentProjects\IncidentManagement' --json
```

The command creates the local project, a managed-agent record, and the agent definition files. Nothing is deployed to Copilot Studio yet. Note the generated workspace path in the result; it isn't necessarily the same as the agent's display name.

For more information about scaffold options and generated files, see [Create an agent and complete your first development loop](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide).

## Edit the agent instructions

Use the tools and workflow you prefer to edit the generated workspace. You can edit files manually or use an AI-assisted workflow with GitHub Copilot, Claude, or another coding assistant. No specific editor or IDE is required.

Visual Studio Code is an optional IDE for browsing and editing the local workspace's files and folders. The [Copilot Studio Visual Studio Code extension](https://learn.microsoft.com/en-us/microsoft-copilot-studio/visual-studio-code-extension-install-configure) offers additional authoring features, but neither Visual Studio Code nor the extension is required. You can install the extension from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-CopilotStudio.vscode-copilotstudio).

For the default CLI scaffold, update the existing static segment's `value` under `configuration.agentSettings.instructions.segments` in `settings.mcs.yml` to match the following example. Make the change yourself or ask your coding assistant to make it, keeping the indentation and surrounding configuration intact:

```yaml
- kind: StaticSegment
  value: |
    Help customers prepare an initial support ticket.
    Ask for a short issue summary, when the issue started, and its business impact.
    Remind customers not to share passwords, secrets, or sensitive customer data.
    Summarize the issue for review. Do not claim to submit a ticket or access customer systems.
```

Save and review the changes before deployment, whether you make them manually or with a coding assistant.

For more information, see [Editing your Copilot Studio agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/edit-agent?view=o365-worldwide).

## Deploy a development draft

1. Register a local deployment target with `msagent deployment create`:

   ```powershell
   msagent deployment create --project 'C:\AgentProjects\IncidentManagement' `
     --agent-name 'Incident Management Agent' --deployment-name develop `
     --deployment-type dev --environment-id '<development-environment-id>'
   ```


   This step saves the target locally. It doesn't upload files or create a cloud agent.

2. Upload your definition with `msagent agent deploy`:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\IncidentManagement' `
     --agent-name 'Incident Management Agent' --deployment-name develop --json
   ```


   Allow about 5 to 10 seconds for deployment to complete. When you run the command interactively without `--json`, a spinner or percentage indicator shows deployment progress.

3. Review the reported environment, cloud agent identity, and warnings. Optionally open [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com), select the same environment, and verify that the agent's draft contains your instructions.

For more information about deployment targets and promotion, see [Deploy and promote an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide).

### Configure connections if you add tools

This example doesn't require connectors. If you add a connector tool or workflow, its connection reference must bind to an authorized connection in the target environment. A connector describes the service API; a connection holds authorization; a connection reference connects your definition to that connection.

After the cloud agent exists, use `msagent deployment connection update` to bind an existing reference:

```powershell
msagent deployment connection update --project 'C:\AgentProjects\IncidentManagement' `
  --agent-name 'Incident Management Agent' --deployment-name develop `
  --connection-reference '<logical-reference-name>' `
  --connection-id '<approved-connection-id>' --json
```

Replace both placeholders with approved values for your tool. Connection changes can immediately enable workflows.

For more information about declaring references, authorizing connections, and recovering an incomplete deployment, see [Working with connections and the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide).

## Publish the Copilot Studio agent

Before publishing, you can [evaluate the draft](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide) to assess its responses. For a complete CSV-based walkthrough, see [Evaluate the draft and improve it](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide#evaluate-the-draft-and-improve-it).

Review the draft and confirm you are happy with the changes to make available to its intended users. Use `msagent agent deploy` with `--publish`:

```powershell
msagent agent deploy --project 'C:\AgentProjects\IncidentManagement' `
  --agent-name 'Incident Management Agent' --deployment-name develop --publish --json
```

Verify publication, dependencies, and intended user access in Copilot Studio.

## Test the published agent

You can test the agent in Copilot Studio, query it from your terminal, or use the local playground. Terminal queries and the playground connect to your published agent in Copilot Studio.

Note

Live queries can consume credits, execute tools and workflows, and change real data. Use safe test inputs and a development environment.

The CLI lets you authenticate from your local machine to the Copilot Studio agent you're working on, provided you have or have been granted permission to access it. Follow the [sign-in steps](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide#sign-in-and-ask-your-agent-a-question), then send a query with `msagent test ask`:

```powershell
msagent test ask --project 'C:\AgentProjects\IncidentManagement' `
  --agent-name 'Incident Management Agent' --deployment-name develop `
  --query 'What information should I include in a support ticket?' --plain
```

For a local conversation UI, use `msagent test playground` after signing in:

```powershell
msagent test playground --project 'C:\AgentProjects\IncidentManagement' `
  --agent-name 'Incident Management Agent' --deployment-name develop
```

For more information, see [Ask an agent questions from the terminal](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) and [Explore a published agent in the playground](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide).

## Next steps

[Put agent definitions in source control](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide)
