<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/live-testing?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Ask an agent questions from the terminal \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Use the `msagent test ask` command to ask a published Copilot Studio agent questions from the terminal and check its live behavior. The following example sends a question to a published agent in the public cloud:

```powershell
msagent test ask --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --query 'What should I bring for my first visit?' --plain
```

## Prerequisites

- An installed CLI and authorization to use this preview.
- A published public-cloud Copilot Studio agent and the exact intended deployment.
- A work account with environment access and agent invocation access.

Note

Testing sends your question to the cloud-hosted, published agent. Its tools and workflows can use credits and make changes to connected services. If you cancel a query, actions already started might still finish and aren't undone. Before retrying, check whether the agent already completed the requested action.

## Sign in and ask your agent a question

1. Sign in with authentication login and check your authentication status:

   ```powershell
   msagent auth login --account 'tester@contoso.com' --tenant '<tenant-id>' --cloud prod
   msagent auth status
   ```

2. Use `test ask`, explicitly selecting the registered agent and deployment:

   ```powershell
   msagent test ask --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop `
     --query 'Where should a visitor check in?' --plain
   ```


   If you have no local project, the fully explicit `test ask` route is:


   ```powershell
   msagent test ask --schema-name '<published-agent-schema>' `
     --environment-id '<target-environment-id>' --tenant '<tenant-id>' `
     --deployment-name '<approved-target-label>' --query 'Hello' --plain
   ```

## Ask a follow-up question or start a new conversation

To ask a follow-up question, copy the conversation ID returned by your previous query and include it with `--conversation-id`. Use the same agent and deployment:

```powershell
msagent test ask --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --conversation-id '<returned-conversation-id>' `
  --query 'What should I bring?' --plain
```

To start a new conversation, leave out `--conversation-id`. The CLI starts a separate conversation each time unless you provide an ID.

Choose the output format that suits your workflow:

- Use `--plain` to display just the final response.
- Use `--json` for structured output that you can capture in a script. It includes activities and the final status.

Use only one of these output options at a time. Neither option changes sign-in requirements. If you use `--non-interactive`, the command stops if it needs you to sign in interactively.

## Use the CLI in a script

Add `--non-interactive` to run a query without interactive sign-in prompts. Sign in first using `msagent auth login`. If the query needs further sign-in interaction, it stops so you can sign in again.

Use `--json` to capture structured output:

```powershell
msagent test ask --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --query 'Where should a visitor check in?' `
  --non-interactive --json
```

This uses your existing signed-in session; it doesn't set up service-principal authentication or unattended sign-in.
