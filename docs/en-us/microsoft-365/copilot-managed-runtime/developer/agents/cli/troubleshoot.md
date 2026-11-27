<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/troubleshoot?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Diagnose CLI problems and resume safely \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use this guide to diagnose CLI problems, identify the failed stage, and preserve work before recovery. Start with the command's error message, error code, and remediation guidance. An error code is a condition identifier. If the problem persists after following the relevant troubleshooting steps, open an issue in the [repo](https://github.com/microsoft/AgentHosting.Cli/issues). To help us understand what's happening, share your CLI version from `msagent --version`, the command you ran, your error code and error responses, and context about what you're experiencing. Don't share sensitive information.

Note

Failed deployment, connection, or test commands can leave cloud effects. Don't assume rollback, delete synchronization state, broadly overwrite content, or replay a potentially mutating request as the first troubleshooting action.

## General CLI troubleshooting recommendations

1. Record your installed CLI version and check the available commands:

   ```powershell
   msagent --version
   msagent --help
   ```


   `msagent --version` displays the installed CLI version. `msagent --help` lists commands and global options; it doesn't diagnose errors. Add `--help` to a specific command, such as `msagent agent deploy --help`, to see its syntax and available options without running the operation.

2. Save your local agent files in Git or an approved backup before pulling cloud changes, redeploying, or cleaning up files. This step ensures you have a copy to compare or recover if an operation changes your local work.
3. Check the current agent and connection configuration in Copilot Studio before retrying. Someone on your team might have changed the cloud version since your last synchronization, or the failed command might have uploaded some changes. Compare the cloud version with your local files before pulling or redeploying.
4. Add `--debug` to the command you're investigating to request additional diagnostic output. It doesn't make the command a dry run: deployment, connection, and test commands can still change cloud data. Debug output varies by command and can change where output is written, so don't assume it preserves the normal JSON output format. Review the diagnostics and remove sensitive information before sharing them in an issue.

## Find the right recovery steps

