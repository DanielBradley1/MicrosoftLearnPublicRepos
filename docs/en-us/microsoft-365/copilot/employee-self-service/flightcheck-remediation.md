<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-remediation -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Fix issues that FlightCheck finds

FlightCheck checks depend on the agent family and workspace configuration. Use the checkpoint IDs and remediation details in the generated report; do not assume every check applies to every agent.

This article explains the native declarative-agent checks and the shared FlightCheck report. The environment, solution, and integration examples later in the article apply to Custom Engine Agent or hybrid workspaces unless the report identifies the same checkpoint for your agent.

## Before you start

Run the check first. In Copilot Chat:

```text
/flightcheck
```

FlightCheck opens an HTML report when it finishes. If you only want the readiness check and don't want to install the full kit, see [Run FlightCheck without installing the full kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone).

## Native declarative-agent checks

For a native no-Dataverse declarative agent, FlightCheck uses agent-specific checks instead of the Dataverse solution and connection-reference checks used by other workspaces. The report can include:

| Checkpoint | What it checks |
| --- | --- |
| `DA-AGENT-001` | Access to the exact editable agent selected for authoring. |
| `DA-CONTENT-001` | Whether the selected agent has authored components. |
| `DA-CONN-001` and `DA-CONN-002+` | Connection readiness and per-reference connection details. |
| `ENV-CAPACITY-001` | Copilot Studio message capacity. |

The native readiness flow can also report local-file and publishing checks. A workspace that has a Dataverse endpoint uses the hybrid or legacy check path instead. Use the checkpoint ID in your report as the source of truth for which check ran and what to do next.

Native checks are read-only. The legacy full runtime-reachability probe is different: it creates and removes a temporary flow and asks for consent before running.

## How to read the report

Every result carries a checkpoint ID, such as `PRE-001` or `ENV-004`. The prefix tells you which area the checkpoint belongs to, and the report groups results by area.

Each checkpoint also carries a priority:

| Priority | What it means |
| --- | --- |
| Critical | Fix before you deploy |
| High | Fix, or have a remediation plan, before you deploy |
| Medium | Important, but you can address it after deployment |
| Low | Optional configuration |

Some checkpoints are marked for manual validation. FlightCheck can't confirm those automatically, usually because the setting isn't exposed through an API, so it tells you what to verify yourself.

## Legacy and hybrid role handoffs

The role map and common failures below apply to Custom Engine Agent or hybrid checkpoints. For a native declarative-agent result, follow the report's checkpoint-specific remediation and role handoff:

| Role | Owns |
| --- | --- |
| Microsoft 365 admin | License assignment, cloud policies, Graph connectors, and integrated app approval |
| Power Platform admin | Environments, DLP policies, connections, solution import, cloud flow state, and Dataverse environment variables |
| Entra admin | App registrations, SAML configuration, Conditional Access, and directory role assignment |
| Workday admin | ISU accounts, security groups, domain permissions, RaaS, and authentication policies |

Include the checkpoint ID and report so the administrator can review the finding and its supporting evidence.

## Legacy and hybrid checks

| Area | Prefix | What it covers |
| --- | --- | --- |
| Prerequisites | `PRE` | Licensing, capacity, and the directory roles the deployment needs |
| Environment | `ENV` | The Power Platform environment, Dataverse, DLP policies, connections, and connection references |
| Solution | `ESS-SOLN` | Whether the base Employee Self-Service solution is installed |
| Authentication | `AUTH` | Sign-in configuration and Conditional Access |
| Entra application | `ENTRA`, `SIGNOPT` | App registration, SAML settings, and assignment |
| Workday | `WD` | Tenant configuration, extension packs, connections, reference data, and topic coverage |
| ServiceNow | `SN` | Flow status and configuration |
| Topics | `TOPIC` | Trigger phrases and integration bindings on your agent's topics |
| Local files | `LOCAL` | Your local agent files and knowledge sources |
| Publishing | `PUB`, `QA` | Publishing readiness and quality checks |
| Infrastructure | `INFRA` | Reachability of the Microsoft service endpoints the agent depends on |
| Policy | `POL` | Cloud Policy settings, such as whether feedback is allowed |

## Recheck one area instead of everything

After you fix a result, rerun the relevant check. The available scopes vary by agent family. From a terminal in the `ess-maker-skills` folder, use `python scripts/flightcheck/cli.py --help` to see the supported scopes for your version. To recheck one result, use `--checkpoint` with the exact checkpoint ID from the report.

## Common Custom Engine Agent or hybrid failures

### Licenses and roles

**Microsoft 365 Copilot licenses aren't assigned \(`PRE-001`\)**

