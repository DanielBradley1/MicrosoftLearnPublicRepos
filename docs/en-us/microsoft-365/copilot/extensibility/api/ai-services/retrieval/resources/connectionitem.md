<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/connectionitem -->
<!-- Sitemap-Last-Modified: 2025-10-24 -->

# connectionItem resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a Copilot connector to include in retrieval operations in the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `connectionId` | String | The ID of a Copilot connector connection to include. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.connectionItem",
  "connectionId": "string"
}
```
