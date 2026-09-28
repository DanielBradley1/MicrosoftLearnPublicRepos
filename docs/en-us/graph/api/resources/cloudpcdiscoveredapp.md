<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdiscoveredapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-13 -->

# cloudPcDiscoveredApp resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a defined collection of discovered apps whose details can be used to create a cloud app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appDetail | [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta) | Specifies the details of the discovered app. Read-only. |
| appName | String | The name of the discovered app; for example, `Paint`. Read-only. |
| discoveredAppId | String | The unique identifier of the discovered app. Read-only. |
| sourceId | String | The ID of the source of the discovered app. For example, if the source is a custom device image, the **sourceId** value is the ID of that image. For example, `3035e17f-c0f7-49c1-9502-5990afcaf86f`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDiscoveredApp",
  "appDetail": {"@odata.type": "microsoft.graph.cloudPcCloudAppDetail"},
  "appName": "String",
  "discoveredAppId": "String",
  "sourceId": "String"
}
```
