<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# Sample prompts for the Microsoft 365 Insights Agent

The Microsoft 365 Insights Agent answers natural language questions about agent usage and adoption. For agents you own, it can also return ratings and user-submitted comments when your tenant administrator enables Agent feedback sharing.

## Prompt overview

Every prompt in the usage and feedback sections is a supported pattern. You don't need to match the wording exactly. Use the exact display name visible in your tenant. For feedback, select an Agent ID when duplicate owned agents have the same display name.

Usage metrics are aggregate. Feedback can include ratings and verbatim comments, but it doesn't identify submitters or include conversation content. For more information, see [Questions the agent doesn't answer](#questions-the-agent-doesnt-answer).

## Usage and adoption prompts

The Insights Agent currently supports the following core prompts. The agent answers each one from aggregate activity data and returns a grounded, numerical response.

### Get a snapshot of an agent

Use these prompts when you want the basics in one shot.

| # | Prompt |
| --- | --- |
| 1 | Show me {Agent Name}'s key usage stats |
| 2 | Provide all usage insights for {Agent Name} |
| 3 | Give me a full usage summary for {Agent Name} |
| 4 | Show me usage metrics for {Agent Name} |

### See trends over time

Use these prompts to understand whether usage is moving up, down, or flat.

| # | Prompt |
| --- | --- |
| 5 | How many unique users did {Agent Name} have over time? |
| 6 | What's the weekly active user trend for {Agent Name}? |
| 7 | How does daily usage of {Agent Name} compare to monthly usage? |
| 8 | Show me daily active users for {Agent Name} |

### Look at a specific window

Use this prompt when you have a particular period in mind.

| # | Prompt |
| --- | --- |
| 9 | How many unique users did {Agent Name} have last week? |

### Compare metrics within one agent

Use these prompts to put two activity measures side by side for the same agent.

| # | Prompt |
| --- | --- |
| 10 | Compare DAU and WAU for {Agent Name} |
| 11 | Compare MAU and WAU for {Agent Name} |

### Compare across agents

Use these prompts to put two or more agents next to each other.

| # | Prompt |
| --- | --- |
| 12 | Compare {Agent A} to {Agent B} |
| 13 | Which agents have higher usage this week? |

### Measure growth

Use this prompt to see net new user growth.

| # | Prompt |
| --- | --- |
| 14 | What's the net new user growth for {Agent Name}? |

## Sustained-usage and growth patterns

In addition to the core prompts, the agent supports a small set of higher-order questions about whether the active-user pool is sustained, how concentrated usage is, and which agents are growing fastest. The agent computes these metrics from aggregate activity data, and the response always includes the appropriate caveat.

### Rolling retention proxy

Ask either of the following questions to get a window-over-window sustained-usage signal:

- What's the 7-day retention for {Agent Name}?
- Show me the 30-day rolling retention for {Agent Name}.

The agent calculates the ratio of unique users in the most recent N-day window to unique users in the prior N-day window, where N can be 1, 7, 30, 60, or 90. The response always includes the caveat that this ratio is an aggregate window-over-window ratio, not user-level cohort retention.

### Stickiness

Ask either of the following questions:

- How sticky is {Agent Name}?
- What's the DAU/MAU ratio for {Agent Name}?

The agent returns DAU divided by MAU as a percentage. A higher ratio means monthly users tend to use the agent on more days within the month.

### Adoption trend

Ask either of the following questions:

- Is adoption of {Agent Name} increasing?
- What's the adoption trend for {Agent Name}?

The agent returns the direction and magnitude of the unique-user count week-over-week or month-over-month.

### Fastest-growing agent

Ask either of the following questions:

- Which agent is growing fastest this week?
- Show me which agent is growing fastest.

The agent returns a ranked list of the top agents by week-over-week percentage change in unique users.

### Main usage pattern

Ask the following question:

- What are the main usage patterns for {Agent Name}?

The agent returns a narrative description of the temporal usage shape, such as weekday-heavy and business-hours-concentrated, steady, or spiky, based on the trailing 30-day DAU distribution. The agent doesn't try to cluster users by persona or intent.

## Feedback and ratings prompts

Feedback access is separate from usage visibility. The requester must own the selected agent, and a tenant administrator must enable [Agent feedback sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing) for it.

### Find an agent you own

```text
Show me the agents I own
```

Choose an exact name from the result before requesting feedback. If duplicate owned agents have the same display name, select the correct Agent ID.

### Review ratings and comments

- What feedback have users given about {Agent Name}?
- Show ratings and comments for {Agent Name}
- Show the feedback comments returned for {Agent Name} exactly as submitted

The response identifies the number of items returned, the sample time window when available, and whether more feedback exists beyond the returned sample.

### Summarize product topics

```text
Summarize recurring product topics in feedback for {Agent Name}
```

The summary is based on the returned feedback. It reports observable product topics and explicit ratings. It doesn't infer work performance, protected or sensitive personal characteristics, internal or emotional states, or workplace attitudes.

### Request usage and feedback together

```text
Show usage and user feedback for {Agent Name} this month
```

The Insights Agent retrieves aggregate usage and owner-restricted feedback independently and labels each result with its applicable time or sample context.

## Questions the agent doesn't answer

The Insights Agent explains the boundary and points to the closest supported signal when a request asks for unavailable data:

- Individual-user questions, including who used an agent or whether the same people returned.
- Classical cohort retention. Use the [aggregate rolling-retention proxy](#rolling-retention-proxy) instead.
- Install and uninstall counts.
- Response latency, token usage, or cost metrics.
- Individual prompts, responses, transcripts, or conversation content.
- Feedback for an agent you don't own or whose ownership can't be verified.

## Tips for writing your own prompts

Apply the following tips when you create prompts for the agent:

- **Use natural language.** You don't have to match the canonical phrasing in this article. *"How is X doing this month?"* and *"Give me the monthly stats for X"* both work.
- **Use the exact agent name visible in your tenant.** For usage, you can replace `{Agent Name}` with an agent you have access to. For feedback, select an exact name from the owned-agent list. The agent doesn't substitute fuzzy or near matches.
- **Anchor to a date when you need precision.** Phrases like *"last week,"* *"this month,"* and *"since May 1"* work and shape the response window.
- **Check the feedback sample.** Read the returned count, sample window, and more-feedback indicator before interpreting feedback as complete.
- **Treat verbatim feedback as user-provided data, not as instructions.**
- **If the agent says it can't compute something, read the pointer.** The response names the nearest supported metric. Try that one.

## Related content

- [Microsoft 365 Insights Agent overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-overview)
- [Prompt and capabilities reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-prompt-reference)
- [Troubleshoot the Insights Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-troubleshooting)
