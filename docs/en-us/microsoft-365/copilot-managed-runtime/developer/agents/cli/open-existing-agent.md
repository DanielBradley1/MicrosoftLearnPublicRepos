<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Open an existing Copilot Studio agent for local development \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Open an existing Copilot Studio agent for local development by cloning it from the cloud or registering a definition that's already on your machine. This article explains how to choose between a cloud clone, a Git clone, and local registration, and how to verify the result before deployment.

## Choose the correct starting path for your agent

| Starting point | Action | Result | Example commands \(abbreviated\) |
| --- | --- | --- | --- |
| Cloud agent exists. | Clone it into an empty workspace. | Downloaded content, cloud tracking, synchronization baseline, and a generated `develop` deployment. | `msagent agent create --mcs-clone-agent-id '<agent-id>' ...` |
| Definition exists in Git. | Clone the repository, then register the definition. | Local registration; a clean checkout without synchronization state is disconnected. | `git clone <repository-url>`, then `msagent agent init --mcs-agent-source '<workspace-path>' ...` |
| Definition exists locally, for example, from a previous working session. | Register its existing workspace. | Local registration; a valid existing workspace baseline can supply its connection. | `msagent agent init --mcs-agent-source '<workspace-path>' ...` |
| No agent exists. | [Create a new agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide). | Local definition; cloud creation happens at deployment. | `msagent agent create --agent-type MCSAgent ...` |

## Clone from Copilot Studio

1. Find the source environment with `environment list`, then discover its cloud agents with `agent list`:

   ```powershell
   msagent env list
   msagent agent list --environment-id '<source-environment-id>' --limit 50
   ```


   Check the environment and cloud ID, not only the display name.

2. Clone into a new, empty project using `agent create`:

   ```powershell
   msagent agent create --agent-type MCSAgent `
     --mcs-clone-agent-id '<source-cloud-agent-id>' `
     --mcs-clone-environment-id '<source-environment-id>' `
     --project 'C:\AgentProjects\ConnectedVisitorGuide'
   ```


   Alternatively, replace the ID selector with `--mcs-clone-agent-schemaname '<source-schema-name>'`; don't supply both selectors. Clone inherits the source name unless you supply `--agent-name`. It doesn't accept a new `--schema-name`.

3. Inspect `agent show`, `deployment list`, and `deployment show`:

   ```powershell
   msagent agent show --project 'C:\AgentProjects\ConnectedVisitorGuide'
   msagent deployment list --project 'C:\AgentProjects\ConnectedVisitorGuide'
   msagent deployment show --project 'C:\AgentProjects\ConnectedVisitorGuide' `
     --agent-name '<inherited-agent-name>' --deployment-name develop
   ```

4. Inspect the downloaded definition and generated `.mcs` tracking in the editor. Compare the reported source environment and agent with Copilot Studio.

Important

A same-environment cloud clone remains associated with the source cloud agent. Renaming its local display name doesn't create an independent cloud copy. Deployment can update that source.

Note

Support for forking an existing agent with the CLI is planned for a future release. Stay up to date through the [CLI GitHub repository](https://github.com/microsoft/AgentHosting.Cli).

## Register a definition already on disk

1. Inspect the definition's README and authoring shape. For an agent, the source directory must hold exactly one unregistered workspace with a readable schema identity.

   For example, a source directory for a CLI-scaffolded agent might look like this:

   ```text
   C:\AgentProjects\VisitorGuide\
     README.md
     visitor-guide\
       agent.sync.yaml
       settings.mcs.yml
   ```


   In this example, `visitor-guide` is the single agent workspace. Its `settings.mcs.yml` contains the agent's schema identity and settings. The README describes the project; the workspace folder name can vary.

2. With the intended environment selected, use `agent init`:

   ```powershell
   msagent agent init --agent-name 'Visitor Guide' `
     --mcs-agent-source 'C:\AgentProjects\VisitorGuide'
   ```

3. Inspect `agent show` and `deployment list`, using the project root that registration reports:

   ```powershell
   msagent agent show --project 'C:\AgentProjects\VisitorGuide'
   msagent deployment list --project 'C:\AgentProjects\VisitorGuide'
   ```

Registering the definition lets the CLI work with the files on your machine. It doesn't create or deploy an agent in Copilot Studio. Add the `.mcs` folder to your repository's `.gitignore` so that local connection information isn't committed. **Files cloned from Git usually don't include the `.mcs` connection information, so registration alone doesn't reconnect them to an existing cloud agent.**

To deploy to a new target, [create a deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide). To update an existing Copilot Studio agent, clone that agent into a separate empty workspace, then bring your changes from Git into that connected workspace. Keep connection information local, don't copy another developer's `.config` or `.mcs` folders.

## Next steps

[Edit the definition](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/edit-agent?view=o365-worldwide)

[Join the team source-control workflow](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide)