No Microsoft 365 Copilot license is assigned to users in the tenant.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Billing** > **Licenses**.
2. Purchase or assign Microsoft 365 Copilot licenses.
3. Assign them to the people who use the Employee Self-Service agent.

**Copilot Studio licenses aren't assigned \(`PRE-002`\)**

Administrators and makers don't have Copilot Studio licenses.

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to **Billing** > **Licenses**.
2. Assign Copilot Studio licenses to your Power Platform administrators and environment makers.

**A required directory role isn't assigned \(`PRE-008`, `PRE-009`\)**

No user holds the Global Administrator role \(`PRE-008`\) or the Power Platform Administrator role \(`PRE-009`\).

1. In the [Microsoft Entra admin center](https://entra.microsoft.com), go to **Roles and administrators**.
2. Search for the role, then select **Add assignment**.
3. Have the administrator assign the role to the person who must perform the operation. Do not assign a broad directory role to the maker unless the operation requires it.

For the full list of roles the deployment needs, see [Prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites).

### Environment

**The environment can't be found \(`ENV-001`\)**

FlightCheck couldn't resolve the environment, or your account doesn't have administrative access to it.

1. Confirm the environment the kit is pointed at is the one you expect.
2. Confirm you hold the Environment Admin or Power Platform Administrator role.
3. If the kit is pointed at the wrong environment, run `/setup` again.

**Dataverse isn't provisioned \(`ENV-002`\)**

The environment exists, but it has no Dataverse database.

1. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com), select the environment.
2. Select **Add database**, then wait for provisioning to finish.

**No DLP policies apply, or a required connector is blocked \(`ENV-008`\)**

Either no data loss prevention policy covers the environment, or an existing policy blocks a connector the agent needs.

1. In the Power Platform admin center, go to **Policies** > **Data policies**.
2. Review the policies that apply to this environment.
3. Make sure the Workday, ServiceNow, and SAP connectors are in the **Business** group.

**A connection reference is unbound or orphaned \(`ENV-004`\)**

A topic uses a connection reference that has no connection bound, points at a connection that no longer exists, or isn't present in the environment at all. The report names the specific reference.

In the Power Platform admin center, open the solution and bind the reference to a valid connection.

For environment setup guidance, see [Prepare for deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prepare).

### Authentication

**Entra ID isn't reachable \(`AUTH-001`\)**

FlightCheck couldn't read organization information. This is almost always a permissions problem rather than an outage. Confirm your account has permission to read directory information, then rerun the check.

**No Conditional Access policies are configured \(`AUTH-002`\)**

This is reported as a warning, not a failure. It flags a security gap rather than something that blocks deployment. If your organization expects Conditional Access, configure it in the [Microsoft Entra admin center](https://entra.microsoft.com) under **Protection** > **Conditional Access**.

### Workday

**A required environment variable isn't set \(`WD-ENV-001`\)**

The account name environment variable wasn't configured after the Workday extension pack was installed.

Run `/connect-workday` to walk through the setup, which sets this for you. To set it manually, open the environment's default solution in the Power Platform admin center and set the variable to your ISU account name.

**A connection is in an error state \(`WD-CONN`\)**

Authentication expired, or credentials were rotated.

1. In the Power Platform admin center, go to **Connections**.
2. Find the connection in an error state, then select **Edit** and reauthenticate.
3. Run `/connect-workday` if you'd rather be guided through it.

**A flow is turned off \(`WD-FLOW`\)**

A Workday cloud flow is disabled. In Power Automate, find the flow and turn it on.

**Permission denied on a workflow \(`WD-WF`\)**

The ISU account doesn't hold the Workday security domain the workflow needs. The report names the workflow. Ask your Workday administrator to grant the corresponding self-service permission for that domain.

For Workday setup, see [Simplified Workday integration setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-simplified-setup).

## When the kit fixes it for you

FlightCheck offers to fix the issues it can resolve safely. When it makes an offer, it tells you what it intends to change and waits for you to confirm. Anything it can't fix, or that needs an administrator, is reported with enough detail to hand off.

## Declarative agents

FlightCheck includes checkpoints specific to declarative agents, covering agent identity and connection state.

Note

Some commands behave differently on declarative agents. In particular, `/troubleshoot` isn't available yet. The Agent Developer Kit commands reference lists current availability. See [Release notes, known issues, and limitations](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/known-issues-limitations) for the latest status.

## If you're still stuck

- For problems in your first day with the kit, such as installation and setup, see [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).
- For problems with the kit itself, file an issue in the [kit repo](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/issues).
- For problems with the Employee Self-Service product rather than the kit, use your normal support route. The kit is a sample and learning toolkit, and its support is separate from the product's.

## Related content

- [Run FlightCheck without installing the full kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/flightcheck-standalone)
- [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started)
- [Prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites)
- [Publish the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish)
