<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-streaming-api -->
<!-- Sitemap-Last-Modified: 2026-10-05 -->

# Use the streaming API with Microsoft Defender for Business

If your organization has a Security Operations Center \(SOC\), you can use the [Microsoft Defender for Endpoint streaming API](https://learn.microsoft.com/en-us/defender-endpoint/api/raw-data-export) with [Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview) and [Microsoft 365 Business Premium](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-overview). The Microsoft Defender for Endpoint streaming API enables you to stream data, such as device file, registry, network, sign-in events, and more to one of the following services:

- [Microsoft Sentinel](#use-the-streaming-api-with-microsoft-sentinel): A scalable, cloud-native solution that provides security information and event management \(SIEM\) and security orchestration, automation, and response \(SOAR\) capabilities.
- [Azure Event Hubs](#use-the-streaming-api-with-event-hubs): A modern, big data streaming platform and event ingestion service that can seamlessly integrate with other Azure and Microsoft services. For example, Azure Stream Analytics, Power BI, and Azure Event Grid, along with outside services like Apache Spark.
- [Azure Storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction): Microsoft's cloud storage solution for modern data storage scenarios, with highly available, massively scalable, durable, and secure storage for a variety of data objects in the cloud.

By using the Defender for Endpoint streaming API, you can use [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) and [attack detection](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) with Defender for Business and Microsoft 365 Business Premium. The streaming API enables security operations centers to view more data about devices, understand better how an attack occurred, and take steps to improve device security.

## Use the streaming API with Microsoft Sentinel

To stream Defender for Business data to Microsoft Sentinel, complete the following steps.

Note

[Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/overview) is a paid service. Several plans and pricing options are available. See [Microsoft Sentinel pricing](https://www.microsoft.com/security/pricing/microsoft-sentinel/).

1. Ensure that you set up and configure Defender for Business, and that you onboard devices. See [Set up and configure Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-setup-configuration).
2. Create a Log Analytics workspace to use with Microsoft Sentinel. See [Create a Log Analytics workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/quick-create-workspace?tabs=azure-portal).
3. Onboard to Microsoft Sentinel. See [Quickstart: Onboard Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard).
4. Enable the Microsoft Defender connector. See [Connect data from Microsoft Defender to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender?tabs=MDE).

## Use the streaming API with Event Hubs

To use [Azure Event Hubs](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about), you need an Azure subscription. Before you begin, ensure you create an [event hub](https://learn.microsoft.com/en-us/azure/event-hubs/) in your organization. Then, sign in to the [Azure portal](https://ms.portal.azure.com/), go to **Subscriptions** > **Your subscription** > **Resource Providers** > **Register to Microsoft.insights**.

To configure streaming to Azure Event Hubs, complete the following steps.

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. Go to the [Data export settings page](https://security.microsoft.com/interoperability/dataexport).
3. Select **Add data export settings**.
4. Choose a name for your new settings.
5. Choose **Forward events to Azure Event Hubs**.
6. Enter your **Event Hubs name** and your **Event Hubs ID**.

   Note

   If you leave the Event Hubs name field empty, the system creates an event hub for each category in the selected namespace. If you don't use a [Dedicated Event Hubs Cluster](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-dedicated-overview), which is a single-tenant deployment with dedicated capacity, remember that there's a limit of 10 Event Hubs namespaces.

   To get your **Event Hubs ID**, go to your Event Hubs namespace page in the [Azure portal](https://ms.portal.azure.com/). On the **Properties** tab, copy the text under **ID**.
7. Choose the events you want to stream and then select **Save**.

### View the event schema in Azure Event Hubs

The following JSON sample shows the format of each event hub message that Event Hubs receives when event forwarding is enabled. Each message contains a `records` array with one or more event entries:

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the organization that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

Each event hub message in Azure Event Hubs contains a list of records. Each record contains the event name, the time Defender for Business received the event, the organization to which it belongs \(you get events from your organization only\), and the event in JSON format in a property called `properties`. For more information about the schema of Advanced Hunting events streamed to Azure Event Hubs, see [Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

## Use the streaming API with Azure Storage

To configure streaming to Azure Storage, complete the following steps.

Note

[Azure Storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction) requires an Azure subscription. Before you begin, ensure you create a [Storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview) in your organization. Then, sign in to your [Azure organization](https://ms.portal.azure.com/), and go to **Subscriptions** > **Your subscription** > **Resource Providers** > **Register to Microsoft.insights**.

### Enable raw data streaming

Raw data streaming forwards security event data from Defender for Business directly to your Azure Storage account, where you can retain and analyze it. To enable raw data streaming to Azure Storage, complete the following steps.

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. Go to [Data export settings page](https://security.microsoft.com/settings/mtp_settings/raw_data_export) in Microsoft Defender XDR.
3. Select **Add data export settings**.
4. Choose a name for your new settings.
5. Choose **Forward events to Azure Storage**.
6. Type your **Storage Account Resource ID**. To get your **Storage Account Resource ID**, go to your Storage account page in the [Azure portal](https://ms.portal.azure.com/). Then, on the **Properties** tab, copy the text under **Storage account resource ID**.
7. Choose the events you want to stream and then select **Save**.

### View the event schema in Azure Storage

A blob container is created for each event type. The following JSON sample shows the schema of a single event row written to Azure Storage. Each row includes the event timestamp, your tenant identifier, the Advanced Hunting category, and the event data in JSON format:

```json
{
  "time": "<The time WDATP received the event>"
  "tenantId": "<Your tenant ID>"
  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
  "properties": { <WDATP Advanced Hunting event as Json> }
}
```

Each blob contains multiple rows. Each row contains the event name, the time Defender for Business received the event, the organization to which the event belongs \(you get events from your organization only\), and the event in JSON format properties. For more information about the advanced hunting event data streamed to Azure Storage, see [Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

## Related content

- [Raw Data Streaming API](https://learn.microsoft.com/en-us/defender-endpoint/api/raw-data-export) in Defender for Endpoint
- [Overview of management and APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/management-apis)
