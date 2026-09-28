<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkcameraconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# teamworkCameraConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the camera configuration for a Microsoft Teams Rooms [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentCameraConfiguration | [teamworkContentCameraConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcontentcameraconfiguration?view=graph-rest-beta) | The configuration for the content camera. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| cameras | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) collection | The list of connected cameras. |
| defaultContentCamera | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | The configured content camera that is used to share analog whiteboard content in a meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkCameraConfiguration",
  "contentCameraConfiguration": {
    "@odata.type": "microsoft.graph.teamworkContentCameraConfiguration"
  }
}
```
