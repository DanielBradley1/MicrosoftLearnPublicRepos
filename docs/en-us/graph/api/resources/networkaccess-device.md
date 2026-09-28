<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-device?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# device resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Unique Microsoft Entra ID device identified by Global Secure Access.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceId | String | A unique device ID. |
| displayName | String | The display name for the device. |
| isCompliant | Boolean | A value that indicates whether or not the device is compliant. |
| lastAccessDateTime | DateTimeOffset | The most recent access time for the device. |
| operatingSystem | String | The operating system on the device. |
| trafficType | microsoft.graph.networkaccess.trafficType | The traffic classification. The possible values are: `internet`, `private`, `microsoft365`, or `all`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.device",
  "displayName": "String",
  "deviceId": "String",
  "operatingSystem": "String",
  "isCompliant": "Boolean",
  "trafficType": "String",
  "lastAccessDateTime": "String (timestamp)"
}
```
