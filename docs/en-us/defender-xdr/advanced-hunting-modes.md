<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-modes -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Choose between guided and advanced modes to hunt in Microsoft Defender XDR

## Use guided and advanced modes in advanced hunting

You can find the **advanced hunting** page by going to the left navigation bar in the Microsoft Defender portal and selecting **Hunting** > **Advanced hunting**. If the navigation bar is collapsed, select the hunting icon ![Screenshot of the Advanced hunting icon in the Microsoft Defender portal navigation bar](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-modes/hunting-icon.png).

In the **advanced hunting** page, two modes are supported:

- **Guided mode** – to query using the query builder
- **Advanced mode** – to query using the query editor using Kusto Query Language \(KQL\)

The main difference between the two modes is that the guided mode *does not* require the hunter to know KQL to query the database, while advanced mode requires KQL knowledge.

Guided mode features a query builder that has an easy-to-use, visual, building-block style of constructing queries through dropdown menus containing available filters and conditions. To use guided mode, see [Get started with guided hunting mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-modes#get-started-with-guided-hunting-mode).

Advanced mode features a query editor area where users can create queries from scratch. To use advanced mode, see [Get started with advanced hunting mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-modes#get-started-with-advanced-hunting-mode).

## Get started with guided hunting mode

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

When you open the advanced hunting page for the first time after guided mode \(guided hunting\) is made available to you, you are invited to take the tour to learn more about the different parts of the page like the tabs and query areas.

To take the tour, select **Take tour** when the guided hunting invitation banner appears:

[![Screenshot of the guided hunting prompt with an option to take the tour](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-modes/1-guided-hunting-banner-tb.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-modes/1-guided-hunting-banner.png#lightbox)

Follow the blue teaching bubbles that appear throughout the page and select **Next** to continue through the tour.

You can take the tour again at any time by going to **Help resources** > **Learn more** and selecting **Take the tour**.

![Screenshot of Help resources menu with Learn more and Take the tour options](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-modes/help-resources.png)

You can then start building your query to hunt for threats. The following articles can help you get the most out of hunting in guided mode:

| Learning goal | Description | Resource |
| --- | --- | --- |
| **Craft your first query** | Learn the basics of the query builder like specifying the data domain and adding conditions and filters to help you create a meaningful query. Learn further by running sample queries. | [Build hunting queries using guided mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder) |
| **Learn the different query builder capabilities** | Get to know the different supported data types and guided mode capabilities to help you fine-tune your query according to your needs. | [Refine your query in guided mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder-details) |
| **Learn what you can do with query results** | Get familiar with the Results view and what you can do with generated results like how to take action on them or link them to an incident. | - [Work with query results in guided mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder-results)  <br>- [Take action on query results](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-take-action)  <br>- [Link query results to an incident](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-link-to-incident) |
| **Create custom detection rules** | Understand how you can use advanced hunting queries to trigger alerts and take response actions automatically. | - [Custom detections overview](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview)  <br>- [Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules) |

## Get started with advanced hunting mode

We recommend using the following learning resources to quickly get started with advanced hunting:

| Learning goal | Description | Resource |
| --- | --- | --- |
| **Learn the language** | Advanced hunting is based on [Kusto query language](https://learn.microsoft.com/en-us/azure/kusto/query/), supporting the same syntax and operators. Start learning the query language by running your first query. | [Query language overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language) |
| **Learn how to use the query results** | Learn about charts and various ways you can view or export your results. Explore how you can quickly tweak queries, drill down to get richer information, and take response actions. | - [Work with query results in advanced mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-results)  <br>- [Take action on query results](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-take-action)  <br>- [Link query results to an incident](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-link-to-incident) |
| **Understand the schema** | Get a good, high-level understanding of the tables in the schema and their columns. Learn where to look for data when constructing your queries. | - [Schema reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)  <br>- [Transition from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde) |
| **Get expert tips and examples** | Train for free with guides from Microsoft experts. Explore collections of predefined queries covering different threat hunting scenarios. | - [Get expert training](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-expert-training)  <br>- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)  <br>- [Quickly investigate entities with Go hunt](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-go-hunt)  <br>- [Hunt for threats across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices) |
| **Optimize queries and handle errors** | Understand how to create efficient and error-free queries. | - [Query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)  <br>- [Handle errors](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-errors) |
| **Create custom detection rules** | Understand how you can use advanced hunting queries to trigger alerts and take response actions automatically. | - [Custom detections overview](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview)  <br>- [Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules) |

## See also

- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Build hunting queries using guided mode](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-builder)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
