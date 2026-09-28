<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkhardwaredetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkHardwareDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the hardware properties of a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| macAddresses | String collection | MAC address. |
| manufacturer | String | Device manufacturer. |
| model | String | Devie model. |
| serialNumber | String | Device serial number. |
| uniqueId | String | The unique identifier for the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkHardwareDetail",
  "macAddresses": [
    "String"
  ],
  "manufacturer": "String",
  "model": "String",
  "serialNumber": "String",
  "uniqueId": "String"
}
```
