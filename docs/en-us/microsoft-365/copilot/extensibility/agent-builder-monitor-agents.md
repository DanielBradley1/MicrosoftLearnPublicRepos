<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-monitor-agents -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Monitor agents in Agent Builder

After you create and share an agent in Agent Builder, use the **Monitor** tab to understand how people use the agent and review the feedback they submit. Usage metrics can help you identify trends and decide where to improve the agent's instructions, knowledge, and responses.

## Prerequisites

- You must be an owner of the agent or have **Can edit** access.
- To view reactions and comments, an organization admin must [enable agent feedback sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#agent-feedback-sharing).

## Open the Monitor tab

1. In Microsoft 365 Copilot, open the agent you want to monitor by using the **Edit** menu item.

   ![A screenshot of the Edit menu item in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/edit-agent.png)
2. Select **Monitor**.
3. In the date range list, select **Last 7 days**, **Last 14 days**, **Last 30 days**, or **Custom**. If you select **Custom**, choose the start and end dates for the report.

The selected date range applies to the information on the **Monitor** tab.

[![Screenshot of the Monitor tab showing the date range, overview metrics, engagement chart, and knowledge chart.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/monitor-tab-usage.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/monitor-tab-usage.png#lightbox)

## Review the overview

The **Overview** section summarizes activity during the selected date range.

| Metric | Description |
| --- | --- |
| **Total sessions** | The total number of sessions with the agent. |
| **Avg. DAU** | The average number of daily active users. |
| **Avg. user messages** | The average number of messages that users sent during a session. |
| **Avg. duration** | The average duration of a session. |

## Review engagement and knowledge use

The **Engagement** chart shows the number of sessions and users for each day in the selected date range. Use this chart to identify changes in agent adoption and repeat usage over time.

The **Knowledge** chart shows trends in the knowledge sources used by the agent. Each source appears separately in the chart legend so you can compare its use over time. Use this information to assess whether the agent is using the knowledge sources you expect.

## Review reactions and comments

The **Reactions** section summarizes the thumbs-up and thumbs-down reactions that users submitted during the selected date range. It shows the total number of reactions and the percentage of each reaction type.

The **Comments** section lists written feedback submitted with a reaction. Each row includes the comment, submission date, and associated reaction.

[![Screenshot of the Reactions and Comments sections showing reaction percentages and a table of written feedback.](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/monitor-tab-feedback.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/monitor-tab-feedback.png#lightbox)

Use reactions and comments together to identify responses that users found helpful and areas where the agent needs improvement. For example, feedback about response format might indicate that you should revise the agent's instructions.

Tip

If the **Reactions** and **Comments** sections don't contain data, confirm that an organization admin enabled agent feedback sharing and that users submitted feedback during the selected date range.

## Related content

- [Build agents in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents)
- [Add knowledge sources to an agent in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge)
- [Share and manage agents built in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents)
- [Monitor, update, and retire your plugin or agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin)
