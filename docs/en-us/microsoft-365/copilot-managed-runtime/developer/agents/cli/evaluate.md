<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/evaluate?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Evaluate agent behavior \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Evaluate your Copilot Studio agent's behavior with test sets that run asynchronously in Copilot Studio, so you get repeatable evidence before you release changes. Runs appear in the maker portal UX beside portal-started runs. The CLI starts and manages these runs, but execution and grading happen in Copilot Studio, not locally. Use `msagent agent eval --help` or add `--help` to a subcommand to inspect its options.

## Choose the agent to evaluate

Your agent must already be deployed to Copilot Studio, and you need permission to access its environment, Dataverse, and the evaluations feature. You can evaluate a draft without publishing it first.

Before running an evaluation:

1. Check your agent and deployment details with `msagent agent show`, `msagent deployment list`, or `msagent deployment show`.
2. Select the environment containing the agent you want to evaluate. If you deployed to another environment, specify its ID with `--environment-id`; evaluations don't automatically target your latest deployment.
3. Evaluate the draft by default, or add `--published` to evaluate the published version.
4. If your test scenarios require authentication, provide an evaluation connection ID with `--connection`. Signing in to the CLI doesn't automatically sign in the evaluation.
5. Agree with the agent owner on suitable test data, any actions the agent can perform, and expected evaluation costs.

Warning

Evaluations and test conversation generation run in Copilot Studio and can incur charges. During an evaluation, your agent can use tools and workflows that change data or trigger actions. Use appropriate test data and connections; canceling a run doesn't undo completed actions. Review usage in the Power Platform admin center and check any connected services for additional charges.

## Create a test set

Create a CSV file with questions you want to test against your agent. Include common questions, follow-up questions, and questions the agent should ask for more information about or decline to answer. You can also include expected answers to help assess its responses.

Save the following example as `visitor-smoke.csv`:

```csv
conversationNumber,question,response
1,What should I bring for my first visit?,Bring photo identification and check in at reception.
1,Where should I check in?,Check in at reception.
2,Is parking free?,Confirm parking details with your host.
```

### CSV format

Each row contains a question. Use these columns:

| Column | Description |
| --- | --- |
| `conversationNumber` | Required. A whole number that groups questions into a conversation. Questions with the same number run in the order they appear in the file. |
| `question` | Required. The question to ask your agent. |
| `response` | Optional. An expected answer to compare with the agent's response. |

Each test set supports up to 20 conversations, with up to 6 questions per conversation and 1,000 characters per question. Every row must have a valid conversation number and a question.

### Create and inspect the test set

1. Import your CSV to create a test set in Copilot Studio. Give it a name you can use when running evaluations:

   ```powershell
   msagent agent eval testset create --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
     --name VisitorSmokeV1 --from-csv 'C:\AgentProjects\VisitorGuide\visitor-smoke.csv'
   ```


   Choose a name that isn't already used by another test set for this agent.

2. List the agent's test sets to confirm your new set appears:

   ```powershell
   msagent agent eval testset list --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>'
   ```

3. View the test set's questions, expected answers, and ID:

   ```powershell
   msagent agent eval testset show --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
     --testset VisitorSmokeV1
   ```


   Check that the imported questions and expected answers match your CSV. If a name matches more than one set, use the test set ID with `--testset` instead.

4. Export the test set to a CSV file if you want to review, share, or save a local copy:

   ```powershell
   msagent agent eval testset export --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
     --testset VisitorSmokeV1 --output 'C:\AgentProjects\VisitorGuide\visitor-reviewed.csv'
   ```

5. Review the exported CSV and remove any sensitive information before sharing it or saving it in Git. The CSV is a local copy; editing it doesn't change the test set in Copilot Studio until you import the changes with `msagent agent eval testset update`.

### Generate candidate conversations

Use `msagent agent eval generate` to suggest test conversations and save them to a CSV file. This approach lets you review and edit the questions before creating a test set in Copilot Studio.

The following example generates three conversations with two turns each:

```powershell
msagent agent eval generate --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --count 3 --turns 2 --output 'C:\AgentProjects\VisitorGuide\candidate-cases.csv'
```

