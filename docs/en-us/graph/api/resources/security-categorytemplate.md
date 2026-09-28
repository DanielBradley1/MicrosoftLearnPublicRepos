<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# categoryTemplate resource type

Namespace: microsoft.graph.security

Specifies a group of similar types of content in a particular department. This resource supports CRUD operations to apply and manage the [filePlanAppliedCategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanappliedcategory?view=graph-rest-1.0) descriptor, and any [filePlanSubcategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplansubcategory?view=graph-rest-1.0) descriptor for a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). These file plan descriptors supplement a retention label to improve the manageability and organization of Microsoft 365 content.

Inherits from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List categories](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-categories?view=graph-rest-1.0) | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) objects and their properties. |
| [Create categories](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-categories?view=graph-rest-1.0) | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) | Create a new [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) object. |
| [Get categories](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-get?view=graph-rest-1.0) | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) object. |
| [Delete categories](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-delete-categories?view=graph-rest-1.0) | None | Delete a [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) object. |
| [List subcategories](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-list-subcategories?view=graph-rest-1.0) | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) collection | Get the subcategoryTemplate resources from the subcategories navigation property. |
| [Create subcategories](https://learn.microsoft.com/en-us/graph/api/security-categorytemplate-post-subcategories?view=graph-rest-1.0) | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) | Create a new subcategoryTemplate object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the category descriptor. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the category descriptor is created. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| displayName | String | Unique string that defines a category name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). |
| id | String | Unique ID of the category. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subcategories | [microsoft.graph.security.subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) collection | Represents all subcategories under a particular category. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.categoryTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
