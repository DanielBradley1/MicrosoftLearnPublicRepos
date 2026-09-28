<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontentdevicematch?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# applicableContentDeviceMatch resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of devices and recommendations for the applicable catalog content.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceId | String | Collection of vendors who recommend the content. |
| recommendedBy | String collection | Collection of vendors who recommend the content. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.applicableContentDeviceMatch",
  "deviceId": "String",
  "recommendedBy": ["String"]
}
```
