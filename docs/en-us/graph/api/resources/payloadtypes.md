<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/payloadtypes?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# payloadTypes resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This resource represents data content of a raw or visual user notification that will be delivered to and consumed by the app client receiving this notification.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rawContent | String | The notification content of a raw user notification that will be delivered to and consumed by the app client on all supported platforms \(Windows, iOS, Android or WebPush\) receiving this notification. At least one of Payload.RawContent or Payload.VisualContent needs to be valid for a POST Notification request. |
| visualContent | [visualProperties](https://learn.microsoft.com/en-us/graph/api/resources/visualproperties?view=graph-rest-beta) | The visual content of a visual user notification, which will be consumed by the notification platform on each supported platform \(Windows, iOS and Android only\) and rendered for the user. At least one of Payload.RawContent or Payload.VisualContent needs to be valid for a POST Notification request. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "rawContent": "String",
  "visualContent": {"@odata.type": "microsoft.graph.visualProperties"}
}
```
