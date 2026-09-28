<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/resources/copilotconversationlocation -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# copilotConversationLocation resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents user location information during a Copilot conversation through the [Microsoft 365 Copilot Chat API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/chat/copilotroot-post-conversations).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `countryOrRegion` | String | The country or region of the location. |
| `countryOrRegionConfidence` | Float | The confidence level of the country or region location. |
| `latitude` | Float | Latitude of user location. |
| `longitude` | Float | Longitude of user location. |
| `timeZone` | String | Time zone of user location in [IANA format](https://aka.ms/Copilot-APIs/Chat/IANA_Format). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotConversationLocation",
  "latitude": "Float",
  "longitude": "Float",
  "timeZone": "String",
  "countryOrRegion": "String",
  "countryOrRegionConfidence": "Float"
}
```
