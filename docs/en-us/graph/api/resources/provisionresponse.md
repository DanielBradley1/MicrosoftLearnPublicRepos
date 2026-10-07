<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisionresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# provisionResponse resource type

Namespace: microsoft.graph

Represents the response returned by the [provision](https://learn.microsoft.com/en-us/graph/api/device-provision?view=graph-rest-1.0) action of the [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) resource.

An approved Virtual Desktop Infrastructure \(VDI\) provisioning service receives this response after it provisions a device and passes it to the device so that the device can complete its registration with the directory.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| challenge | String | The cryptographic challenge that the device uses to complete its registration with the directory. |
| deviceId | String | The unique identifier of the provisioned device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.provisionResponse",
  "challenge": "String",
  "deviceId": "String"
}
```
