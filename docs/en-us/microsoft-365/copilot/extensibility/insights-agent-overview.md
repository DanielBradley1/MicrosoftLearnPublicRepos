<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-overview -->
<!-- Sitemap-Last-Modified: 2026-10-27 -->

# Microsoft 365 Insights Agent overview

The Microsoft 365 Insights Agent brings usage analytics and user feedback for the agents in your tenant into one Copilot experience. Ask natural language questions about daily, weekly, and monthly active users, rolling retention, stickiness, adoption trends, agent comparisons, ratings, and user-submitted verbatim feedback.

Use aggregate usage signals to understand what is happening, and then review ratings and comments to decide what to improve. Usage is available for agents you can see in your tenant. Feedback requires verified ownership and tenant-admin-enabled feedback sharing for the selected agent.

## Why use the Insights Agent

Agent owners, IT admins, and business stakeholders all need to know how their agents are performing. Today, that information is located in dashboards, Power BI reports, Teams Developer Portal, and ad hoc Kusto queries that most of these audiences can't run themselves. As a result:

- It takes a long time to learn whether anyone is using an agent after you ship it.
- Synchronization across these sources can be inconsistent.
- Understanding usage depends on a small group of analysts.
- Teams define basic terms like *retention* and *stickiness* inconsistently.
- Agent owners might not have a consistent way to review the feedback users submit for their agents.

The Insights Agent gives you a consistent, documented set of activity metrics and answers in plain language in the same Copilot Chat surface where your agents live. Aggregate usage signals show whether adoption is growing, holding, or declining. Ratings and user-submitted verbatim feedback add direct context about what users value and what needs attention.

The two data types have different access rules. Agent visibility is enough for aggregate usage analytics. Feedback is returned only when the requester owns the agent and a tenant administrator has enabled feedback sharing for it. Returned feedback excludes submitter identity and associated conversation content.

## Who it's for

The Insights Agent is built for three audiences:

1. **Agent owners and product managers.** You need to know whether usage is growing, where it's plateauing, and how it compares with peer agents in your tenant. For agents you own, you can pair those signals with ratings and comments to identify product issues and prioritize improvements.
2. **IT administrators and Copilot champions.** You need adoption trends and a defensible way to discuss them with business sponsors. Tenant administrators also control whether feedback is eligible to be shared with owners through the Agent feedback sharing setting in the Microsoft 365 admin center. This control doesn't by itself give administrators access to an agent's feedback.
3. **Business stakeholders and executives.** You funded an agent investment and want a periodic, plain-language read on whether it's paying off, without learning a BI tool.

The agent isn't designed for individual user analysis or cohort attribution. For more information, see [Scope boundaries](#agent-scope).

## What you can do with the Insights Agent

By using the Insights Agent, you can:

- Get daily, weekly, and monthly active users for any agent you can see in your tenant.
- Compare metrics across two agents side by side.
- See unique user counts over rolling windows \(last 7 days, last 30 days, or a custom anchor date\).
- Get an aggregate rolling retention proxy \(1, 7, 30, 60, or 90 day windows\) without exposing individual identity.
- Get usage concentration \(stickiness\) \(DAU divided by MAU\) for any agent.
- Identify the fastest-growing agent in your tenant by week-over-week change in unique users.
- Get a narrative read of an agent's main usage pattern \(weekday-heavy, business-hours-concentrated, steady, or spiky\) from the trailing 30-day distribution.
- List the agents you own so you can select an exact agent for a feedback request.
- Review ratings and user-submitted verbatim comments for an agent you own, when your tenant admin enables feedback sharing for that agent.
- See the number of feedback items returned, the sample time window, and whether more feedback is available.
- Ask for a summary of recurring product topics in the returned feedback without inferring user identity, emotion, attitude, or work performance.

## Access and data visibility

Access depends on the type of information you request:

