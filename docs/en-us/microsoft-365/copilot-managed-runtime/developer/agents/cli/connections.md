<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/connections?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-19 -->

# Manage agent connections with the CLI \(preview\)

\[This article is prerelease documentation and is subject to change.\]

This article explains how to manage agent connections with the CLI, including how to inspect, create, bind, and remove them in each environment. Connections involve several components:

- A connector describes an API.
- A connection holds service-side authorization under an owner.
- A connection reference is the logical declaration your definition uses.
- Binding connects that reference to an authorized connection in a particular environment.

To work with connectors, you need permission to use them in your environment, including administrator approval under your organization's data policies. You work locally with connection references. For standard connectors, the connector is already available; you create the connection in the Power Platform environment you're signed in to. The connection is stored in the cloud, not on your machine. Your local connection references are then bound to that cloud connection.

## Whose connection does the agent use?

Tools can use an agent author's connection or ask each user to sign in with their own:

- **Agent author authentication:** The tool uses the author's configured connection and its permissions.
- **User authentication:** The tool uses the signed-in user's connection and permissions. Users might be prompted to sign in or grant consent.

The CLI commands in the following section create and bind connections in your environment. Binding a connection doesn't by itself determine which authentication mode the tool uses. Check the tool's authentication settings in Copilot Studio. Signing in to the CLI is separate from signing in to a service used by a tool.

See [Configure user authentication for tools](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configure-enduser-authentication).

## When to bind connections

You can prepare cloud connections before deployment, but reference binding depends on the type of project:

| Project or task | When it can run |
| --- | --- |
| Create a cloud connection with `msagent deployment connection add --connection-only`. | Before any agent or workflow deployment. Supply the target environment ID; this step creates no reference or binding. |
| Bind references for a standalone workflow. | Before its first deployment, after local registration and deployment-record creation. The CLI resolves the local workflow definition without requiring a cloud agent. |
| Bind references for an agent. | When the target cloud agent already exists, including an existing agent you cloned or one created by a partial initial upload. A local deployment record alone isn't enough. |

Don't wait for a completely successful deployment if a missing binding is what prevents it from completing. Bind the exact reference, inspect what was saved, then retry deployment. Binding and workflow activation are separate results; an activation failure doesn't necessarily undo saved bindings.

Connection updates and draft deployments can activate eligible workflows even without publishing the conversational agent. Review the workflow's intended state and effects before either operation.

For the full standalone flow procedure, see [Manage a standalone workflow with the CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot-managed-runtime/developer/agents/cli/standalone-workflows?view=o365-worldwide#configure-and-deploy-your-workflow).

## Check your agent and environment

1. Confirm the local target with `deployment show`.
2. Discover available connectors by using `connection connectors`.

   ```powershell
   msagent deployment connection connectors --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop --filter Office --limit 50
   ```

3. View declared connection references by using `connection list`.

   ```powershell
   msagent deployment connection list --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop --by-reference --json
   ```

4. Check internal connector IDs, exact logical reference names, candidate connection IDs, owners, current bindings, and diagnostics. Consult the [connector reference](https://learn.microsoft.com/en-us/connectors/connector-reference/) for the selected service's requirements.

## Create or reuse an existing connection

Use an approved existing reference and eligible connection. If more than one option exists, it might cause ambiguity.

For an **existing** reference, bind the approved connection with connection update:

```powershell
msagent deployment connection update --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --connection-reference '<logical-reference-name>' `
  --connection-id '<approved-connection-id>' --json --non-interactive
```

The selected scope must resolve exactly one connector. An explicit ID with narrow scope skips selection menus; `--by-reference` is useful when separately resolving references.

If you need a **new** reference, use connection add:

```powershell
msagent deployment connection add --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --connector shared_office365 --connection-id '<approved-office365-connection-id>'
```

Use the returned logical name in the tool or workflow declaration. Without an explicit connection, interactive selection can choose an existing connection or create one through browser consent. A declaration can remain unbound even when the command exits successfully. Check `ready`, status, and diagnostics; use the returned binding guidance instead of repeating add and creating duplicate references.

If a cloud agent doesn't yet exist but you want to prepare an authorized connection, connection add with connection-only can operate directly in an environment:

```powershell
msagent deployment connection add --connection-only `
  --environment-id '<development-environment-id>' --connector shared_office365
```

This command always creates a new connection, declares no reference, and binds nothing. Don't combine this environment-only path with agent or deployment selectors or `--connection-id`.

## Complete consent and verify readiness

1. Complete the browser consent handoff with the intended connection owner. Don't approve scopes or service accounts outside your policy.
2. Recheck connection list. For an update result, inspect `connectionsReady`, `workflowsReady`, `ready`, and diagnostics.
3. If deployment was incomplete due to a workflow reference, bind that exact reference and retry agent deploy:

   ```powershell
   msagent agent deploy --project 'C:\AgentProjects\VisitorGuide' `
     --agent-name 'Visitor Guide' --deployment-name develop
   ```

4. Independently verify the deployed tool's reference, connection ownership, consent, and workflow activation by testing the agent.

For standalone workflows, binding can run before the first successful deployment. For agents, a partial initial upload might already have created the cloud agent needed for reference discovery.

## Handle sign-in and connection selection prompts

Some connection commands require you to choose a connection or complete consent in a browser. The `--json` option changes the output format but doesn't remove these prompts. The `--non-interactive` option stops the browser from opening automatically, but you might still need to complete consent or select a connection.

- If the command displays a consent link, open it to finish authorizing the connection. Some connectors require you to use a browser on the same machine.
- When updating connections, the command might ask you to choose from available connections. If you cancel, any connections already saved remain in place.
- When adding a connection with `--non-interactive`, the CLI creates one only if it can confirm that no existing connections are available. If it finds multiple options or can't check them, you might need to select a connection yourself.
- Changes are saved as the command progresses. If a later step fails or is canceled, earlier changes remain.

Before running a script unattended, bind your references to specific, approved connection IDs and check that the connections are ready. Any required consent still needs to be completed.

## Change or remove a connection

To use a different connection, create one or choose an existing connection, then use connection update to link your agent's connection reference to it. Test the affected tools and workflows afterward. Repeat this process for each environment where you deploy the agent.

If your agent no longer needs a connection reference, remove it with connection remove:

```powershell
msagent deployment connection remove --project 'C:\AgentProjects\VisitorGuide' `
  --agent-name 'Visitor Guide' --deployment-name develop `
  --connection-reference '<unused-logical-reference-name>'
```

This action removes the reference from your local files and tries to remove it from the Power Platform environment. If another component still uses the reference, the cloud removal might be blocked. Check the command's output to see what was removed.

Removing a reference doesn't delete the connection itself. Deleting the connection is a separate operation that uses `--connection-id`. Before deleting it, check whether other agents or workflows use it, including those outside your local project. The `--force` option doesn't bypass dependency checks in Power Platform.
