<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwarehealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkHardwareHealth resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the hardware health of a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| computeHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The system health details for a [teamworkDevice](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta). |
| hdmiIngestHealth | [teamworkPeripheralHealth](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta) | The health details about the HDMI ingest of a device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkHardwareHealth",
  "computeHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  },
  "hdmiIngestHealth": {
    "@odata.type": "microsoft.graph.teamworkPeripheralHealth"
  }
}
```
