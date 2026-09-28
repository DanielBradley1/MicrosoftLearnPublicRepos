<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwareconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# teamworkHardwareConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the hardware configuration for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| processorModel | String | The CPU model on the device. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| compute | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | The system details for a [teamworkDevice](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta). |
| hdmiIngest | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | The product details about the HDMI ingest of a device. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkHardwareConfiguration",
  "processorModel": "String"
}
```
