<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveitemaccessoperationsviewpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# driveItemAccessOperationsViewpoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates whether the user can carry out the described actions on this item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| canComment | Boolean | Indicates whether the user can comment on this item. |
| canCreateFile | Boolean | Indicates whether the user can create files within this object. Returned only on folders. |
| canCreateFolder | Boolean | Indicates whether the user can create folders within this object. Returned only on folders. |
| canDelete | Boolean | Indicates whether the user can delete this item. |
| canDownload | Boolean | Indicates whether the user can download this item. |
| canRead | Boolean | Indicates whether the user can read this item. |
| canUpdate | Boolean | Indicates whether the user can update this item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveItemAccessOperationsViewpoint",
  "canComment": "Boolean",
  "canCreateFile": "Boolean",
  "canCreateFolder": "Boolean",
  "canDelete": "Boolean",
  "canDownload": "Boolean",
  "canRead": "Boolean",
  "canUpdate": "Boolean"
}
```
