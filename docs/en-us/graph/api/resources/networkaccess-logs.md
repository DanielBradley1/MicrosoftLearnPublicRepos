<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-logs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# logs resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents Global Secure Access traffic logs that provide insight into who is accessing what resources, where they're accessing them from, and what action took place.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connections | [microsoft.graph.networkaccess.connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) collection | An aggregated log entry that contains comprehensive information about network traffic events. |
| generativeAiInsights | [microsoft.graph.networkaccess.generativeAIInsight](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-generativeaiinsight?view=graph-rest-beta) collection | A collection of generative AI insights extracted from traffic events, including prompt and MCP activity metadata. |
| remoteNetworks | [microsoft.graph.networkaccess.remoteNetworkHealthEvent](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkhealthevent?view=graph-rest-beta) collection | A collection of remote network health events. |
| traffic | [microsoft.graph.networkaccess.networkAccessTraffic](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccesstraffic?view=graph-rest-beta) collection | A network access traffic log entry that contains comprehensive information about network traffic events. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.logs"
}
```
