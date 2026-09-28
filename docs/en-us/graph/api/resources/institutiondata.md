<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/institutiondata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# institutionData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents more information about an undergraduate, graduate, postgraduate degree, or other educational activity for a user and is used within an [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Short description of the institution the user studied at. |
| displayName | String | Name of the institution the user studied at. |
| location | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-beta) | Address or location of the institute. |
| webUrl | String | Link to the institution or department homepage. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "location": {"@odata.type": "microsoft.graph.physicalAddress"},
  "webUrl": "String"
}
```
