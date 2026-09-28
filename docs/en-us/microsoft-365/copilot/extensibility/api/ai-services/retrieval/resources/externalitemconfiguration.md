<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/externalitemconfiguration -->
<!-- Sitemap-Last-Modified: 2025-10-24 -->

# externalItemConfiguration resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents configuration options for retrieving data from Copilot connectors in the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `connections` | [connectionItem](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/connectionitem) collection | An array of connection objects specifying the Copilot connector connection identifiers to include in retrieval. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.externalItemConfiguration",
  "connections": [
    {
      "@odata.type": "microsoft.graph.connectionItem"
    }
  ]
}
```