Open `candidate-cases.csv` and check that the questions are relevant to your agent and appropriate for your test environment. Edit them as needed, and check that the file meets the [CSV format limits](#csv-format) before importing it. A generated file can still exceed those limits.

When you're satisfied with the conversations, use `msagent agent eval testset create` with `--from-csv` to import the reviewed file. Use `--from-csv`, not `--generate`, to keep your edits: `--generate` creates new conversations rather than using the file you reviewed.

### Update a test set

Use `msagent agent eval testset update` to add conversations from a CSV file to an existing test set. By default, existing conversations are kept.

To replace all conversations with those in your CSV, add `--replace`:

```powershell
msagent agent eval testset update --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --testset VisitorSmokeV1 --from-csv 'C:\AgentProjects\VisitorGuide\visitor-reviewed.csv' --replace
```

Export a copy of the existing set before replacing it. The CLI normally adds the new conversations before removing the old ones, but it might need to remove some first to stay within the test-set limits. If an update fails, check the conversations in Copilot Studio before trying again, because some changes might already be saved. Coordinate with your team so only one person updates the set at a time.

## Run an evaluation

Run an existing test set against your agent:

```powershell
msagent agent eval run --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --testset VisitorSmokeV1 --watch --timeout-minutes 15
```

This command evaluates the agent's draft. Add `--published` to evaluate the published version instead. If your evaluation requires authentication, add `--connection '<evaluation-connection-id>'`, using the evaluation connection's ID rather than a connector name.

You can also create a test set from a CSV and run it in one command:

```powershell
msagent agent eval run --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --from-csv 'C:\AgentProjects\VisitorGuide\visitor-smoke.csv' `
  --name VisitorReleaseV1 --watch --output 'C:\AgentProjects\VisitorGuide\release-run.json'
```

To generate new conversations instead of importing a CSV, replace `--from-csv` and its file path with `--generate 3 --turns 2`. Choose one source for each run: an existing `--testset`, a CSV file, or generated conversations.

When creating a set, choose a new name. To replace the conversations in an existing set with that name and run it, add `--update-testset`.

### Wait for results and save a report

Without `--watch`, the CLI returns the run ID once Copilot Studio accepts the evaluation. The evaluation continues in the background.

With `--watch`, the CLI waits for results up to the specified timeout. If that time expires, the evaluation can still be running in Copilot Studio. Use the run ID to check its progress rather than starting it again. The command can return successfully even if it stopped waiting before the evaluation finished.

To save a report, use `--output` with `--watch`. The report is always JSON, regardless of the filename extension, and is written only when the evaluation completes, fails, or is canceled. If the CLI stops waiting because of a timeout, it doesn't write a report file.

## Review evaluation results

List recent evaluation runs to find the one you want to review:

```powershell
msagent agent eval list --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' --limit 20
```

Use its run ID to view the results and conversation transcripts:

```powershell
msagent agent eval show --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --run-id '<run-id>' --transcript
```

Review the run's status, scores, passed and failed cases, results for each conversation, and reported credit usage. Transcripts shown in the terminal are shortened; export a report to see the full details:

```powershell
msagent agent eval show --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --environment-id '<test-environment-id>' `
  --run-id '<run-id>' --output 'C:\AgentProjects\VisitorGuide\run-details.json'
```

Use a `.json` filename for JSON output or another extension, such as `.md`, for Markdown. Add `--conversation 2` to focus the terminal output on the second conversation. The exported report still includes all conversations.

You can view and export results while an evaluation is running, but those results might be incomplete. Check the run's status to confirm whether it has completed, failed, or been canceled.

To cancel an evaluation that's still queued or running, use `msagent agent eval cancel` with the same project, agent, and environment options and `--run-id`. Completed runs can't be canceled.

Use the results to improve your agent, deploy the changes, and run the same test set against the same environment and agent version—draft or published—to compare results.

## Use the results to decide what to publish

Agree with your team on what good results look like before running evaluations. Review any failed cases and confirm that the results apply to the agent version and environment you plan to release. The CLI reports the results; you or your team choose when the agent is ready to publish.

Optionally save reports your team needs for review or future comparisons in a location with appropriate access permissions. Check transcripts for sensitive information before sharing them.

### Delete runs and test sets you no longer need

Before deleting evaluation data, check your team's retention requirements:

- `msagent agent eval delete --run-id '<run-id>'` deletes a completed, failed, or canceled run without a confirmation prompt. It doesn't delete the test set.
- `msagent agent eval testset delete --testset '<set-name-or-id>'` deletes the test set and its conversations, but keeps existing evaluation runs. It asks you to confirm the set name unless you use `--force` or `--non-interactive`.

Include the project, agent, and environment options to select the intended target when using either command.

When you review the results and agree on the next step, follow the deployment guide to [promote your changes to test or production](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/deploy?view=o365-worldwide#promote-approved-source).
