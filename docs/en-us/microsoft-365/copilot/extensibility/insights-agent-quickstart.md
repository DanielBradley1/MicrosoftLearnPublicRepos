<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-quickstart -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# Quickstart: Use the Microsoft 365 Insights Agent

The Microsoft 365 Insights Agent answers natural language questions about how agents in your tenant are used. It returns aggregate usage metrics for agents you can see. For agents you own, it also returns ratings and user-submitted comments when your tenant administrator enables Agent feedback sharing.

This quickstart shows how to ask your first usage question, compare metrics, list the agents you own, and request feedback for an owned agent.

## Prerequisites

Before you begin, make sure you have the following items:

- A Microsoft 365 Copilot license assigned to your account.
- At least one Copilot agent deployed in your tenant that you have permission to use. You don't need to own an agent to request its aggregate usage metrics.
- A few days of agent activity in your tenant. Some metrics, such as rolling retention, adoption trend, and fastest-growing, need at least one prior window of data to compute a delta. New tenants might see partial results until enough activity accumulates.
- For feedback: verified ownership of the selected agent and [Agent feedback sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing) enabled for that agent by a tenant administrator.

## Step 1: Open the Insights Agent

Sign in to [Microsoft 365 Copilot Chat](https://m365.cloud.microsoft/chat) by using a work account that's assigned a Copilot license in your tenant.

In the agent picker, search for **Insights Agent**, and then select it.

## Step 2: Choose an agent for a usage question

Have the exact display name of an agent in your tenant ready. You can request usage for an agent visible to you. Ownership isn't required for aggregate usage analytics.

## Step 3: Ask your first usage question

Paste the following prompt into the chat, and replace `{Agent Name}` with the name of the agent you want usage data for.

```text
Provide all usage insights for {Agent Name}
```

Select **Enter**, and then wait for the response.

## Step 4: Read the usage response

A successful response includes the following:

- A short narrative summary that names the agent you asked about and identifies the time window that the numbers cover.
- One or more aggregate metrics from the supported-metric list. For example, daily active users, weekly active users, monthly active users, or unique users over time.
- The numerical values themselves, expressed as counts or percentages.
- A caveat line on any metric that requires interpretation. For example, the rolling retention proxy is always labeled as an aggregate window-over-window ratio, not user-level cohort retention.

If the Insights Agent doesn't have data for the requested agent or window, it says so instead of generating a number.

## Step 5: Try a comparison

After you have a baseline response, try one of the comparison prompts to see how the agent handles a two-metric or two-agent question:

```text
Compare DAU and WAU for {Agent Name}
```

To compare two agents, use:

```text
Compare {Agent A} to {Agent B}
```

The response shape is the same: a narrative summary, and then the numerical comparison.

## Step 6: List the agents you own

Feedback requests require ownership. Ask:

```text
Show me the agents I own
```

The response lists agents you own. When more than one owned agent has the same display name, the response includes Agent IDs and asks you to select one. It doesn't choose an agent automatically.

## Step 7: Request feedback

Choose one exact agent from the list of agents you own, and then ask:

```text
What feedback have users given about {Agent Name}?
```

If ownership is verified and feedback sharing is enabled for the selected agent, a response can include:

- Thumbs-up or thumbs-down ratings.
- User-submitted comments.
- The number of feedback items returned.
- The sample time window, when available.
- Whether more feedback is available beyond the returned sample.

Important

Feedback results don't include submitter identity, AI context, individual prompts or responses, transcripts, or other conversation content.

## Confirm successful setup

You completed the quickstart when:

- The Insights Agent appears in your Microsoft 365 Copilot Chat agent picker.
- A prompt against a real agent in your tenant returns a grounded numerical response that states the agent name and time window.
- A comparison prompt returns parallel metrics for both items being compared.
- The ownership prompt returns agents whose ownership can be verified.
- For an owned agent with feedback sharing enabled, a feedback prompt returns available ratings or comments, or clearly reports that no feedback is available. When feedback is returned, the response identifies the returned sample.

If a step doesn't produce the result described, see [Troubleshoot the Insights Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-troubleshooting).

## Related content

- [Sample prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts)
- [Prompt and capabilities reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-prompt-reference)
- [Microsoft 365 Insights Agent overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-overview)
