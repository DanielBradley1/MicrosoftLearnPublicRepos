<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/create-agent?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Create an agent and complete your first development loop \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Create an agent and complete your first development loop when you don't have an existing Copilot Studio agent. In this tutorial, you create a local definition, edit its instructions, deploy and evaluate a cloud draft, publish it, and test it locally, so you can iterate on an agent before it reaches users.

## Prerequisites

- Install the CLI and [select your development account and environment](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/authenticate?view=o365-worldwide).
- Obtain permission to create and evaluate agents in a nonproduction environment.
- Use an empty project directory and your preferred editing tools or AI-assisted workflow. Optionally, use Visual Studio Code with the [Copilot Studio extension](https://marketplace.visualstudio.com/items?itemName=ms-CopilotStudio.vscode-copilotstudio). See [Install and configure the extension](https://learn.microsoft.com/en-us/microsoft-copilot-studio/visual-studio-code-extension-install-configure).

Examples use `C:\AgentProjects\VisitorGuide` as the project root and `Visitor Guide` as the local record name. Replace the environment placeholder with your actual development environment ID.

## Create the local definition

1. Use `agent create` with an explicit Copilot Studio type:

   ```powershell
   msagent agent create --agent-type MCSAgent `
     --agent-name 'Visitor Guide' --schema-name contoso_visitorGuide `
     --description 'Answers basic office visitor questions.' `
     --initial-prompt 'Help visitors prepare for their first office visit. Do not invent office policies.' `
     --environment-id '<development-environment-id>' `
     --project 'C:\AgentProjects\VisitorGuide'
   ```

2. Inspect `agent show`:

   ```powershell
   msagent agent show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide'
   ```

3. Open the generated workspace beneath the project root in your editor. Inspect `agent.sync.yaml` and `settings.mcs.yml`, where present, and the machine-specific `.config\agent.config.json` at the project root.

Your agent files are now saved on your machine and registered with the CLI. This local registration has its own ID, separate from the cloud agent ID. Nothing has been published yet.

The default scaffold shape is `CLI`. Use the latest harness for building new Copilot Studio agents. Choose `--mcs-agent-type Classic` only when you need that authoring shape. `--init-template default` is valid only with Classic. Cloned projects retain their source shape.

## Make one focused edit

In the default CLI scaffold, open `settings.mcs.yml`. Under `configuration.agentSettings.instructions.segments`, replace the existing static segment's `value` with the following text. Keep its indentation, schema identity, model settings, and other fields. This excerpt shows the segment, not a replacement for the entire file:

```yaml
- kind: StaticSegment
  value: |
    Help visitors prepare for their first office visit.
    Visitors should bring photo identification and check in at reception.
    If asked about parking, say that parking details must be confirmed with the host.
    Do not invent other office policies or take actions on the visitor's behalf.
```

This text is an example visitor policy. Review it before use. Your editor performs the edit.

## Deploy a development draft

1. Create the named local target with `deployment create`:

   ```powershell
   msagent deployment create --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop `
     --deployment-type dev --environment-id '<development-environment-id>'
   ```


   Creating a deployment record doesn't upload content or create an environment.

2. Upload the current files with `agent deploy`:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

3. Check the reported environment, cloud agent identity, uploaded components, and warnings. To check that the deployment worked, you can go to the Copilot Studio UX portal, select that environment, open that agent, and confirm the changed draft instructions.

Don't add `--publish` yet. A saved deployment record isn't proof that content, connections, and workflow activation all succeeded. This simple agent doesn't use connectors; if you add them, follow [connection readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide).

## Evaluate the draft and improve it

1. In your editor, save `C:\AgentProjects\VisitorGuide\visitor-smoke.csv`:

   ```csv
   conversationNumber,question,response
   1,What should I bring for my first visit?,Bring photo identification and check in at reception.
   1,Where should I check in?,Check in at reception.
   2,Is parking free?,Confirm parking details with your host.
   ```


   Reference answers guide evaluation grading in Copilot Studio; the CLI itself doesn't do the comparison.

2. Run the following command to upload your CSV as a test set named `VisitorSmokeV1` in Copilot Studio and evaluate it against your agent's draft. Specify your development environment explicitly:

   ```powershell
   msagent agent eval run --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<development-environment-id>' `
     --from-csv 'C:\AgentProjects\VisitorGuide\visitor-smoke.csv' `
     --name VisitorSmokeV1 --watch
   ```


   The default is the cloud draft. If your scenario requires an authenticated evaluation profile, get its approved Copilot Studio connection ID and supply `--connection`. The authenticated evaluation profile is specific to the evaluation feature set of Copilot Studio and is separate from the identity you use to sign in to the CLI.

3. Copy the returned run ID and inspect agent eval show:

   ```powershell
   msagent agent eval show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<development-environment-id>' `
     --run-id '<returned-run-id>' --transcript
   ```

4. Confirm the service run completed, review failed conversations and credits, and decide whether replies match the policy. If not, make one reviewed instruction change, deploy the draft again, and use agent eval run with `--testset VisitorSmokeV1 --watch`. Reusing `--from-csv` with the same name attempts another durable test-set creation and is refused unless you explicitly request replacement.

A watch timeout can leave the cloud run continuing.

## Publish the agent

After reviewing results and getting approval, use the agent deploy command with the `--publish` flag:

```powershell
msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop --publish
```

You can confirm that the agent was published successfully by using `msagent test ask` to check that its response reflects your updated instructions. If prompted, sign in or grant permission to chat with the agent:

```powershell
msagent test ask --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --query 'What should I bring for my first visit, and where should I check in?' --plain
```

Check that the response tells visitors to bring photo identification and check in at reception, as specified in the instructions you changed. Alternatively, open the agent in the [Copilot Studio UX portal](https://copilotstudio.microsoft.com) and check that its status is **Published**.

## Next steps

[Put your portable definition into source control](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/source-control?view=o365-worldwide)

[Do some additional testing](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide)

[Plan a deployment promotion](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide)
