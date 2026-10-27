<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-monitor-telemetry-feedback -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Monitor your Employee Self-Service declarative agent

After you publish your Employee Self-Service declarative agent, use the **Monitor** tab in Microsoft Copilot Studio to review its usage and employee feedback.

## Review usage and feedback

Open your Employee Self-Service declarative agent in Microsoft Copilot Studio, and then select **Monitor**. Use the date-range selector to change the reporting period for all charts on the page.

The **Monitor** tab includes these cards:

- **Overview**: Review **Total sessions**, **Avg. DAU** \(average daily active users\), **Avg. user messages** per session, and **Avg. duration** per session.
- **Engagement**: Review daily sessions and active users for the selected period. Select **See details** to review daily and monthly active-user trends. To export chart data, open the chart menu and select **Download CSV**.
- **Knowledge source use**: Review up to five of the agent's most-used knowledge sources for the selected period.
- **Reactions**: Review thumbs-up and thumbs-down reactions and the comments employees submit with them.

Monitoring for declarative agents doesn't include every metric and view available for Employee Self-Service custom engine agents.

## Enable employee feedback sharing

For agents published to the Microsoft Copilot channel, an administrator must allow feedback sharing in the Microsoft 365 admin center before developers can view reactions and comments in **Monitor**. Feedback sharing is off by default.

In the Microsoft 365 admin center, go to **Agents** > **Settings** > **Agent feedback sharing**. An administrator can allow feedback sharing for all agents or selected agents. This setting controls whether developers receive feedback. It doesn't affect whether employees can rate agents.

If the **Reactions** card doesn't appear, ask your Microsoft 365 administrator to check whether feedback sharing is enabled for your agent. For the configuration steps, see [Agent feedback sharing in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing).

## Related content

- [Evaluate your Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations).
- [Known issues and limitations for Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-known-issues-limitations).
