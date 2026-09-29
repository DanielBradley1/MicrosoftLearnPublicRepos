<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/streaming-api-event-hub -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Configure Microsoft Defender XDR to stream Advanced Hunting events to your Azure event hub

Learn how to configure Microsoft Defender XDR to stream Advanced Hunting events to Azure Event Hubs for downstream processing, integration, and long-term storage.

This article explains how to configure the Microsoft Defender XDR streaming API to forward Advanced Hunting events to Azure Event Hubs for downstream processing, integration, and long-term storage. Security administrators can use this guide to set up streaming, understand the event schema, and estimate the required Event Hub capacity. Before you begin, review the prerequisites to ensure your Event Hubs environment and permissions are in place.

**Applies to:**

- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Prerequisites

Before you configure Microsoft Defender to stream data to Event Hubs, ensure the following prerequisites are fulfilled:

1. Create an Event Hubs \(for information, see [Set up Event Hubs](https://learn.microsoft.com/en-us/defender-xdr/configure-event-hub#set-up-event-hubs)\).
2. Creating an Event Hubs Namespace \(for information, see [Set up Event Hubs namespace](https://learn.microsoft.com/en-us/defender-xdr/configure-event-hub#set-up-event-hubs-namespace)\).
3. Add permissions to the entity who has the privileges of a **Contributor** so that this entity can export data to the Event Hubs. For more information on adding permissions, see [Add permissions](https://learn.microsoft.com/en-us/defender-xdr/configure-event-hub#add-permissions)

Note

The Streaming API can be integrated either via Event Hubs or Azure Storage Account.

## Enable raw data streaming

To enable raw data streaming to your Azure event hub, complete the following steps in the Microsoft Defender portal:

1. Sign in [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) as a ***Security Administrator*** or higher.
2. Go to the [Streaming API settings page](https://sip.security.microsoft.com/settings/mtp_settings/raw_data_export).
3. Select **Add**.
4. Choose a name for your new settings.
5. Choose **Forward events to Azure Event Hub**.
6. You can select if you want to export the event data to a single Event Hub, or to export each event table to a different Event Hubs in your Event Hubs namespace.
7. To export the event data to a single Event Hub, enter your **event hub name** and your **event hub Namespace resource ID**.

   To get your **event hub Namespace resource ID**, go to your Azure Event Hubs namespace page on the [Azure portal](https://ms.portal.azure.com/) > **Properties** tab > copy the text under **Resource ID**:

   [![An Event Hub resource ID](https://learn.microsoft.com/en-us/defender-xdr/media/streaming-api-event-hub/event-hub-resource-id.png)](https://learn.microsoft.com/en-us/defender-xdr/media/streaming-api-event-hub/event-hub-resource-id.png#lightbox)
8. Go to the [Supported Microsoft Defender XDR event types in event streaming API](https://learn.microsoft.com/en-us/defender-xdr/supported-event-types) to review the support status of event types in the Microsoft 365 Streaming API.
9. Choose the events you want to stream and select **Save**.

## Event schema in Azure Event Hub

The following JSON sample shows the structure of an event payload delivered to Azure Event Hubs by the streaming API:

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft Defender XDR received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft Defender XDR Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- Each Event Hubs message in Azure Event Hubs contains list of records.
- Each record contains the event name, the time Microsoft Defender received the event, the tenant it belongs \(you only get events from your tenant\), and the event in JSON format in a property called "**properties**".
- For more information about the schema of Microsoft Defender events, see [Advanced Hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).
- In Advanced Hunting, the **DeviceInfo** table has a column named **MachineGroup** which contains the group of the device. Here, every event is decorated with this column as well.

## Data type mappings

To get the data types for event properties:

1. Sign in [Microsoft Defender XDR](https://go.microsoft.com/fwlink/p/?linkid=2077139) and go to [Advanced Hunting page](https://security.microsoft.com/hunting-package).
2. Replace `{EventType}` with your event table name and run the following query to retrieve the column names and data types for that event:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Here's an example for Device Info event:

  [![An example query for device info](https://learn.microsoft.com/en-us/defender-endpoint/media/machine-info-datatype-example.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/machine-info-datatype-example.png#lightbox)

## Estimating initial Event Hub capacity

The following advanced hunting query can help provide a rough estimate of data volume throughput and initial event hub capacity based on events/sec and estimated MB/sec. We recommend running the query during regular business hours so as to capture 'real' throughput.

Use this query to estimate table volume over the past seven days. The output shows the average events per second and estimated MB/sec for each table, which you can use to determine the required event hub throughput units.

```kusto
let bytes_ = 1000;
union withsource=MDTables MyDefenderTable // TODO: Insert desired tables one by one separated by a comma (for example: DeviceEvents, DeviceInfo) or with a wildcard (Device*)
| where Timestamp > startofday(ago(7d))
| summarize count() by bin(Timestamp, 1m), MDTables
| extend EPS = count_ /60 
| summarize avg(EPS), estimatedMBPerSec = avg(EPS) * bytes_ / (1024*1024) by MDTables, bin(Timestamp, 3h)
| summarize avg_EPS=max(avg_EPS), estimatedMBPerSec = max(estimatedMBPerSec) by MDTables
| sort by toint(estimatedMBPerSec) desc
| project MDTables, avg_EPS, estimatedMBPerSec
```

To check the different Event Hub limits, review [Azure Event Hubs quota and limits](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-quotas).

## Monitoring created resources

You can monitor the resources created by the streaming API using **Azure Monitor**. To learn how to export log data for analyzing streaming API resources, see [Log Analytics workspace data export in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/logs-data-export).

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Overview of Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Microsoft Defender XDR streaming API](https://learn.microsoft.com/en-us/defender-xdr/streaming-api)
- [Supported Microsoft Defender event types in event streaming API](https://learn.microsoft.com/en-us/defender-xdr/supported-event-types)
- [Stream Microsoft Defender XDR events to your Azure storage account](https://learn.microsoft.com/en-us/defender-xdr/streaming-api-storage)
- [Azure Event Hubs documentation](https://learn.microsoft.com/en-us/azure/event-hubs/)
- [Troubleshoot connectivity issues - Azure Event Hubs](https://learn.microsoft.com/en-us/azure/event-hubs/troubleshooting-guide)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
