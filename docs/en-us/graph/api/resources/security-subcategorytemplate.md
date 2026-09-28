<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# subcategoryTemplate resource type

Namespace: microsoft.graph.security

Supports CRUD operations to apply and manage the [filePlanSubcategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplansubcategory?view=graph-rest-1.0) descriptor for a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). The **subcategory** file plan descriptor supplements a retention label to improve the manageability and organization of Microsoft 365 content.

Inherits from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-list-subcategories?view=graph-rest-1.0) | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-post-subcategories?view=graph-rest-1.0) | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) | Create a new [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-subcategorytemplate-get?view=graph-rest-1.0) | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-delete-subcategories?view=graph-rest-1.0) | None | Delete a [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the subcategory descriptor. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the subcategory descriptor is created. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| displayName | String | Unique string that defines a subcategory name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). |
| id | String | Unique ID of the subcategory. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

Here's JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.subcategoryTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
