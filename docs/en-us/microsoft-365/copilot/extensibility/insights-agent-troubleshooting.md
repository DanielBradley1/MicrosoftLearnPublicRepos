<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# Troubleshoot the Microsoft 365 Insights Agent

Use this article to resolve common Insights Agent issues, including an outdated installation, an **Agent not found** install or open error, missing usage data, unavailable feedback, ownership verification, and unexpected metric results.

## The Insights Agent doesn't show feedback capabilities

You can open the Insights Agent, but its conversation starters or responses don't include feedback and ratings.

### Cause

Your installed copy didn't refresh to the current Insights Agent package.

### Resolution

1. Remove the Insights Agent from your Microsoft 365 Copilot agent list.
2. Search for **Insights Agent**.
3. Add the Insights Agent again.
4. Open it and try "Show me the agents I own" or "What feedback have users given about {Agent Name}?"

Removing and adding the Insights Agent refreshes your personal installation. It doesn't remove or modify the agents you analyze.

## The Insights Agent is searchable, but opening or installing it shows Agent not found

The Insights Agent appears in search, but selecting it produces an **Agent not found** error instead of opening or installing it.

### Cause

The Insights Agent availability assignment can be stale even when the Microsoft 365 admin center shows that the agent is available to all users.

### Resolution

Contact your Microsoft 365 administrator and ask them to reset the Insights Agent availability assignment:

1. Open the Insights Agent availability or user-assignment control in the Microsoft 365 admin center.
2. Set the Insights Agent to **No users**, and then save.
3. Set the Insights Agent to **All users**, and then save again.
4. Wait for the change to propagate, and then retry opening or installing the Insights Agent.

Important

This reset applies to the Insights Agent availability assignment. Don't change **Agent feedback sharing** as part of this recovery.

## No usage data for the agent you asked about

You ask a supported usage prompt, such as "Provide all usage insights for {Agent Name}," and the response says there's no data.

### Most likely causes

- The agent name doesn't exactly match the name visible in your tenant.
- The agent has insufficient activity for the requested window. New agents might have no activity yet, and windowed metrics need enough activity in the current and comparison periods.
- You don't have visibility into the agent.

### Resolution

Verify the exact name, confirm that the agent has enough activity for the requested window, and retry. If an active and visible agent still returns no data, contact support with the exact prompt and response through an approved channel.

## Usage works, but feedback is unavailable

### Most likely causes

- You don't own the selected agent.
- Ownership couldn't be verified.
- Your tenant administrator selected **No agents** for Agent feedback sharing.
- Your tenant administrator selected **Selected agents** and didn't include the requested agent.

### Resolution

1. Ask "Show me the agents I own."
2. Select one exact agent name from the ownership result.
3. Ask your tenant administrator to check **Agents** > **Settings** > **Agent feedback sharing**.
4. If **Selected agents** is configured, confirm that the selected agent is included.
5. Retry the feedback request after the setting has propagated.

Usage visibility doesn't grant feedback access. Enabling feedback sharing makes feedback eligible for owners, but it doesn't give administrators access unless they also satisfy the ownership check. For configuration guidance, see [Agent feedback sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing).

## The feedback request succeeds but returns zero items

No feedback is currently available for the selected agent. This is a valid result and doesn't indicate an ownership or feedback-sharing problem. No permission change is required.

## A combined usage-and-feedback request returns only one result

Usage and feedback use separate retrieval and authorization paths. If usage succeeds but feedback doesn't, follow the [feedback ownership and sharing steps](#usage-works-but-feedback-is-unavailable). If feedback succeeds but usage doesn't, verify the agent name, visibility, and requested usage window. Don't interpret one successful result as proof that the other path should also succeed.

## Ownership is denied or unavailable

| Status | Meaning | What to do |
| --- | --- | --- |
| Denied | The ownership check determined that you aren't an owner. | Choose an agent you own or ask an owner to review its feedback. |
| Unavailable | The service couldn't verify ownership. | Retry later. If the issue continues, contact support. Don't treat this as proof that you aren't an owner. |
| Ambiguous name | More than one owned agent has the same display name. | Select the exact Agent ID shown by the Insights Agent. |

## The retention response includes a caveat

A retention response includes a statement such as "This is computed as an aggregate window-over-window ratio, not user-level cohort retention."

### Cause

The caveat is required because the Insights Agent reports an aggregate sustained-usage proxy. Classical cohort retention requires tracking the same users across time, which the Insights Agent doesn't return.

### Resolution

Interpret the value as whether the active-user pool is growing, holding, or shrinking across consecutive equal-length windows.

## Install or uninstall counts are unavailable

Install and uninstall signals aren't connected to the Insights Agent data layer. Use DAU, WAU, MAU, and unique-user trends as adoption signals.

## A trend query returns an unexpectedly small number or an error

### Most likely cause

The requested time window might not have enough activity, or an earlier installed package might not parse the time expression correctly.

### Resolution

- Remove the Insights Agent, and then add it again to refresh your installation.
- Retry by using the exact agent name and a supported prompt from [Sample prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts).
- If the issue continues, contact support through an approved channel. Provide the original prompt and response.

## A comparison doesn't match another dashboard

### Likely causes

- The two surfaces use different time anchors.
- The other dashboard counts sessions, prompts, or accounts instead of distinct users.
- Someone renamed or republished the agent, and the two surfaces attribute activity to different versions.

### Resolution

Use the same date anchor, and confirm that both surfaces count distinct users. If the discrepancy remains, contact support through an approved channel. Provide the prompt and dashboard evidence.

## The fastest-growing result is unexpected

### Cause

The fastest-growing ranking ranks agents by week-over-week percentage change in unique users. A small starting population can produce a large percentage change.

### Resolution

Before you interpret the ranking, review the underlying unique-user counts and percentage change together.

## Before contacting support

- Record the exact prompt and complete response.
- Record the date, time, and tenant.
- State whether usage works and only feedback fails.
- State whether you removed and added the Insights Agent again.
- For feedback issues, record whether the response reported no feedback, sharing disabled, ownership denied, ownership unavailable, or an ambiguous agent name. Also record whether Agent feedback sharing is set to **No agents**, **All agents**, or **Selected agents**.
- Don't include user feedback comments, prompts, responses, or other private content unless support requests it through an approved channel.

## Related content

- [Sample prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts)
- [Prompt and capabilities reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-prompt-reference)
- [Microsoft 365 Insights Agent overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-overview)