- **Usage analytics.** A user with a Microsoft 365 Copilot license can ask about any agent they can see and use in their tenant. Ownership isn't required. Results are aggregate and don't identify individual users.
- **Feedback and ratings.** The requester must be a verified owner of the selected agent, and a tenant administrator must enable feedback sharing for all agents or include that agent under **Selected agents**. Usage visibility alone doesn't grant feedback access.
- **Tenant administration.** The Agent feedback sharing setting determines whether feedback is eligible to share with owners. It doesn't affect whether users can submit ratings or comments, and it doesn't give administrators access to an agent's feedback unless they also satisfy the ownership check.
- **Work IQ.** Programmatic access follows the same rules: agent visibility for aggregate usage; administrator-enabled sharing and verified ownership for feedback.

## Available metrics

The agent currently supports the following metrics. It computes each metric deterministically from aggregate activity data. It doesn't generate numbers or estimate them from a model.

| Metric | What it answers | How it's computed |
| --- | --- | --- |
| Daily active users \(DAU\) | How many distinct users used the agent today, or on a specified day | Count of distinct users with at least one session in the day |
| Weekly active users \(WAU\) | How many distinct users used the agent in a 7-day window | Count of distinct users with at least one session in the 7-day window |
| Monthly active users \(MAU\) | How many distinct users used the agent in a 30-day window | Count of distinct users with at least one session in the 30-day window |
| Unique users over time | How the unique-user count changes across windows | Series of distinct-user counts across consecutive windows |
| Pairwise compare | Side-by-side DAU, WAU, and MAU for two agents | Two parallel metric pulls plotted together |
| Rolling N-day retention proxy | Whether the active-user pool is sustained, growing, or shrinking | `unique_users[t − N → t] / unique_users[t − 2N → t − N]`, where N is 1, 7, 30, 60, or 90 |
| Stickiness | How concentrated usage is among monthly users | DAU divided by MAU, expressed as a percentage |
| Adoption trend | Direction of the unique user count week-over-week or month-over-month | Sign and magnitude of the most recent week-over-week or month-over-month delta |
| Fastest growing | Which agent grew the most this week | Ranked week-over-week percentage delta of unique users across agents in scope |
| Main usage pattern | Temporal shape of usage | Categorical narrative from the DAU distribution over the trailing 30 days |

Important

The rolling retention proxy is an **aggregate window-over-window ratio**, not user-level cohort retention. The agent always includes this caveat in its response. Cohort retention requires user-level identity, which the Insights Agent doesn't collect by design.

## Available feedback and ratings

The Insights Agent returns feedback only when both access checks pass: a tenant administrator enables feedback sharing for the selected agent, and the requester is a verified owner of that agent. Being able to see or use an agent, or retrieve its aggregate usage, doesn't establish ownership or grant access to feedback.

| Feedback data | What it answers | What it returns |
| --- | --- | --- |
| Ratings | What ratings users submitted | Thumbs-up or thumbs-down values with the feedback sample |
| User-submitted verbatim feedback | What users said about the agent | Verbatim comments, which can be reproduced when explicitly requested |
| Returned feedback count | How many feedback items are included | Count of feedback items in the returned page |
| Sample time window | When the returned feedback was submitted | Start and end timestamps for the returned feedback sample, when available |

Important

Feedback results don't include submitter identity. The Insights Agent also doesn't expose AI context, individual prompts or responses, transcripts, or conversation content.

When summarizing feedback, the agent reports observable product topics and explicit ratings. It doesn't infer work performance, protected or sensitive personal characteristics, internal or emotional states, or workplace attitudes.

## How usage and feedback requests work

For usage analytics, a typical interaction follows this pattern:

1. You ask the Insights Agent a question in Microsoft 365 Copilot Chat. For example, "What's the weekly active user trend for {Agent Name}?"
2. The agent matches your intent to the supported metrics.
3. If the query is supported, the agent pulls the relevant aggregate metrics for the agent and window you asked about, and then returns a grounded answer with the underlying numbers.
4. If the query isn't supported - for example, individual-user retention - the agent returns a deterministic, scoped-down response that points you to the closest supported signal.