| Problem | Start here |
| --- | --- |
| The CLI isn't found, won't install, or reports a missing runtime. | [Installation and runtime](#the-cli-isnt-found-wont-install-or-reports-a-missing-runtime). |
| Sign-in fails or an environment isn't available. | [Identity and access](#sign-in-fails-or-an-environment-isnt-available). |
| Registration, local files, or cloud tracking don't match expectations. | [Workspace and synchronization](#registration-local-files-or-cloud-tracking-dont-match-expectations). |
| Deployment, connection binding, workflow activation, or publication is incomplete. | [Deployment and dependencies](#deployment-connection-binding-workflow-activation-or-publication-is-incomplete). |
| Evaluation input fails, a run times out, or results are unexpected. | [Evaluations](#evaluation-input-fails-a-run-times-out-or-results-are-unexpected). |
| Terminal queries or Playground can't connect or need setup. | [Optional live testing and playground](#terminal-queries-or-playground-cant-connect-or-need-setup). |

## The CLI isn't found, won't install, or reports a missing runtime.

| Symptom | Safe recovery |
| --- | --- |
| Tool isn't found. | Open a new terminal, check `dotnet tool list --global`, and verify that the global .NET tool directory is on `PATH`. The default is `%USERPROFILE%\.dotnet\\tools` on Windows and `$HOME/.dotnet/tools` on macOS. |
| Wrong version. | Check `msagent --version` and [update the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli). |
| Missing shared framework. | Run `dotnet --list-runtimes` to check what's installed. The CLI requires both .NET 10 and ASP.NET Core 10 runtimes for the appropriate architecture. Install the [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0), which includes both, then open a new terminal and try again. |
| Package source failure. | Verify network access and your organization's NuGet source configuration. Use the [documented package source and installation command](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli); don't add unrelated sources. |
| CLI isn't installed. | Ensure the CLI is installed. Get the [Microsoft.Agents.Hosting.Cli package on NuGet](https://www.nuget.org/packages/Microsoft.Agents.Hosting.Cli) and follow [Install the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli). |
| `dotnet` isn't found or no compatible SDK is installed. | Install the [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0), open a new terminal, and run `dotnet --list-sdks` to confirm installation before retrying the CLI installation. |

The installation commands require the .NET 10 SDK. See [Install the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli) for the package, commands, and prerequisites.

## Sign-in fails or an environment isn't available

1. Inspect authentication status, which doesn't contact the identity service:

   ```powershell
   msagent auth status
   ```

2. If the account or ring is wrong, use `msagent auth switch` for a stored account or `msagent auth login` for authorized interactive sign-in. Then reselect the intended environment.
3. Use `msagent env list` and `msagent env select`:

   ```powershell
   msagent env list
   msagent env select '<intended-environment-id>'
   ```

4. For an absent environment or insufficient permissions, have your administrator verify tenant, environment access, service availability, and policy.

## Registration, local files, or cloud tracking don't match expectations

Use `msagent agent show` and `msagent deployment list`:

```powershell
msagent agent show --project 'C:\AgentProjects\VisitorGuide'
msagent deployment list --project 'C:\AgentProjects\VisitorGuide'
```

| Symptom | Safe recovery |
| --- | --- |
| Project or configuration not found. | Verify the project root and explicit path. For portable existing files without registration, [register the existing definition](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide#register-a-definition-already-on-disk) with `msagent agent init`. |
| Machine-local configuration invalid or unsupported. | Preserve portable files and a trusted local backup. Recover valid personal state or reconstruct registration through supported commands; don't restore another developer's committed bindings. |
| Multiple records or workspaces. | Supply the exact local agent selector; resolve multiple unregistered workspaces before initialization. |
| Local and remote IDs confused. | Use local record IDs for local operations. Check `msagent agent show` and the command's `--help`; don't assume a local record ID is the cloud agent ID. [Evaluations](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide#choose-the-agent-to-evaluate) also need the correct cloud copy and environment. |
| Clean checkout is disconnected. | Registration doesn't reconstruct cloud tracking. Use [cloud clone into an empty workspace](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/open-existing-agent?view=o365-worldwide#clone-from-copilot-studio) and compare reviewed portable files. |
| Workspace points to another cloud agent. | Stop and verify the source connection and intended target. Don't rename identity or copy caches to force a match. |
| Portal drift or conflicting edits. | Preserve local source, use `msagent agent pull` from the verified connection, and review warnings and conflicts before deployment. |

`msagent agent pull` uses its workspace connection, not the active environment. Development drift checks don't protect every component or test/production deploy. Standalone workflow pull replaces rather than merges and has different overwrite semantics.

## Deployment, connection binding, workflow activation, or publication is incomplete.

1. Check your deployment configuration with `msagent deployment show`:

   ```powershell
   msagent deployment show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```


   This command shows the saved local configuration. In Copilot Studio, check that the environment and agent match the deployment you want to update.

2. Select the appropriate deployment by name or ID. Changing the active environment with `msagent env select` doesn't change an existing deployment's target environment.
3. If deployment didn't finish, review the uploaded content in Copilot Studio and the command's messages before retrying. Some changes might already be uploaded or recorded in the local deployment configuration.
4. Check for missing connection bindings with `msagent deployment connection list`:

   ```powershell
   msagent deployment connection list --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop --by-reference --json
   ```

5. Check the connection owner, connector, reference name, and any required consent. Use `msagent deployment connection update` to bind the affected reference to the appropriate connection ID. If the reference already exists, update it rather than adding it again.
6. Check workflow activation in Copilot Studio as well as connection bindings. You can bind standalone workflow references before the first deployment. For agents, the target cloud agent must exist before the CLI can discover its references. See [when to bind connections](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide#when-to-bind-connections).
7. If the agent wasn't published, resolve any reported content or workflow activation issues, then run `msagent agent deploy` with `--publish` when you're ready to publish. Confirm the publication status and intended users' access in Copilot Studio.

Connection bindings and workflow readiness are separate checks, so review both even when the command completes successfully. Connection setup can still require consent or input when you use non-interactive mode. For more information, see [connections](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide) and [deployment recovery](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide#fix-a-failed-deployment-or-restore-an-earlier-version).

## Evaluation input fails, a run times out, or results are unexpected.

1. If your CSV isn't accepted, check that it has the required headers, whole-number conversation IDs, and a question in every row. Check the supported limits in [CSV format](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide#csv-format).
2. Find your evaluation run and review its status and conversation transcripts with `msagent agent eval list` and `msagent agent eval show`:

   ```powershell
   msagent agent eval list --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>'
   msagent agent eval show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
     --run-id '<run-id>' --transcript
   ```

3. If watching a run times out, check the existing run's status before starting another. The evaluation can continue in the cloud after the CLI stops waiting, and a report file might not be created yet. To stop a run that's still in progress, use `msagent agent eval cancel`.
4. If results or costs differ from what you expected, review the full transcripts, the authentication profile used for the evaluation, the grader results, and consumption in the Power Platform admin center. A completed run can still contain failed test cases. Use these details to decide what to change before running the evaluation again.

See [Review evaluation results](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide#review-evaluation-results).

## Terminal queries or Playground can't connect or need setup

Use the `help` command to check the available testing options:

```powershell
msagent test ask --help
msagent test playground --help
```

| Symptom | Safe recovery |
| --- | --- |
| A command isn't recognized. | Check `msagent --version` and [update the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/?view=o365-worldwide#install-the-cli), then inspect its help. |
| Sign-in or invocation consent is required. | Follow [sign-in and query setup](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide#sign-in-and-ask-your-agent-a-question), and ask your administrator to verify invocation permissions if access is refused. |
| Agent isn't published. | Publish the agent in Copilot Studio or use `msagent agent deploy` with `--publish` for the intended deployment, then try again. |
| Agent isn't accessible. | Ask the agent's owner to share the agent with you. |
| Deployment-selection failure. | Pass an explicit deployment; a single non-default record isn't selected automatically. |
| Endpoint discovery failure. | Check the agent's schema name, environment, tenant, access permissions, and service availability. |
| Playground package won't install or launch. | Review the package installation error, check network access and package registry settings, and update or reinstall the Playground package as described in [Playground setup](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide). |
| New terminal requests sign-in. | Playground can ask you to sign in separately from the CLI. Complete the sign-in steps in the Playground terminal. |
| Direct Line rejects selectors or non-interactive mode. | When using Direct Line, follow the interactive setup for a published agent configured with no authentication. Enter credentials only when prompted in the masked input field. |
| Process launched but no conversation. | Wait for **Connected** and the message input to become available. Check the Playground terminal for messages or sign-in steps to complete. |
| Query interrupted or session failed. | Check whether the agent completed any actions before retrying. To stop Playground, press Ctrl+C in the terminal where it's running. Closing the CLI terminal doesn't close Playground. |

See [terminal testing](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide) and [Playground setup](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/playground?view=o365-worldwide).
