<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveitemviewpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# driveItemViewpoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Returns information specific to the calling user for this drive item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessOperations | [driveItemAccessOperationsViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/driveitemaccessoperationsviewpoint?view=graph-rest-beta) | Indicates whether the user can perform the described actions on this item. |
| sharing | [sharingViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/sharingviewpoint?view=graph-rest-beta) | Indicates sharing operations the current user can take on the specified item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveItemViewpoint",
  "accessOperations": {
    "@odata.type": "microsoft.graph.driveItemAccessOperationsViewpoint"
  },
  "sharing": {
    "@odata.type": "microsoft.graph.sharingViewpoint"
  }
}
```
