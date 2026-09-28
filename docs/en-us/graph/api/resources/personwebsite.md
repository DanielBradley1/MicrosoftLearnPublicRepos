<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# personWebsite resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about websites associated with a user in various services.

Inherits from [itemFacet](https://learn.microsoft.com/en-us/graph/api/resources/itemfacet?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/profile-list-websites?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) collection | Get the [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) resources from the **websites** navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/profile-post-websites?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) | Create a new [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/personwebsite-get?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) | Read the properties and relationships of a [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/personwebsite-update?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) | Update the properties of a [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/personwebsite-delete?view=graph-rest-beta) | None | Delete a [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | Contains categories a user has associated with the website \(for example, personal, recipes\). |
| description | String | Contains a description of the website. |
| displayName | String | Contains a friendly name for the website. |
| webUrl | String | Contains a link to the website itself. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.personWebsite",
  "id": "String (identifier)",
  "allowedAudiences": "String",
  "inference": {
    "@odata.type": "microsoft.graph.inferenceData"
  },
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "source": {
    "@odata.type": "microsoft.graph.personDataSource"
  },
  "categories": [
    "String"
  ],
  "description": "String",
  "displayName": "String",
  "webUrl": "String"
}
```
