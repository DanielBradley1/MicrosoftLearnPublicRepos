<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# discoveredCloudAppDevice resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a device associated with a discovered cloud app.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-endpointdiscoveredcloudappdetail-list-devices?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppDevice](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta) collection | Get a list of [devices](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappdevice?view=graph-rest-beta) that access a discovered cloud app. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the cloud app. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.discoveredCloudAppDevice",
  "name": "String"
}
```