For a list of supported prompts and how to phrase them, see [Sample prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts).

### How feedback works

Feedback requests follow a separate interaction:

1. A tenant administrator enables Agent feedback sharing for all agents or includes the selected agent.
2. You ask the Insights Agent which agents you own, or request feedback for an exact owned agent.
3. The agent resolves the selected agent and verifies that the requester is an owner before retrieving feedback.
4. When ownership is verified and feedback sharing is enabled for the selected agent, the agent returns available ratings and verbatim comments with the returned feedback count, sample window, and whether more feedback is available.
5. If ownership can't be verified, the agent doesn't return feedback and explains the ownership status.

### Admin control for feedback sharing

A tenant administrator controls feedback sharing in the Microsoft 365 admin center at **Agents** > **Settings** > **Agent feedback sharing**. Selecting **All agents** or **Selected agents** makes feedback eligible for sharing with verified owners of the applicable agents. The setting doesn't affect whether people can submit ratings or comments, and it doesn't grant administrators access to an agent's feedback unless they also satisfy the ownership check. For full configuration guidance, see [Agent feedback sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing).

## Two ways to get usage and feedback data

You can get usage and feedback data for agents in your tenant by asking the Insights Agent directly in Microsoft 365 Copilot Chat or by accessing the same capabilities programmatically through Work IQ.

|  | In-product \(Insights Agent\) | Programmatic \(Work IQ\) |
| --- | --- | --- |
| **What it is** | Ask the Insights Agent natural-language questions in Copilot Chat | Pull usage metrics and feedback from the Work IQ command line and endpoints |
| **Best for** | Agent owners, IT admins, and sponsors who want a quick, plain-language read | Developers automating the data into dashboards, scorecards, or pipeline checks |
| **Cost** | Included with your Copilot license; no additional cost | Metered through Copilot Credits |

Both paths support usage analytics and feedback. Usage metrics remain aggregate, and feedback access follows the same admin-sharing and ownership requirements. The difference is the surface and how you consume the data.

### In-product experience \(no additional cost\)

Using the Insights Agent inside Microsoft 365 Copilot Chat is included with your Copilot license. There's no additional charge for asking usage questions in product. For most agent owners, IT admins, and business sponsors, the in-product experience is the fastest way to get a grounded answer.

You can access feedback and ratings through the in-product Insights Agent experience when feedback sharing is enabled for the selected agent and your ownership is verified.

### Programmatic access with Work IQ

When you want usage metrics or feedback in your own systems—for example, feeding a weekly adoption scorecard, populating a dashboard, or adding a usage check to an automated pipeline—use Work IQ. Through its command line and endpoints, you can request the supported usage metrics and feedback programmatically and integrate the results into your own workflows. Work IQ programmatic access is a metered, consumption-based capability billed through Copilot Credits.

## Agent scope

The Insights Agent has a narrow scope. The following capabilities are currently out of scope and are handled by separate capabilities:

- **Individual-user analysis.** Usage analytics report aggregate metrics only. The agent doesn't track which specific users used an agent.
- **Install and uninstall trends.** Install signal isn't currently connected to the Insights Agent data layer.
- **Engagement depth and session quality.** These metrics require either user-level identity or richer telemetry than the current data layer provides.
- **Feedback for agents you don't own.** Usage visibility doesn't establish ownership. The agent returns feedback only after ownership is verified.
- **Submitter identity and conversation content.** Feedback results don't include submitter identity, AI context, prompts, responses, transcripts, or conversation content.
- **Restricted inferences from feedback.** The agent doesn't infer work performance, protected or sensitive personal characteristics, internal or emotional states, or workplace attitudes from feedback.

## Related content

- [Sample prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-sample-prompts)
- [Prompt and capabilities reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-prompt-reference)
- [Troubleshoot the Insights Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/insights-agent-troubleshooting)
