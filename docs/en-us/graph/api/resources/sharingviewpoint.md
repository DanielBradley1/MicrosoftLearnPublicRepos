<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharingviewpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# sharingViewpoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents sharing operations the current user can take on the specified item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultSharingLink | [defaultSharingLink](https://learn.microsoft.com/en-us/graph/api/resources/defaultsharinglink?view=graph-rest-beta) | The default sharing link the user can create for this item. |
| sharingAbilities | [sharePointSharingAbilities](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsharingabilities?view=graph-rest-beta) | Provides information about which sharing links are available to the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharingViewpoint",
  "sharingAbilities": {
    "@odata.type": "microsoft.graph.sharePointSharingAbilities"
  },
  "defaultSharingLink": {
    "@odata.type": "microsoft.graph.defaultSharingLink"
  }
}
```
