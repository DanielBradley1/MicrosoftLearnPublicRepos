<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Collaborate on agent definitions through source control \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use Git source control to track changes to your Copilot Studio agent definitions and collaborate through code reviews on GitHub or Azure Repos. Use your preferred Git tools to manage commits, branches, pushes, and merge conflicts, alongside the CLI for agent development and deployment.

Start with a [created or cloned project](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide), Git installed and configured, and access to the team's GitHub or Azure Repos repository. Follow your team's branch policy. For general Git training, see [Introduction to Git](https://learn.microsoft.com/en-us/training/modules/intro-to-git/).

## Choose which files to include in source control

1. Locate the registered project with agent show:

   ```powershell
   msagent agent show --project 'C:\AgentProjects\VisitorGuide'
   ```

2. In the repository's `.gitignore`, add rules that cover nested agent workspaces:

   ```gitignore
   # Machine-specific registration and deployment targets.
   **/.config/agent.config.json
   # Workspace synchronization baselines, connections, and caches.
   **/.mcs/
   ```


   Don't ignore the entire `.config` directory if your project has other portable configuration. Keep credentials, token caches, private transcripts, generated evaluation reports, and personal configuration out of Git using project-specific rules.

3. Review portable inputs: `settings.mcs.yml`, `agent.sync.yaml`, topics \(if using the standard harness agent\), `capabilities`, `knowledge`, `workflows`, intended component collections, portable evaluation CSVs, and `infrastructure\connections\*.sync.yaml` declarations. Connection-reference definitions aren't credentials; review them for environment-specific data before sharing.
4. Use Git to review and save only intended files:

   ```powershell
   Set-Location 'C:\AgentProjects\VisitorGuide'
   git status --short
   git diff
   git add .gitignore '<agent-workspace-directory>' visitor-smoke.csv
   git diff --cached
   git commit -m "Add visitor guide definition and smoke cases"
   git push
   ```


   If creating a repository for the first time, initialize Git and configure the approved remote according to your hosting policy before this sequence. If private state is already tracked, an ignore rule doesn't untrack it; remove only those paths from Git's index and review the change with your team.

## Start working with an agent from your team's repository

1. Clone the team repository with Git:

   ```powershell
   git clone '<approved-repository-url>' 'C:\AgentProjects\VisitorGuide'
   Set-Location 'C:\AgentProjects\VisitorGuide'
   git status --short
   git diff
   ```

2. Read its setup instructions. Use authentication login and environment select for your authorized target, then agent init and agent show:

   ```powershell
   msagent auth login --account 'developer@contoso.com' --tenant '<tenant-id>' --cloud prod
   msagent env select '<development-environment-id>'
   msagent agent init --agent-name 'Visitor Guide' `
     --mcs-agent-source 'C:\AgentProjects\VisitorGuide'
   msagent agent show --project 'C:\AgentProjects\VisitorGuide'
   ```

3. Verify the registration and connection state. A checkout without local sync state is disconnected. Initialization doesn't restore previous deployments or reconnect a cloud agent by schema.

In the project README, explain how to set up the environment and who manages it. Keep each person's local connection settings and saved sign-in tokens out of the repository.

## Review and merge team changes

Review changes to behavior, references, workflow designer metadata, permissions, target assumptions, and evaluation cases, not just YAML syntax.

Use evaluation run against an approved test target and evaluation show with `--output '<report-path>'` to provide review evidence. Save reports with sensitive information removed in your team's approved storage location. Include the Git commit, the Copilot Studio agent and environment used, and the CLI version so teammates can understand and reproduce the results. Keep private conversation transcripts out of source control.

Resolve Git conflicts through Git and your editor. That doesn't resolve cloud synchronization conflicts. Use your team's pull-request and approval process before merging or deploying.

## Keep local files up to date with changes in Copilot Studio

Agree when makers can edit in Copilot Studio and which version is authoritative. You can start from a workspace connected to the intended cloud agent, or create a new agent on your local machine, commit its definition to source control, and then deploy it to Copilot Studio. Support for service principal \(SPN\) deployment through CI/CD workflows is on the roadmap.

To bring changes from Copilot Studio into a connected local workspace:

1. Preserve local definition changes in Git. Inspect `git status` and `git diff`, then commit or make an approved backup before pulling.
2. Confirm tracking with agent show. Agent pull uses the workspace connection's environment, not the active selection or a deployment label.
3. Use agent pull:

   ```powershell
   msagent agent pull --project 'C:\AgentProjects\ConnectedVisitorGuide' `
     --agent-name 'Visitor Guide'
   git diff
   git status --short
   ```

4. Review warnings and reported merge conflicts.
5. Resolve and commit accepted changes, obtain review, and only then [deploy the reviewed definition](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide).

Note

Before deploying, save any changes made in Copilot Studio that you want to keep. Development deployments include checks for some differences between local and cloud versions; test and production deployments use a different process. When you intentionally want to replace cloud content with your local version, use `agent deploy --overwrite`. To bring cloud changes into your local workspace, use `agent pull`, which uses the workspace's existing connection. Standalone workflows follow their own update process.

## Next steps

[Edit and verify behavior](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/edit-agent?view=o365-worldwide)

[Promote approved source](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide#promote-approved-source)
