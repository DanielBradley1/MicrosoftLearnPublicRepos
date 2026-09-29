<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-limits -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Use the advanced hunting query resource report

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

The query resources report shows your organization's consumption of CPU resources for hunting based on queries that ran in the last 30 days by using any of the hunting interfaces.

The query resources report is useful for identifying the most resource-intensive queries and understanding how to prevent throttling due to excessive use.

## Understand advanced hunting quotas and usage parameters

To keep the service performant and responsive, advanced hunting sets various quotas and usage parameters \(also known as "service limits"\). For more information, see [Quotas and usage parameters](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview#quotas-and-usage-parameters).

## Access the query resources report

You can access the query resources report in two ways:

- In the advanced hunting page, select **Query resources report**:

  [![view the query resources report button in the AH portal](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/view-query-resources%20report.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/view-query-resources%20report.png#lightbox)
- In the **Reports** page, find the new report entry in the **General** section.

  [![view the query resources report in the Reports section](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/reports-general-query-resources.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/reports-general-query-resources.png#lightbox)

All users can access the reports. However, only people with Microsoft Entra Security Reader and above roles can see queries done by all users in all interfaces. Other users can only see:

- Queries they ran via the portal
- Public API queries they ran themselves and not through the application
- Custom detections they created

## Query resource report contents

By default, the query resources report table displays queries from the last day. It's sorted by resource usage, so you can easily see which queries used the most CPU resources.

The query resources report includes all queries that ran, along with detailed resource information for each query:

- **Time** – when the query ran
- **Interface** – whether the query ran in the portal, in custom detections, or through API query
- **User/App** – the user or app that ran the query
- **Resource usage** – an indicator of the amount of CPU resources a query used. It can be Low, Medium, or High. High means the query used a large amount of CPU resources and you should improve it to be more efficient.
- **State** – whether the query completed, failed, or was throttled
- **Query time** – how long it took to run the query
- **Time range** – the time range used in the query

Tip

If the query state is **Failed**, you can view the reason for the query failure by hovering over the field.

[![view inefficient queries](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/excessive-usage-sample.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/excessive-usage-sample.png#lightbox)

## Find resource-heavy queries

You can probably optimize queries with high resource usage or a long query time to prevent throttling.

The graph displays resource usage over time per interface. You can easily identify excessive usage and select the spikes in the graph to filter the table accordingly. When you select an entry in the graph, the table filters to that specific date.

You can identify the queries that used the most resources on that day and take action to improve them. [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices) or educate the user who ran the query or created the rule to take query efficiency and resources into consideration.

To view a query, select the ellipsis \(**...**\) beside the timestamp of the query you want to check, and then select **Open in query editor**.

If you're using guided mode, you need to [switch to advanced mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder-details#switch-to-advanced-mode-after-building-a-query) to edit the query.

The graph supports two views:

- Average use per day – the average use of resources per day
- Highest use per day – the highest actual use of resources per day

![Screenshot of the query resources report showing two available view modes for reviewing resource usage over time.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-limits/resource-usage-over-time.png)

The difference between these two views means that, for instance, if on a specific day you ran two queries, one query used 50% of your resources and the other query used 100%, the average daily use value shows 75%, while the top daily use shows 100%.

## Related articles

- [Advanced hunting best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Handle advanced hunting errors](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-errors)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
