<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/standalone-workflows?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Manage a standalone workflow with the CLI \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use the CLI to manage a standalone workflow \(`MCSWorkflow`\) when a cloud workflow should have an independent lifecycle rather than being an agent-linked component. The CLI registers and synchronizes workflow files. Copilot Studio supplies workflow design, execution tests, and run history.

Before you start, [install the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli) and [sign in to your environment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide). You need permission to create and edit workflows, a local folder for your files, and access to any connectors the workflow uses. To clone an existing workflow, you also need its workflow ID \(GUID\) and access to its environment. Run `msagent agent create --help` to see the options for creating or cloning a workflow.

## Create, clone, or register a workflow

Choose the option that matches whether you're starting a new workflow, working with one in the cloud, or using files already on your machine.

### Create a new workflow

Use `msagent agent create` with `--agent-type MCSWorkflow` to create workflow files on your machine:

```powershell
msagent agent create --agent-type MCSWorkflow --agent-name 'Visitor notification' `
  --environment-id '<development-environment-id>' `
  --project 'C:\AgentProjects\VisitorWorkflow'
```

The command creates the local files and registers the workflow with the CLI. It doesn't create a workflow in Copilot Studio until you deploy it. You don't need to provide an agent prompt or description.

### Clone an existing workflow

First, find the workflow you want to work with:

```powershell
msagent agent list --agent-type MCSWorkflow `
  --environment-id '<source-environment-id>' --filter Visitor --limit 50
```

The list includes unmanaged cloud workflows, including those used by agents. The list doesn't include workflows installed through managed solutions.

Copy the workflow's ID, and then clone it into a separate, empty folder:

```powershell
msagent agent create --agent-type MCSWorkflow `
  --mcs-clone-workflow-id '<source-workflow-guid>' `
  --mcs-clone-environment-id '<source-environment-id>' `
  --project 'C:\AgentProjects\ConnectedVisitorWorkflow'
```

Cloning downloads the workflow files, connects your local workspace to the existing cloud workflow, and creates a deployment named `develop`. It doesn't create a second workflow in the cloud.

### Register existing workflow files

If you already have workflow files on your machine, for example, from a Git checkout, use `msagent agent init` to register them with the CLI:

```powershell
msagent agent init --agent-type MCSWorkflow --agent-name 'Visitor notification' `
  --mcs-workflow-source 'C:\AgentProjects\VisitorWorkflow\<workflow-workspace-directory>'
```

The source folder must contain exactly one workflow that the CLI can read. The command uses your currently selected environment, registers the workflow locally, and creates its connection-reference declaration. It doesn't create a deployment or upload the workflow.

Use the project directory shown in the command's output when running subsequent commands.

## Review your workflow files

View the workflow's details with `msagent agent show`:

```powershell
msagent agent show --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification'
```

Open the workflow files in your editor and review the actions, inputs, connection references, and metadata. If you also edit the workflow in the visual designer, keep the information that connects the diagram to its actions, including node IDs, connections between nodes, and action mappings.

Use the supported workflow format when editing actions. An agent definition isn't a template for workflow action JSON.

If you're using Git, commit the workflow files you want to share with your team. Keep local configuration, such as `.config\agent.config.json` and nested `.mcs` folders, credentials, and private generated files out of source control. See the [source-control guide](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide) for details.

## Configure and deploy your workflow

Choose the deployment environment, configure its connections, and upload your workflow files.

### Choose the deployment environment

For a new or registered workflow, create a deployment that points to your development environment:

```powershell
msagent deployment create --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop `
  --deployment-type dev --environment-id '<development-environment-id>'
```

If you cloned the workflow, a deployment named `develop` already exists. You can use that deployment without creating another one.

Check the deployment's details before continuing:

```powershell
msagent deployment show --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop
```

### Configure connections

List the workflow's connection references:

```powershell
msagent deployment connection list --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop --by-reference
```

Bind each reference to the connection you want the workflow to use:

```powershell
msagent deployment connection update --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop `
  --connection-reference '<workflow-reference-logical-name>' `
  --connection-id '<approved-connection-id>'
```

For standalone workflows, you can configure these bindings before the first deployment. Create the local deployment record first so the CLI knows which environment to use.

Check connection bindings and workflow activation separately. If activation fails, the connection binding might still be saved. See [When to bind connections](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide#when-to-bind-connections) for more information.

### Deploy the workflow

Upload your workflow files to the selected environment:

```powershell
msagent agent deploy --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop
```

Review the deployment messages and check the workflow's status in Copilot Studio. The CLI attempts to activate the workflow when its local configuration requests activation or you supply `--publish`. If missing connection bindings leave it in draft, configure those bindings and deploy again.

For a standalone workflow, `--publish` means activate the workflow, not publish an agent.

Note

Deploying replaces the cloud workflow identified by the workflow ID. Unlike agent development deployments, workflow deployments don't check for conflicting cloud changes before replacing content. Adding `--overwrite` doesn't change this behavior. The `--schema-name` option isn't supported for workflow deployments.

For test and production, create a deployment for each environment and configure its connections separately. Check the workflow ID before deploying: a different deployment name doesn't create a separate workflow by itself.

## Pull the latest workflow changes from the cloud

Before pulling changes, save your local workflow files in Git or make a backup. Check that the selected deployment points to the environment and workflow you want to download.

Pull the latest files:

```powershell
msagent agent pull --project 'C:\AgentProjects\VisitorWorkflow' `
  --agent-name 'Visitor notification' --deployment-name develop
```

Review the changes with `git diff` and check any messages from the CLI.

Pulling a workflow replaces local files rather than merging changes. If you have local changes that you didn't deploy, the CLI asks you to resolve them before continuing. Use `--overwrite` only when you want to replace those changes with the cloud version, and save a copy first.

Unlike [pulling an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide#keep-local-files-up-to-date-with-changes-in-copilot-studio), pulling a standalone workflow uses the selected deployment to find the cloud workflow. It can also restore workflow files that are missing locally.

## Test your workflow

Open the deployed workflow in the Power Automate maker portal and select the correct environment. Check its connections and confirm it's turned on, then run a test using suitable test data.

Review the run history to check each action's inputs, outputs, and any errors. A successful deployment confirms that you uploaded the files; testing confirms that the workflow behaves as expected.

Manage access through the workflow's sharing settings. Agent sharing and agent evaluations don't apply to standalone workflows.

## Delete a standalone workflow

Use `msagent agent delete` with an explicit deployment name or ID to select the cloud workflow to delete. This command also removes the workflow's local CLI registration and all its deployment records, but it leaves your source files on disk. It doesn't automatically delete copies in other environments.

By default, `msagent deployment delete` removes only the local deployment record. `msagent deployment delete` can't delete a cloud workflow. To delete the workflow itself, use `msagent agent delete` with the deployment name or ID.

Before deleting, check the selected environment and workflow ID, and whether other workflows still use its connections. Use `--help` on either command to review the available options.

If deployment or connection setup needs further investigation, see [Troubleshooting Guide](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/troubleshoot?view=o365-worldwide).
