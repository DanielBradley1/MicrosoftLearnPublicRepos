<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Deploy and promote a Copilot Studio agent \(preview\)

\[This article is prerelease documentation and is subject to change.\]

To deploy and promote a Copilot Studio agent with the CLI, use a **deployment**: a named target that tells the CLI where to deploy your agent. It identifies a Power Platform environment and a stage, such as development, test, or production. Creating a deployment saves that target locally. Running `msagent agent deploy` uploads your agent to it.

| Step | Command example \(abbreviated\) | What it does |
| --- | --- | --- |
| Create a target. | `msagent deployment create --deployment-name develop ...` | Saves the environment and stage for deployment. |
| Deploy a draft. | `msagent agent deploy --deployment-name develop ...` | Uploads your agent definition to Copilot Studio. |
| Test the draft. | `msagent agent eval run ...` | Evaluates the draft before publication. |
| Publish the agent. | `msagent agent deploy --deployment-name develop --publish ...` | Deploys and publishes the agent for users. |
| Promote to another environment. | `msagent agent deploy --deployment-name staging ...` | Deploys the reviewed definition to a separately configured target. |

## Prerequisites

- A registered [agent project](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide) and [authorized account](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide).
- Environment IDs and create/edit permissions for each intended target.
- Reviewed source, target-specific connections, and a safe evaluation strategy.
- Team-defined release gates, approvers, and a budget for service execution.

Power Platform administrators provision environments and policies outside the CLI. See [environment strategy](https://learn.microsoft.com/en-us/power-platform/admin/environments-overview).

## Create deployment targets for each environment

1. Use `environment list` to verify accessible environments and `agent show` to inspect the local project.
2. Create named targets with `deployment create`:

   **For development:**

   ```powershell
   msagent deployment create --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop `
     --deployment-type dev --environment-id '<development-environment-id>'
   ```


   **For test:**


   ```powershell
   msagent deployment create --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name release-test `
     --deployment-type test --environment-id '<test-environment-id>'
   ```


   **For production:**


   ```powershell
   msagent deployment create --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name production `
     --deployment-type prod --environment-id '<production-environment-id>'
   ```


   Run only the records you need. Cloud cloning already creates `develop`. Test and production require explicit environment IDs. Names are 4–42 permitted letters, digits, hyphens, or underscores.

3. List your agent's deployments:

   ```powershell
   msagent deployment list --project 'C:\AgentProjects\VisitorGuide' --agent-name 'Visitor Guide'
   ```

4. Check the saved configuration for the `develop` deployment:

   ```powershell
   msagent deployment show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

Creating records doesn't create environments or upload an agent. The MCS `deployment update` operation can rename a record with `--new-name`; it doesn't change its stage or environment. Create a deliberate new target instead of assuming renaming retargets it.

## Deploy your agent

1. Check the project, agent, and target shown by local inspection. Review the schema identity and what first deployment will create or adopt. A same-environment clone can update its source agent.
2. Use agent deploy:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

3. Read the environment, cloud agent ID, action, pushed component counts, and warnings. In Copilot Studio, choose that environment and open that exact agent to verify draft content.
4. Inspect connection list, resolve bindings using connection update, and independently verify workflow activation. See [connection readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide).

Specify a deployment ID or name. Deployment commands don't automatically use your currently selected environment.

First deployment creates or adopts a cloud agent and can reconnect the workspace to the target. Read-only managed agents are rejected. Adoption of an existing agent must be verifiable as your project's agent or explicitly acknowledged with overwrite. Don't force adoption merely because a display name matches.

## Publish your agent

When you're happy with your draft and have any required approvals, use agent deploy with the `--publish` flag to upload your latest changes and publish the agent:

```powershell
msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop --publish
```

You can check the publication status in Copilot Studio. Confirm that your intended users have access and that the agent's connections are configured.

To try the published agent, [ask a question from the terminal](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) or [open it in the playground](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide), selecting the same deployment.

## Move your agent from development to test and production

Use the same reviewed agent definition as you move between environments. Configure connections separately for each environment.

1. If you're using Git, select the commit or release tag you want to deploy:

   ```powershell
   Set-Location 'C:\AgentProjects\VisitorGuide'
   git checkout '<approved-commit-or-release-tag>'
   ```


   Save or commit any local changes before switching versions.

2. Check that the `release-test` deployment points to your test environment, then deploy the agent:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name release-test
   ```

3. Evaluate the agent in your test environment:

   ```powershell
   msagent agent eval run --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
     --from-csv 'C:\AgentProjects\VisitorGuide\visitor-smoke.csv' `
     --name ReleaseSmokeV1 --watch
   ```


   Test sets belong to a specific agent and environment. If you already created the set, use `--testset` with its name or ID instead of `--from-csv` and `--name`. If your evaluation needs an authenticated profile, include its connection ID with `--connection`. See [Evaluate agent behavior](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide) for test-set management and result interpretation.

4. Review the evaluation results and check that the agent's tools and connections work as expected. Record any required release approval in your team's usual system.
5. Check that the `production` deployment points to the correct environment and configure its connections. Deploy the same reviewed definition:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name production
   ```

6. When you're ready to make the changes available to users, publish the production agent:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name production --publish
   ```


   Confirm publication and user access, then test a representative question in Copilot Studio, from the terminal, or in the playground.

Keep a release record with the source version, CLI version, target agent and environment, and test results so your team can track what you deployed.

## Fix a failed deployment or restore an earlier version

If a deployment fails, some changes might already be saved. Check the command's output and the agent in Copilot Studio to see what completed before trying again.

1. If a connection needs attention, use `connection list` to check it and `connection update` to fix its binding.
2. To restore an earlier agent definition, select that version in Git or restore your saved files. Then use `agent deploy` with the intended deployment. Add `--publish` when you're ready to make that version available to users.
3. Test the agent and check its connections, publication status, and user access.

Redeploying an earlier definition restores the agent's content, but it doesn't undo actions the agent or its workflows already performed, such as changing data in another service. Handle those changes separately in the affected service.

If someone edited the agent in Copilot Studio, [bring those changes into your local workspace and review them](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide#keep-local-files-up-to-date-with-changes-in-copilot-studio) before deploying. Use `--overwrite` only when you intend to replace the cloud content with your local version. Development deployments check for some conflicting changes; test and production deployments don't include the same checks.

Note

Before deploying or using `--overwrite`, commit your reviewed agent files and push them to your team's source-control repository, or save an approved backup. Include any cloud changes you want to keep so you have a saved version to compare or restore later.
