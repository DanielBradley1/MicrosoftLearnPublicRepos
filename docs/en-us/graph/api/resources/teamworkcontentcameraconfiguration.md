<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkcontentcameraconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkContentCameraConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents configuration details for a content camera connected to a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isContentCameraInverted | Boolean | `True` if the content camera is inverted. |
| isContentCameraOptional | Boolean | `True` if the content camera is optional. |
| isContentEnhancementEnabled | Boolean | `True` if the content enhancement is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkContentCameraConfiguration",
  "isContentCameraInverted": "Boolean",
  "isContentCameraOptional": "Boolean",
  "isContentEnhancementEnabled": "Boolean"
}
```
