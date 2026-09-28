<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# discoveredCloudAppIPAddress resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the IP address associated with a discovered cloud app.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-list-ipaddresses?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppIPAddress](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) collection | Get the list of [IP addresses](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappipaddress?view=graph-rest-beta) associated with a discovered cloud app. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ipAddress | String | The IP address associated with a discovered cloud app. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.discoveredCloudAppIPAddress",
  "ipAddress": "String"
}
```
