<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisionresponse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-24 -->

# provisionResponse resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the response returned by the [provision](https://learn.microsoft.com/en-us/graph/api/device-provision?view=graph-rest-beta) action of the [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) resource.

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
