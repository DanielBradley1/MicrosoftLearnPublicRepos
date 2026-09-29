<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/streaming-api -->
<!-- Sitemap-Last-Modified: 2024-04-25 -->

# Streaming API

**Applies to:**

- [Microsoft Defender XDR](https://go.microsoft.com/fwlink/p/?linkid=2118804)

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-1.0&preserve-view=true). If you're using Microsoft Defender for Business, see [Use the streaming API \(preview\) with Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-streaming-api).

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Stream Advanced Hunting events to Event Hubs and/or Azure storage account

Microsoft Defender XDR supports streaming events through [Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to an [Event Hubs](https://learn.microsoft.com/en-us/azure/event-hubs/) and/or [Azure storage account](https://learn.microsoft.com/en-us/azure/event-hubs/).

For more information on Microsoft Defender XDR streaming API, see the [video](https://learn-video.azurefd.net/vod/player?id=56edfb3f-b612-4e4c-acb9-4bbd141bd535).

## In this section

| Topic | Description |
| :--- | :--- |
| [Stream events to Azure Event Hubs](https://learn.microsoft.com/en-us/defender-xdr/streaming-api-event-hub) | Learn about enabling the streaming API in your tenant and configure Microsoft Defender to stream [Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to Event Hubs. |
| [Stream events to your Azure storage account](https://learn.microsoft.com/en-us/defender-xdr/streaming-api-storage) | Learn about enabling the streaming API in your tenant and configure Microsoft Defender to stream [Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to your Azure storage account. |
| [Supported event types](https://learn.microsoft.com/en-us/defender-xdr/supported-event-types) | Learn which Advanced Hunting event types the Streaming API supports. |

Watch this short video to learn how to set up the streaming API to ship event information directly to Azure Event hubs for consumption by visualization services, data processing engines, or Azure storage for long-term data retention.

<iframe src="https://learn-video.azurefd.net/vod/player?id=56edfb3f-b612-4e4c-acb9-4bbd141bd535" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Related topics

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Overview of Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Azure Event Hubs documentation](https://learn.microsoft.com/en-us/azure/event-hubs/)
- [Azure Storage Account documentation](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
